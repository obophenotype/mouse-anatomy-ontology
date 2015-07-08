## Welcome to emapa

This document describes the EMAPA Mouse Ontology, as hosted on the OBO Phenotype Github
Repository.


The Ontology ( https://github.com/obophenotype/mouse-anatomy-ontology )
------------

In essence an OBO file is use to describe the Ontology; this file can be "Pulled" from 
this Github Repository, edited, and "Pushed" back to here.

Editing of the Ontology is carried out using OBO-Edit ( http://www.oboedit.org ) 

The file: mouse-anatomy-ontology/src/ontology/emapa-edit.obo

NOTA BENE: When the ontology is imported into OBO-Edit, another file MUST be imported at 
the same time, using the "Advanced Options", or ERRORS will occur!

MANDATORY ADDITIONAL file: mouse-anatomy-ontology/src/ontology/CLTEMP.obo

( The ontology now references a cut-down version of the Cell Type ontology, which is NOT
maintained here, merely imported from here:  
https://github.com/obophenotype/cell-ontology )


Significant Files 
-----------------

1. in https://github.com/obophenotype/mouse-anatomy-ontology/tree/master/src/ontology

BASE.obo - Maintained by the IT Support Group
( On Creation of a new Release, this MUST be replaced with the contents of the released
emapa-edit.obo file )

CLTEMP.obo - Maintained by the IT Support Group
( Contains a subset of the Cell Types that the Mouse Atlas projects are interested in)

README-editors.md - Ignore; DO NOT EDIT!

emapa-edit_NO-CL.obo - Maintained by the IT Support Group
( A version of emapa-edit.obo WITHOUT any Cell Type Terms or Relationships in; as 
required by the Jackson Lab )

CHANGES	- Ignore; DO NOT EDIT!

Makefile - Ignore; DO NOT EDIT!

emapa-edit.obo - The MOUSE Ontology, all changes must be made to this file by the Editors

emapa-idranges.owl - Ignore; DO NOT EDIT!


2. in https://github.com/obophenotype/mouse-anatomy-ontology

README.txt - This Document!

A. People
   ------
   
Current Ontology Editors
------------------------

1. Dr Terry Hayamizu, MD - Terry.Hayamizu at jax.org 

The Jackson Laboratory
600 Main Street, Bar Harbor
Maine 04609, USA

( http://www.jax.org/index.html )

Mouse Genome Informatics 
( http://www.informatics.jax.org )
( http://research.jax.org/faculty/martin-ringwald.html )


2. Dr Jane Armstrong - jane.armstrong at ed.ac.uk 

GUDMAP Editorial Office ( http://www.gudmap.org/index.html )

Centre for Integrative Physiology
School of Biomedical Sciences
College of Medicine and Veterinary Medicine
University of Edinburgh, Hugh Robson Building
George Square, Edinburgh
EH8 9XD, UK

( http://www.gudmap.org/Contact/Consortium.html )


IT Support
----------

For Processes that use the Mouse OBO file within Edinburgh Mouse Atlas Projects.

1. Prof Richard Baldock - richard.baldock at igmm.ed.ac.uk
( http://www.hgu.mrc.ac.uk/people/r.baldock.html )

( http://www.hgu.mrc.ac.uk/research_at_the_unit_section/biomedical_systems_analysis.html )
( http://www.e-mouseatlas.org/emap/home.html ) 

MRC Human Genetics Unit MRC IGMM, 
University of Edinburgh Western General Hospital, 
Crewe Road, Edinburgh EH4 2XU, UK

( http://www.gudmap.org/Contact/Consortium.html )


Whenever the OBO file is "pushed" to GitHub, a Continuous Integration Server (hosted by 
the HGU) initiates some processing that validates the Ontology.

Nightly the HGU runs processing to build a relational database from the OBO file - this 
representation is then available for use within the Mouseatlas Projects hosted by the 
HGU.


OBO Phenotype Custodian ( https://github.com/obophenotype ) 
-----------------------

The instigator of using GitHub to manage OBO data.

1. Dr Chris Mungall - cjmungall at lbl.gov

( http://berkeleybop.org/person/chris-mungall )

Berkeley Bioinformatics Open-Source Projects
Lawrence Berkeley National Laboratory
1 Cyclotron Road, Mailstop 100PGF100
Berkeley, CA 94720, USA


