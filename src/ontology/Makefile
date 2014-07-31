
# This Makefile is for use by the emapa Release Manager.
#
# requirements: Oort (http://code.google.com/p/owltools/wiki/OortIntro)
#
# To make a release, type 'make release' in this directory

OBO = http://purl.obolibrary.org/obo

initial-build: emapa.obo
build: emapa.obo 
release: emapa.obo

# all release files are derived from the editors version.
# we use the default Oort setup (hermit as reasoner)
emapa.obo: INPUT-fixed.obo
	ontology-release-runner $< --allow-overwrite --asserted --simple --skip-format owx

# this step can be removed when the editors version includes a line in the header:
#
# ontology: emapa
#
INPUT-fixed.obo: INPUT.obo
	owltools $< --set-ontology-id emapa -o -f obo $@


