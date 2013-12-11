
# This Makefile is for use by the emapa Release Manager.
#
# requirements: Oort (http://code.google.com/p/owltools/wiki/OortIntro)
#
# To make a release, type 'make release' in this directory

OBO = http://purl.obolibrary.org/obo

initial-build: emapa.obo
build: emapa.obo minidiff
release: emapa.obo diff

# all release files are derived from the editors version.
# we use the default Oort setup (hermit as reasoner)
emapa.obo: emapa-edit.owl
	ontology-release-runner $< --allow-overwrite --asserted --simple

# ----------------------------------------
# Imports
# ----------------------------------------
all_imports: imports/go_import.owl imports/pato_import.owl

imports/%_import.owl: emapa-edit.owl
	owltools $< $(OBO)/$*.owl --add-imports-from-supports --extract-module -s $(OBO)/$*.owl -c --extract-mingraph  --set-ontology-id $(OBO)/go/extensions/$@ -o $@

# ----------------------------------------
# Diffs
# ----------------------------------------

# 
diff: emapa.obo
	cd diffs && touch emapa-diff && rm emapa-*diff* && make

# Minidiff: intra-release differences
minidiff: emapa.obo
	cd diffs  && touch emapa-diff && rm emapa-*diff* && make TGTS='html txt' SRC=../emapa.obo && mail -s emapa-diffs RELEASE-MANAGER@FOO.BAR < emapa-combined-diff.txt

