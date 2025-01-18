# Snakemake-workflows
Snakemake workflows for whole genome bioinformatic analyses. This workflow assumes you already have a conda environment set up (and are currently in said activated environment) for the programs used. I recommend running the snakemake command on a separate screen. You may also add additional log files to output throughout the process if you wish. 

# Raw data to vcf files - Snakemake2
This is a simple workflow for whole-genome analysis, starting from raw paired-end fastq files (already quality-checked) and ending with vcf files (which should be changed to bcf to save space). 
This workflow assumes you have a list of sample names (put in a list at the top of the Snakefile, separated by commas) that you would like to iterate the commands over.
This particular pipeline uses bwa mem, samtools, picard, and bcftools to align reads to a reference genome, sort the resulting sam files, and call variants using bcftools mpileup, which may be easily changed to GATK. 

# Compress vcf files
This is optional, but in order to sort and index the bcf files, they need to be smaller in order to save space. This is a simple file that will do that fairly quickly. 

# Config files for running on remote cluster
It is recommended that you create a config file (config.yaml) that neatly tells Snakemake where to run the workflow. You can add this to the Snakemake command by simply adding --profile attach/path/to/profile. This way you can set a default run time, number of cores, nodes, and jobs to use. Make sure to not overload your cluster or things may run more slowly. 

# THIS is still a WIP.
Just be cautious and use at your own risk. I've made lots of changes to these over time and will eventually get to uploading new ones.
