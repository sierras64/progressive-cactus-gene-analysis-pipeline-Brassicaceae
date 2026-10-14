================================================================================
SCRIPT: step4_reverse_complement_add_missingbp.sh
================================================================================
Description: Converts filtered MAF files into aligned FASTA (.aln) format. It concatenates each file's MAF blocks per species, pads species absent from a block with dashes, and reverse-complements based on the reference strand in the BED file. Bases a species skips between consecutive MAF blocks are unaligned sequence and are deliberately not added back: filling them would force gap columns into the reference and shift the frame of the other species relative to it. Also writes extraction_summary.tsv to the output directory.

Usage:
  ./step4_reverse_complement_add_missingbp.sh -m <step3_filtered_dir> -o <output_dir> -b <bed_file> [-t <threads>]

Inputs:
  - -m: Directory of filtered MAF files.
  - -o: Output directory for .aln files.
  - -b: BED file of target regions (used for strand lookup).
  - -t: Number of parallel threads (default: 4).
