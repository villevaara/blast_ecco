# Max resutls?

Philip raised a possible issue of Blast results being limited to max N hits for each sequence. There seem to be a few options for limiting results in BLAST, some with default values (see blast_opt.txt).

 -max_target_seqs <Integer, >=1>
   Maximum number of aligned sequences to keep 
   (value of 5 or more is recommended)
   Default = '500'
    * Incompatible with:  num_descriptions, num_alignments

 -num_descriptions <Integer, >=0>
   Number of database sequences to show one-line descriptions for
   Not applicable for outfmt > 4
   Default = '500'
    * Incompatible with:  max_target_seqs

 -num_alignments <Integer, >=0>
   Number of database sequences to show alignments for
   Default = '250'
    * Incompatible with:  max_target_seqs


https://www.biostars.org/p/364083/ :

**max_target_seqs** for how many maximum target sequences and **max_hsps** for how many maximum hits within target sequences, but still in this case it's picking the latter hit although presumably it has encountered the other hit first. AFAIK there's no grep -m 1 equivalent to blast although perhaps it's possible to disable search within hsps by changing the source code. In other words, it may not return the optimal hit, but it seems to return the optimal hit within the first good enough target sequence. If subject sequences are long, this may have significant speed implications..

 -max_hsps <Integer, >=1>
   Set maximum number of HSPs per subject sequence to save for each query


# Other parameters

 -threshold <Real, >=0>
   Minimum word score such that the word is added to the BLAST lookup table

This is for considering matching seed words. It is currently set to 400, which is probably too high for any fuzzy matching, therefore accelerating the seed word matching considerably. ( https://www.utupub.fi/bitstream/handle/10024/146706/Vesanto_Aleksi_opinnayte.pdf?sequence=1&isAllowed=y p. 19 )
