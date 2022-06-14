# Nextstrain_Quick_Start_Guide
This repository aims to provide a quick start guide to the installation, running, troubleshooting and tips of the Nextstrain workflow (https://nextstrain.org)

# 1. Introduction:


# 2. Pre-start notes:
  - Nextstrain is compatible with macOS, windows, WSL on windows, Ubuntu Linux and docker. 
  - The installation steps here will be for ***Ubuntu linux Native environment*** , if you use macOS you will find a file named macOS_installation_code.txt attached. Or if you use other OS system, you will find a link in the references section. 
  - In this quick guid we will take the ***SARS-CoV2 (ncov)**** workflow as an example. However, Nextstrain provide workflows for multiple pathogens. 

# 3. Installation: 

  ### 3.1 Install miniconda or Anaconda. (If you already have it skip this point)
   - If you want to choose between Anaconda and mini conda, This [link](https://www.educative.io/answers/anaconda-vs-miniconda) might help
   - [Anaconda installation guide](https://docs.anaconda.com/anaconda/install/)
   - [Miniconda Installation guide](https://docs.conda.io/en/latest/miniconda.html) 

  ### 3.2 Install memba tool on the base conda environment:
  ```
  $ conda install -n base -c conda-forge mamba --yes
  
  $ conda activate base
  ```
  ### 3.3 Install nextstrain components: 
   - Create a conda environment named nextstrain and install all the necessary software using mamba:
     ```       
     $ mamba create -n nextstrain -c conda-forge -c bioconda nextstrain-cli augur auspice nextalign snakemake git --yes
     ```
   - Activate the conda environment:
     ```
     $ conda activate mextstrain 
     ```     
   - Confirm that the installation worked.
     ```
     $ nextstrain check-setup --set-default 
     ``` 
   - The final output from the last command should look like this ```Setting default environment to <option>. ``` , where `<option>` is the option chosen in the previous step.

# 4. Installing pathogen specific workflow:
   Here you will find the list of pathogens that has a workflow in Nextstrain. https://nextstrain.org/pathogens 
   - If using the native runtime, install these additional packages necessary to run the ncovworkflow. Make sure to activate the correct conda environment.
      ```
        $ conda activate nextstrain     
        $ mamba install -c conda-forge -c bioconda epiweeks nextclade nextalign pangolin pangolearn 
      ```
      Sometimes using `conda` instead of `mamba` works !  
   
   - Download the ncov workflow:
        - Use `Git` to download a copy of the ncov repository containing the workflow and the testing data.
        ```
            $ git clone https://github.com/nextstrain/ncov.git 
        ```
# 5. After installation make sure that you have the following directories/files in your `#PATH/nextstrain/ncov` directory:
   - snakefile; nextstrain use snakemake as their workflow managment software 
   - data; location of the final input data
   - default; this contain all the defalt parameters for the workflow. Also, this directory contains two files you might need which are:
      - lat_longs.tsv: if you want to add the latitude and longitude of regions or countries that is not included in the default. to be presented in the final map. 
      - color_schemes.tsv: you can take color scheme id numbers if you want to add colors to your additional regions or countries. (we will talk about this in the buid.yml preparation section) 
   - my_profile; includes example profiles and this is where you will have your run_directory which contain your data preparation files and the build.yml and config.yml 
   - results
   - auspice: here is the visulization output `.jason` files location 
   - workflow; contain workflow
   - benchmark
   - docs
   - logs; you will find all the logs (also, helpful in case you face an error massage to identify the issue) 
   - narratives
   - nextstrain_profiles 
   - scripts 

# 6. 





# .Tips and tricks: 

# .References:
  1. [nextstrain/ncov](https://github.com/nextstrain/ncov)
  2. 
