# ----------------------------------------
# Makefile for emapa
# Generated using ontology-starter-kit
# ----------------------------------------
# <do not edit above this line>

# ----------------------------------------
# Standard Constants
# ----------------------------------------
# these can be overwritten on the command line

OBO=http://purl.obolibrary.org/obo
ONT=emapa
BASE=$(OBO)/$(ONT)
SRC=$(ONT)-edit.obo
RELEASEDIR=../..
ROBOT= robot
OWLTOOLS= owltools
USECAT= --use-catalog
SPARQLDIR = ../sparql

# ----------------------------------------
# Top-level targets
# ----------------------------------------

all: sparql_test all_imports $(ONT).owl $(ONT).obo
test: sparql_test all
prepare_release: all
	cp $(ONT).owl $(ONT).obo $(RELEASEDIR) &&\
	mkdir -p $(RELEASEDIR)/imports &&\
	cp imports/*.owl $(RELEASEDIR)/imports &&\
	cp imports/*.obo $(RELEASEDIR)/imports &&\
	(test -f subsets/*owl && cp subsets/* $(RELEASEDIR)/subsets && git add $(RELEASEDIR)/subsets/* || echo "no subsets") &&\
	echo "Release files are now in $(RELEASEDIR) - now you should commit, push and make a release on github"

# ----------------------------------------
# Main release targets
# ----------------------------------------

# by default we use Elk to perform a reason-relax-reduce chain
# after that we annotate the ontology with the release versionInfo
$(ONT).owl: $(SRC)
	$(ROBOT)  reason -i $< -r ELK relax reduce -r ELK annotate -V $(BASE)/releases/`date +%Y-%m-%d`/$(ONT).owl -o $@
$(ONT).obo: $(ONT).owl
	$(ROBOT) convert -i $< -f obo -o $(ONT).obo.tmp && grep -v ^owl-axioms $(ONT).obo.tmp > $@

# ----------------------------------------
# Import modules
# ----------------------------------------
# Most ontologies are modularly constructed using portions of other ontologies
# These live in the imports/ folder
# These can be regenerated with make all_imports

IMPORTS = ro
IMPORTS_OWL = $(patsubst %, imports/%_import.owl,$(IMPORTS)) $(patsubst %, imports/%_import.obo,$(IMPORTS)) $(patsubst %, imports/%_terms.txt,$(IMPORTS))

# generate seed with all referenced entities
seed.txt: $(SRC)
	$(ROBOT) query -f csv -i $< --query ../sparql/terms.sparql $@

# Generate terms.txt for each import.  # Assume OBO-style Possibly hacky step?
# Should be able to drop this if robot can just take a big messy list of terms as input.

imports/%_terms_combined.txt: seed.txt
	cat $< imports/$*_terms.txt >  $@

# Make this target to regenerate ALL
all_imports: $(IMPORTS_OWL)

# Use ROBOT, driven entirely by terms lists NOT from source ontology
imports/%_import.owl: mirror/%.owl imports/%_terms_combined.txt
	$(ROBOT) extract -i $< -T imports/$*_terms.txt --method BOT -O $(BASE)/$@ -o $@
.PRECIOUS: imports/%_import.owl

# Add '--check false' flag if your OWL is not obo-strict
imports/%_import.obo: imports/%_import.owl
	$(ROBOT) convert -i $< -o $@

# clone remote ontology locally, perfoming some excision of relations and annotations
mirror/%.owl: $(SRC)
	$(ROBOT) convert -I $(OBO)/$*.owl -o $@
.PRECIOUS: mirror/%.owl

# ----------------------------------------
# Release
# ----------------------------------------
# copy from staging area (this directory) to top-level
release: $(ONT).owl $(ONT).obo
	cp $^ $(RELEASEDIR) && cp imports/* $(RELEASEDIR)/imports

# ----------------------------------------
# Sparql queries: Q/C
# ----------------------------------------

# these live in the ../sparql directory, and have suffix -violation.sparql
# adding the name here will make the violation check live
VCHECKS = equivalent-classes  owldef-self-reference xref-syntax nolabels

# run all violation checks
VQUERIES = $(foreach V,$(VCHECKS),$(SPARQLDIR)/$V-violation.sparql)
sparql_test: $(SRC)
	robot verify -i $< --queries $(VQUERIES) -O reports/

# ----------------------------------------
# Sparql queries: Reports
# ----------------------------------------

REPORTS = basic-report class-count-by-prefix edges xrefs obsoletes synonyms
REPORT_ARGS = $(foreach V,$(REPORTS),-s $(SPARQLDIR)/$V.sparql reports/$V.tsv)
all_reports: $(SRC)
	robot query -f tsv -i $< $(REPORT_ARGS)

# ----------------------------------------
# Docker (experimental)
# ----------------------------------------
IM=build-$(ONT)
build-docker:
	docker build -t $(ONT) .
