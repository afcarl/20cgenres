train20
=======

Code and data used to train models of 20c literary genres, 2016. The governing strategy here is to slice strategically, creating progressively smaller sets and progressively better models.

To achieve this start with volume-level discriminations, and then work downward to the page level, training page-level models _only within_ literary genres.

But also, even within the volume-level process, we work through successive eliminations — first constituting a rough list of possible fiction candidates by modeling fiction-against-everything, and then paring away things that a more precise model suggests are actually biography, drama, or poetry.

bzipmeta.csv
------------
Created June 2016. Contains metadata for all the files with extracted features in TARDIS/work/hathifiles. These should also have volume-level summaries in TARDIS/work/train20.


inferfromreaders.py
-------------------
1) First stage of constructing a training set. This looks at 362 volumes tagged by undergrads at a page level and sorts them into volume-level groups. Produces *confidentvolumes.csv* as well as **genredividedvols.csv.** The latter are not used in volume-level classification.

manualtagging.py
----------------
2) Amplifies the page-level training set with several hundred volume-level genre tags assigned by Underwood. Places these in **taggedvolumes.csv.**

createtrainingset.py
--------------------
3) Fuses the output of the previous two stages in order to produce **maintrainingset.csv.** This becomes the metadata used in ...

trainamodel.py
--------------
4) Functions centrally needed for creating models of one genre against another genre, or of one genre against all other genres.
