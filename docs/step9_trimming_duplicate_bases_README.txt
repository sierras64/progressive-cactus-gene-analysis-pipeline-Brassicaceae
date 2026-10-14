================================================================================
SCRIPT: step9_trimming_duplicate_bases.py
================================================================================
Description: Trims each stitched alignment to the reference CDS using the BED exon coordinates. It detects the BED convention once per run (0-based half-open or 1-based inclusive) and, per file, whether step 1 extracted one extra base per exon; that base is removed at the same columns in every species. Columns where the reference row has a gap are also removed. A file is written only if the trimmed reference row equals its FNA sequence (N and IUPAC ambiguity codes match any base they stand for). Every file, written or refused, is listed with its status and reason in <output_dir>/step9_trimming_report.tsv. Files refused as EXTRACTION_SHIFTED cannot be repaired here; rerun step 1 for them with corrected coordinates.
**Before running step9, run clean_nucleotide_fasta_headers.py on the reference nucleotide fasta file first**

Usage:
  python3 step9_trimming_duplicate_bases.py <step8_stitched_dir> <output_dir> <reference_nucleotide_fna_file> <bed_file> <threads>

Inputs:
  - <step8_stitched_dir>: Stitched alignments from step 8.
  - <output_dir>: Destination for the trimmed .aln files.
  - <reference_nucleotide_fna_file>: Plain-text FASTA of true reference nucleotide sequences, with the transcript ID as the first word of each header (gzipped FASTA is not supported).
  - <bed_file>: Reference BED file containing exon coordinates and Transcript IDs.
  - <threads>: Number of threads to use.
