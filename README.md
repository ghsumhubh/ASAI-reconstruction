
# ASAI reconstruction

A reconstruction of the main results of the paper [Enhancing CRISPR-Cas9 gRNA efficiency
prediction by data integration and deep learning](https://www.nature.com/articles/s41467-021-23576-0)

## Requirements

We reccomend using the requirements listed in

https://github.com/RTH-tools/crispron

We personally used python 3.6 for our reconstruction whenver running CRISPRon scripts (With their reccomended versions), while for the preprocessing steps done in interactive python notebooks we used the following configuration on a windows 11 machine:

- Python 3.11.4
- numpy                   1.26.4
- pandas                  2.2.2
- matplotlib              3.8.4
- scipy                   1.13.0
## Running the Reconstruction

### Cloning CRISPRon's repo
Clone the repository from 

https://github.com/RTH-tools/crispron

Navigate to the folder /modified_crispron under our repository.

Move the following file into the cloned repository folder:

`ASAI-reconstruction/modified_crispron/DeepCRISPRon_train.py`

to
`crispron/bin/`



### Getting the data

Download supplementary Data 1 from
https://www.nature.com/articles/s41467-021-23576-0

Save TRAP12k microarray oligos tab as co_sequences.csv
Save spCas9_eff_D8-dox tab as co2.csv
Save spCas9_eff_D10-dox as co4.csv

Put all three files in /Original files

Download aax9249_table_s1.xlsx from 
https://www.science.org/doi/10.1126/sciadv.aax9249

Save HT_Cas9_Train tab as kim1.csv
Save HT_Cas9_Test tab as kim2.csv

Put both files in /Original files

### Combining the data
Run the notebook `1_initial_preprocessing.ipynb`

### Getting ready for CRISPRoff
Run the notebook `2_prepare_co_for_crisproff.ipynb`

### Running CRISPRoff
Move the file Before CRISPRoff/co_and_kim_30.fa and place it in the main folder of the cloned CRISPRon folder.

Navigate to the CRISPRon folder using `cd <folder_name>`

Run `./bin/CRISPRon.sh co_and_kim_30.fa latest`

After the scripts finishes, navigate to the newly created `latest` folder and copy all the files to `ASAI-reconstruction/After CRISPRoff`

### Reconstructing the features
Run the notebook `3_aftercrisproff.ipynb`


### Running CRISPRon
Move the file `After CRISPRoff/co_data.csv` to 
`crispron/bin/`

Run `python DeepCRISPRon_train.py`
## Acknowledgements

 - [CRISPRon](https://www.nature.com/articles/s41467-021-23576-0) for the architecture and data.
 - [Kim2019](https://www.science.org/doi/10.1126/sciadv.aax9249) for part of the data.
