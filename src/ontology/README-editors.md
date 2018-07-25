These notes are for the EDITORS of emapa

This project was created using the [ontology starter kit](https://github.com/cmungall/ontology-starter-kit). See the site for details.

For more details on ontology management, please see the [OBO tutorial](https://github.com/jamesaoverton/obo-tutorial) or the [Gene Ontology Editors Tutorial](go-protege-tutorial.readthedocs.io)

You may also want to read the [GO ontology editors guide](http://go-ontology.readthedocs.org/)

## Requirements

 1. Protege (for editing)
 2. A git client (we assume command line git)
 3. [docker](https://www.docker.com/get-docker) (for managing releases)

## Editors Version

Make sure you have an ID range in the [idranges file](emapa-idranges.owl)

If you do not have one, get one from the head curator.

The editors version is [emapa-edit.owl](emapa-edit.owl)

** DO NOT EDIT emapa.obo OR emapa.owl in the top level directory **

[../../emapa.owl](../../emapa.owl) is the release version

To edit, open the file in Protege. First make sure you have the repository cloned, see [the GitHub project](https://github.com/obophenotype/mouse-anatomy-ontology) for details.

## ID Ranges

These are stored in the file

 * [emapa-idranges.owl](emapa-idranges.owl)

** ONLY USE IDs WITHIN YOUR RANGE!! **

If you have only just set up this repository, modify the idranges file
and add yourself or other editors. Note Protege does not read the file
- it is up to you to ensure correct Protege configuration.


### Setting ID ranges in Protege

We aim to put this up on the technical docs for OBO on http://obofoundry.org/

For now, consult the [GO Tutorial on configuring Protege](http://go-protege-tutorial.readthedocs.io/en/latest/Entities.html#new-entities)

## Imports

All import modules are in the [imports/](imports/) folder.

There are two ways to include new classes in an import module

 1. Reference an external ontology class in the edit ontology. In Protege: "add new entity", then paste in the PURL
 2. Add to the imports/foo_terms.txt file

After doing this, you can run

`./run.sh make all_imports`

to regenerate imports.

Note: the foo_terms.txt file may include 'starter' classes seeded from the ontology starter kit. It is safe to remove these.

## Release Manager notes

You should only attempt to make a release AFTER the edit version is
committed and pushed, and the travis build passes.

These instructions assume you have
[docker](https://www.docker.com/get-docker). This folder has a script
[run.sh](run.sh) that wraps docker commands.

to release:

    cd src/ontology
    ./run.sh make

If this looks goo
d type:

    ./run.sh make prepare_release

This generates derived files such as emapa.owl and emapa.obo and places
them in the top level (../..). The versionIRI will be added.

Commit and push these files.

    git commit -a

And type a brief description of the release in the editor window

Finally type

    git push origin master

IMMEDIATELY AFTERWARDS (do *not* make further modifications) go here:

 * https://github.com/obophenotype/mouse-anatomy-ontology/releases
 * https://github.com/obophenotype/mouse-anatomy-ontology/releases/new

The value of the "Tag version" field MUST be

    vYYYY-MM-DD

The initial lowercase "v" is REQUIRED. The YYYY-MM-DD *must* match
what is in the versionIRI of the derived emapa.owl (data-version in
emapa.obo).

Release title should be YYYY-MM-DD, optionally followed by a title (e.g. "january release")

Then click "publish release"

__IMPORTANT__: NO MORE THAN ONE RELEASE PER DAY.

The PURLs are already configured to pull from github. This means that
BOTH ontology purls and versioned ontology purls will resolve to the
correct ontologies. Try it!

 * http://purl.obolibrary.org/obo/emapa.owl <-- current ontology PURL
 * http://purl.obolibrary.org/obo/emapa/releases/YYYY-MM-DD.owl <-- change to the release you just made

For questions on this contact Chris Mungall or email obo-admin AT obofoundry.org

# Travis Continuous Integration System

Check the build status here: [![Build Status](https://travis-ci.org/obophenotype/mouse-anatomy-ontology.svg?branch=master)](https://travis-ci.org/obophenotype/mouse-anatomy-ontology)

Note: if you have only just created this project you will need to authorize travis for this repo.

 1. Go to [https://travis-ci.org/profile/obophenotype](https://travis-ci.org/profile/obophenotype)
 2. click the "Sync account" button
 3. Click the tick symbol next to mouse-anatomy-ontology

Travis builds should now be activated

