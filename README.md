# BLAST Ecco

Using BLAST for text reuse detection on ECCO, EEBO, etc...

**Copied and adapted from https://github.com/avjves/textreuse-blast**

## Running

### Simple version:

python run_full.py  --data_folder="../../data/raw/" --output_folder="../../output/blast_hume_vol5" --language="ENG"

### Batches:

python data_preparer.py  --data_location="../../data/raw/" --output_folder="../../output/blast_rushworth" --language="ENG" --threads=1
python blast_batches.py  --output_folder="../../output/blast_rushworth" --batch_folder="../../output/blast_rushworth/data_out" --threads=1 --text_count=9 --qpi=10 --iter=0 --e_value=0.000000001

## BLAST paremeters:

`blastp`

**Picked as metaparam in Aleksi's thesis:**
- window_size <Integer, >=0>
    Multiple hits window size, use 0 to specify 1-hit algorithm
    * Prob didn't have a huge effect?
    * Might help with reducing the combining of of hits?

**metaparameters in Python code:**
- threshold <Real, >=0>
    Minimum word score such that the word is added to the BLAST lookup table
    * This one is default 400 in the script. Lowering it will probably give very slightly more accurate results, but will use quite a bit more resources. Increases fuzziness of the hits.
- evalue <Real>
    Expectation value (E) threshold for saving hits 
    Default = '10'
    * Lower this to get better accuracy of hits.
- word_size <Integer, >=2>
    Word size for wordfinder algorithm
    * Default 6 in the script. Lowering this helps with tackling the OCR noise, but again uses quite a bit more resources. Increases fuzziness of the hits.
- gapopen <Integer>
    Cost to open a gap
    * Cost of starting a gap sequqnce in combining two close by sequences. Might not be useful to touch?
- gapextend <Integer>
    Cost to extend a gap
    * Cost of expanding a gap for combining to sequences in close proximity. Increasing this might make the results more fragmented, which might be good! Or might result in too short fragments.
- matrix <String>
    Scoring matrix name (normally BLOSUM62)
    * Don't touch this!
    * Using a better matching matrix might make the results better though. One that took ocr probabilities into account.

**others in code:**
[-outfmt format]
[-out output_file]
[-db database_name]
[-num_threads int_value]


**test next:**

- modifying gapopen and gapextend
- lowering evalue? --- by a lot. eg. -> 0.000000001
- lowering treshold?
- 

## CSC application text

Program Codes, Methods.

Python script wrapper around NCBI BLAST Basic Local Alignment Search Tool) bioinformatics software, utilizing multiple threads. Custom version of BLAST has been adopted to detecting natural language text-reuse data in historical literature corpus. Low intensity text reuse detection does not require cluster computing, but the nature of the sources (full text corpus of circe 300,000 text with relatively bad OCR quality) warrants use of a method that is able to detect text reuse in very noisy material, and is computationally demanding. For more detailed information on the method see: Vesanto (2019): Detecting and Analyzing Text Reuse with BLAST (https://www.utupub.fi/handle/10024/146706) and the code repository at: https://github.com/avjves/ .

## Test 2 -- all the english poets

from The Most Disreputable Trade. Two large collections of poetry at the end of 18th century. Compare volumes covering same poets, as well as the original works of those poets.

* The works of the English poets. With prefaces, biographical and critical, by Samuel Johnson.
  * Johnson, Samuel
  * Vol. 1. London : printed by John Nichols; for J. Buckland, J. Rivington and Sons, T. Payne and Sons, L. Davis, B. White and Son [and 37 others in London], 1790.. 326 pp.

* A complete edition of the poets of Great Britain.
  * Vol. 1. London : printed for John and Arthur Arch, and for Bell and Bradfute and I. Mundell and Co., in Edinburgh, [1792-5].. 741 pp.

## Real batch run

Data loc for preparation:
/media/vvaara/uh-villevaara-ext1/chunks_for_blast/

python data_preparer.py  --data_location="/media/vvaara/uh-villevaara-ext1/chunks_for_blast/" --output_folder="/media/vvaara/uh-villevaara-ext1/blast_work/" --language="ENG" --threads=1

output_folder: This is the location of the folder that data_preparer produced. In others words, that one above, so input for this. ^^
batch_folder: Final output location. 

python blast_batches.py  --output_folder="../../output/blast_rushworth" --batch_folder="../../output/blast_rushworth/data_out" --threads=1 --text_count=9 --qpi=10 --iter=0 --e_value=0.000000001




