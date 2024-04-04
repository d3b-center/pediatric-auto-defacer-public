# PedsAutoDeface tool

This tool can be used to automatically deface pediatric brain MRIs (trained on T1w, T2w, T2w-FLAIR, T1w contrast-enhanced). It was trained using the nnU-Net framework on a multi-institutional, heterogeneous dataset (see reference).

Input files can be unprocessed or pre-processed images.

If you use this tool in your work, please cite the following reference accordingly:

[...]

## STEP 1: Prepare the input files

### Organization

Input files must be located in an `input/` directory folder (called "input"):

For example:
```
input/
    sub001_t1.nii.gz
    sub001_t2.nii.gz
    sub001_fl.nii.gz
    sub002_t1.nii.gz
    sub003_t1ce.nii.gz
    ...
```

## STEP 2: Usage

1. [Install Docker](https://docs.docker.com/engine/install/)
2. copy the `docker-compose.yml` file from this repository into the directory that contains your `input/` folder:
    ```
    docker-compose.yml
    input/
        sub001_t1.nii.gz
        sub001_t2.nii.gz
        ...
    ```
3. from within that folder, run the command:
    ```
    docker compose up
    ```

It takes about an hour to fully process a single subject's data (with 16 GB memory, 2 GHz 4 cores; however, this depends on your machine specs). Defaced images will be stored in an `output/` folder with files named `[input-file-name]_defaced.nii.gz` .

## Issues

Please submit any issues you find while using the tool here: [...].
