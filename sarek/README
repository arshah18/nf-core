Hi,
I am trying to run sarek in offline mode for somatic variant calling.
Command and Error shown below,
The plugins directory is a read only one and you cannot write to that directory. From my machine where the internet is not available, this path is read-only.
But why would sarek want to write to that directory. There are plugins already there like one shown below:

# Start the nf-core on amazon
nf-amazon-2.1.4 
nf-prov-1.2.1 
nf-validation-1.1.3

# Commands
export NXF_SINGULARITY_CACHEDIR=/cluster/share/nf-core/singularity_sarek_3.4.0
export SINGULARITY_CACHEDIR=/cluster/projects/tmp_tinu/singularity/cache_dir
export NXF_TEMP=/cluster/projects/tmp_tinu/tmp/
export SINGULARITY_TMPDIR=/cluster/projects/tmp_tinu/singularity/tmp/

OUTDIR=/cluster/projects/pipeline_runs/DNA/somatic/sarek_3.4.0_results
mkdir -p ${OUTDIR}

export NXF_OFFLINE='true'
export NXF_HOME=/cluster/apps/shared/nextflow_home
export NXF_PLUGINS_DIR=/cluster/customapps/shared/nextflow_home/plugins


module load StdEnv/2023
module load java/17.0.6

/cluster/customapps/shared/nextflow/nextflow run /cluster/share/nf-core/workflows/sarek-3.4.0/workflow \
--tools freebayes, mutect2, strelka2 \
--step mapping \
--igenomes_base /cluster/share/nf-core/references/sarek_3.4.0 \
--input /cluster/projects/DNA/somatic/prostate_WES_somatic_samples.csv \
--save_mapped \
--save_output_as_bam \
--max_cpus 3 \
--outdir ${OUTDIR} \
-c $(pwd)/ethz.config -resume
