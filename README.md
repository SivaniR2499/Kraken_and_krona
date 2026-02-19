
**Kraken2 + Krona on WashU HPC**
This repo is a small, opinionated collection of Bash scripts I use to run Kraken2 and visualize results with Krona on the WashU HPC. It’s meant to be readable, copy‑pasteable, and easy to adapt to your own project.

**Files in this repo**
01_run_kraken2.sh
This script walks through a full Kraken2 workflow for paired‑end data:

How to start an interactive Docker + conda session on the WashU LSF cluster

How to create and activate a conda environment and install Kraken2

How to run Kraken2 on a single sample (paired FASTQs)

How to loop over multiple samples in a directory and:

Classify reads with Kraken2

Use extract_kraken_reads.py (KrakenTools) to pull out human‑only reads (taxid 9606)

Compress the filtered reads and align them to hg38 using Bowtie2

You can use this script whenever you want to:

Screen CUT&RUN or other NGS libraries for contamination

Keep only human reads before downstream alignment/peak calling

Scale from a single test sample to an entire batch of samples in a consistent way

It’s written to be read and modified: most of the “commands” are documented with comments, and you’re expected to edit the paths and sample names for your own data.

**02_krona_from_kraken.sh**
This script shows how to turn Kraken2 outputs into interactive Krona HTML plots:

Points to where your *.kraken2_report.txt files live

Demonstrates a single‑sample example: one Kraken2 report → one Krona HTML

Shows a batch mode: loop over all reports and generate one Krona plot per sample

Uses ktImportTaxonomy (and optionally kreport2krona.py from KrakenTools) to build the inputs Krona expects

You can use this script when you want to:

Quickly inspect the taxonomic composition of your samples in a browser

Compare contamination profiles across multiple libraries

Drop Krona plots into reports, talks, or QC summaries

Again, the goal is clarity rather than cleverness: change the directories, run it in your own conda env with Krona installed, and you should get a set of .krona.html files you can open in any web browser.

Both scripts are meant as starting points, not black boxes. Skim the comments, edit the paths, and adapt them to your own project layout and HPC environment.
