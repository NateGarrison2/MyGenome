# Generate an Optimized MyGenome Assembly using Velvet and SPAdes

Run Velvet using a range of k-mer values:
>`sbatch velvetoptimiser.sh Sg341 57 137 10`
>`sbatch velvetoptimiser.sh Sg341 89 105 2`

Check stats for the Velvet Round 1 assembly
>`singularity run --app seqkit2900 /share/singularity/images/ccs/conda/amd-conda19-rocky9.sinf seqkit stats Sg341/velvet_Sg341_57_137_10_noclean/contigs.fa`

Check stats for the Velvet Round 2 assembly
>`singularity run --app seqkit2900 /share/singularity/images/ccs/conda/amd-conda19-rocky9.sinf seqkit stats Sg341/velvet_Sg341_89_105_2_noclean/contigs.fa`

Run SPAdes
>`sbatch spades.sh . Sg341`

Run SPAdes on paired-end reads
>`sbatch Spades-paired.sh . Sg341`

Check stats for the SPAdes assembly
>`singularity run --app seqkit2900 /share/singularity/images/ccs/conda/amd-conda19-rocky9.sinf seqkit stats Sg341_spades_assembly/scaffolds.fa`

Count the # of contigs using grep
>`grep -c ">" Sg341_spades_assembly/scaffolds.fasta`

Alternative manual checks for genome size and N50 on SPAdes
>`grep -v ">" Sg341_spades_assembly/scaffolds.fasta | tr -d '\n' | wc -c`
>`./n50.sh Sg341_spades_assembly/scaffolds.fasta`

>`singularity run --app seqkit2900 /share/singularity/images/ccs/conda/amd-conda19-rocky9.sinf seqkit stats Sg341/contigs.fa`

Simplify headers
>`perl SimpleFastaHeaders.pl Sg341/velvet_Sg341_89_105_2_noclean/contigs.fa Sg341`

`sbatch GenomePostProcess.sh Sg341_newheader.fasta`

`singularity run --app seqkit2900 /share/singularity/images/ccs/conda/amd-conda19-rocky9.sinf seqkit stats Sg341_final.fasta`

`grep -v ">" Sg341_final.fasta | tr -d '\n' | wc -c`
`./n50.sh Sg341_final.fasta`

