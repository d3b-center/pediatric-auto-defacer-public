# PedsAutoDeface tool

This tool can be used to automatically deface pediatric brain MRIs (trained on T1w, T2w, T2w-FLAIR, T1w contrast-enhanced). It was trained using the nnU-Net framework on a multi-institutional, heterogeneous dataset (see reference).

Input files can be unprocessed or pre-processed images.

If further training/fine-tuning is desired, the trained model weights can be accessed here: [https://drive.google.com/file/d/1P06VrdaMxX_VENOYVRyvFgJN82SMEsMz/view?usp=sharing](https://drive.google.com/file/d/1P06VrdaMxX_VENOYVRyvFgJN82SMEsMz/view?usp=sharing)

If you use this tool in your work, please cite the following reference accordingly:

Familiar, A. M., Khalili, N., Khalili, N., Schuman, C., Grove, E., Viswanathan, K., ... & Nabavizadeh, A. (2024). Empowering Data Sharing in Neuroscience: A Deep Learning De-identification Method for Pediatric Brain MRIs. American Journal of Neuroradiology.

Link to paper: [https://doi.org/10.3174/ajnr.A8581](https://doi.org/10.3174/ajnr.A8581)

## STEP 1: Prepare the input files

### Organization

Input files must be located in an `input/` directory folder (called "input") in NIfTi file format. The exact naming of the files does not matter, the container will process all NIfTi files in the `input/` directory separately (the format of the output name of each file will be: `[input-file-name]_defaced.nii.gz`).

For example input files for a single subject could describe the image type:
```
input/
    t1ce.nii.gz
    ...
```

Or include the subject IDs if there are more than one subject:

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

It takes about an hour to fully process 1 MRI file (with 16 GB memory, 2 GHz 4 cores; however, this depends on your machine specs). Defaced images will be stored in an `output/` folder with files named `[input-file-name]_defaced.nii.gz` and the model-predicted face mask as `[input-file-name]_face_mask.nii.gz`, for example:

```
input/
    t1ce_defaced.nii.gz
    t1ce_face_mask.nii.gz
    ...
```


## Issues

Please submit any issues you find while using the tool here: [...].
