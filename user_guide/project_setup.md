# Setup your Project and Configure your Run

The assumed project sub-directory structure within this guide is as follows:

```
/home/$USER/projects/yyyy_mm_dd_project_name/
|-- data
|   |-- raw
|   |-- reference
|   `-- sample_sheet
|-- results
`-- src
    |-- nf_config
    |-- nf_params
    `-- shell
```

This directory tree can be established by running the command shown below from within the `/home/$USER/projects` directory.

```bash
# setup project directory structure
mkdir -p ./yyyy_mm_dd_project_name/{data/{raw,reference,sample_sheet},results,src/{nf_config,nf_params,shell}}
```

Many nf-core pipelines require a sample sheet detailing the files you wish to analyse. You can find nf-core pipelines by visiting [https://nf-co.re/pipelines](https://nf-co.re/pipelines). Each pipeline page has more information on how to use the pipeline as well as a full description of sample sheet requirements and formatting.

Your sample sheet should be located inside your `sample_sheet` sub-directory.

There are two other things you will require to run an nf-core pipeline:

1. A pipeline launcher parameter configuration file
2. A submission script

The general launch command in the script template provided here assumes you have configured your specific run using an nf-core pipeline launcher. For example, the launcher for the nf-core/rnaseq pipeline that can be found [here](https://nf-co.re/launch?pipeline=rnaseq). The parameters specified for your run using the launcher should be saved in a file named `nf-params.json` within the `nf_params` sub-directory.

To create your run script, navigate to the `script` sub-directory and run the following:

```shell
nano nf_run.sh
```

Paste the contents of the template file linked below into the editor ensuring to change the generic information for your own where indicated in the comment lines.

[Template run submission script](../templates/script/run_script_template.sh)

Now save and exit by typing "Ctrl + O" then "Return" then "Ctrl + X".