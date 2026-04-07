# Generate an Optimized MyGenome Assembly using Velvet and SPAdes

## Run Velvet using a range of k-mer values:
`sbatch velvetoptimiser.sh Sg341 57 137 10`
`sbatch velvetoptimiser.sh Sg341 89 105 2`

## Run SPAdes
`sbatch spades.sh . Sg341`

## Count the # of contigs using grep
`grep -v ">" Sg341_spades_assembly/scaffolds.fasta | tr -d '\n' | wc -c`

`singularity run --app seqkit2900 /share/singularity/images/ccs/conda/amd-conda19-rocky9.sinf seqkit stats Sg341/contigs.fa`
`singularity run --app seqkit2900 /share/singularity/images/ccs/conda/amd-conda19-rocky9.sinf seqkit stats Sg341/velvet_Sg341_57_137_10_noclean/contigs.fa`
`singularity run --app seqkit2900 /share/singularity/images/ccs/conda/amd-conda19-rocky9.sinf seqkit stats Sg341/velvet_Sg341_89_105_2_noclean/contigs.fa`
`singularity run --app seqkit2900 /share/singularity/images/ccs/conda/amd-conda19-rocky9.sinf seqkit stats Sg341_spades_assembly/scaffolds.fa`
`perl SimpleFastaHeaders.pl Sg341/velvet_Sg341_89_105_2_noclean/contigs.fa Sg341`

`sbatch GenomePostProcess.sh Sg341_newheader.fasta`

`singularity run --app seqkit2900 /share/singularity/images/ccs/conda/amd-conda19-rocky9.sinf seqkit stats Sg341_final.fasta`

`grep -v ">" Sg341_final.fasta | tr -d '\n' | wc -c`
`./n50.sh Sg341_final.fasta`
`./n50.sh Sg341_spades_assembly/scaffolds.fasta`
`sbatch Spades-paired.sh . Sg341`
