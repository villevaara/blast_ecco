# Documentation

https://www.utupub.fi/bitstream/handle/10024/146706/Vesanto_Aleksi_opinnayte.pdf?sequence=1&isAllowed=y

## Running BLAST

see README in code/work/

python blast_batches.py --output_folder="$WRKDIR/txt_reuse/blast_work_from_puhti/blast_work" --batch_folder="$WRKDIR/txt_reuse/results_qpi10" --threads=$1 --text_count=1302141 --qpi=10 --iter=$2 --e_value=0.000000001

### batches

python data_preparer.py --data_location="../../data/raw" --output_folder="../../output/blast_out" --threads=1 --language="ENG"
python blast_batches.py --batch_folder="/media/vvaara/uh-villevaara-500gb/blast_results/max_target_seqs_500" --output_folder="/media/vvaara/uh-villevaara-500gb/blast_data" --threads=3 --iter=0 --text_count=1302141 --qpi=1 --e_value=0.000000001 --max_target_seqs=500

### one go

python run_full.py --data_folder="../../data/raw" --output_folder="../../output/blast_simple" --language="ENG" --threads=1

### next runs

aleksi param:
go: ge:
{3, 11, (double) INT2_MAX, 0.201, 0.012, 0.061, 3.3, -58, 0.740802, 140.417000, 141.882000},

to test:
{3, 14, (double) INT2_MAX, 0.201, 0.012, 0.061, 3.3, -58, 0.740802, 140.417000, 141.882000},
{3, 15, (double) INT2_MAX, 0.201, 0.012, 0.061, 3.3, -58, 0.740802, 140.417000, 141.882000},

already run:
{3, 11, (double) INT2_MAX, 0.201, 0.012, 0.061, 3.3, -58, 0.740802, 140.417000, 141.882000},
{3, 12, (double) INT2_MAX, 0.201, 0.012, 0.061, 3.3, -58, 0.740802, 140.417000, 141.882000},
{3, 13, (double) INT2_MAX, 0.201, 0.012, 0.061, 3.3, -58, 0.740802, 140.417000, 141.882000},

python blast_batches.py --batch_folder="../../output/export_go3_ge13" --output_folder="../../output/blast_out_h5" --threads=1 --iter=0 --text_count=5 --qpi=5 --e_value=0.000000001

python blast_batches.py --batch_folder="../../output/export" --output_folder="../../output/blast_out_h5" --threads=1 --iter=0 --text_count=5 --qpi=5 --e_value=0.000000001
python blast_batches.py --batch_folder="../../output/export" --output_folder="../../output/blast_out" --threads=1 --iter=0 --text_count=5 --qpi=5 --e_value=0.000000001



