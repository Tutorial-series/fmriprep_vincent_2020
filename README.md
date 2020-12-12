# fmriprep_vincent_2020
------
The fmriprep tutorial for COSN @2020 by Qing Wang (Vincent).
## Commands for building fMRIPrep containers
```sudo docker pull poldracklab/fmriprep:latest```

```sudo singularity build fmriprep_latest.simg docker://poldracklab/fmriprep:latest```
## Running fMRIPrep on local machine
### Docker
```sudo docker run -it -v host_bids_dir:/data:ro -v host_derivates_dir:/out poldracklab/fmriprep:latest /data /out --participant_label sub-0001```
...You need to change "host_bids_dir" for your BIDS path on your machine, and \data is the BIDS path inside the container;
...You need to change "host_derivates_dir" for your output directory. 
### Singularity
```singularity run --cleanenv -B host_bids_dir:/data:ro -B host_derivates_dir:/out fmriprep_latest.simg (singularity container) /data /out --participant_label sub-0001```
## Running fMRIPrep on slurm HPC (codes in /scripts)
### fmriprep.sh
Prepare running env and submit job.
### fmriprep.slurm
Scripts for running fMRIPrep in parallel.
### fmriprep.format
Collect the results.
### select_ses-2.json
Select specific input data (session 2 here for both T1 and bold images).
