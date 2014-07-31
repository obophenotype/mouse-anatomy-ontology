These notes are for the EDITORS of emapa

## Editors Version

The editors version is emapa-edit.obo

** DO NOT EDIT emapa.obo OR emapa.owl **

emapa.obo is the release version

## ID Ranges

TODO - these are not set up

These are stored in the file

  emapa-idranges.owl

** ONLY USE IDs WITHIN YOUR RANGE!! **

## Setting ID ranges in OBO-Edit

 In the Metadata menu, select the ID manager option. You can set the ID range of any 
 profile you create here by clicking on the settings icon (cog wheels) next to the profile 
 name. In the window that appears, you can set the ID range by editing the default rule: 
 "ID:$sequence(<number of digits>,<minimum of range>,<maximum of range>)$"
 Thus, "EMAPA:$sequence(8,2000000,2999999)$" will set a range of 8 digit IDs from 200000 
 to 2999999.  
 
## Git Quick Guide

TODO add instructions here

## Release Manager notes

to release:

    cd src/ontology
    make

If this looks good:

    git commit -a

And type a brief description of the release in the editor window

== Jenkins Continuous Integration System ==

TODO - editors do you want this set up?

Check:

http://build.berkeleybop.org/job/build-emapa/

after committing

== General Guidelines ==

See:
http://wiki.geneontology.org/index.php/Curator_Guide:_General_Conventions
