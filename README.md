# GSoC-2020
## RDF - to - text generator, using GANs and reinforcement learning. For Google summer of code 2020.

This folder contains the final code of the Google Summer of Code program.

The project concerns developing an end-to-end system that takes RDF (Resource Description Framework) triples as input, and generates an adequate verbalization therefrom.

The approach taken is to setup an adversarial training workflow, where two networks (transformers chosen as final model) are trained together.
The Generator is trained to generate text from given triples, whereas the discriminator is trained to distinguish between real triple text pairs, and fake (generated ones)

In order to reproduce the experiments, you will need to install the *requirements.txt* file. The processed data files (for both .json and .xml format corpus) have been provided under the transformers/data directory. To generate custom data files, you may use the xml & json parser scripts, under the data_utils directory.

**In order to recreate the final results, you will need to download the model weights for the discriminator and the generator, here:**

- Generator weights:
- Discriminator weights: 


### 1) Preprocessing files

It is worth noting that the folder data already contains all the files processed.

In order to use a custom dataset (from .xml or .json format files), you may use the scripts from the data_utils directory

#### 1.1) To create dataset from .xml files, run the following command:
 - ```python xml_parser.py --out_file path_to_output_file.txt --in_dir path_to_xml_files ```

#### 1.2) To create dataset from .json files, run the following command:
- ``` python xml_parser.py --out_file path_to_output_file.txt --in_dir  path_to_json_files ``` 
                       
#### 1.3) To create datasets from both file types, run the following command:
 - ``` python create_raw_datasets.py --json_out_file path_to_json_output_file.txt --json_in_dir  path_to_json_files --xml_out_file path_to_xml_file.txt --xml_in_dir  path_to_xml_files ```
                 
#### 1.4) Link to data files 
- *The source .xml files used for this project can be found [here](https://github.com/ThiagoCF05/webnlg/tree/master/data/v1.5/en/train)*

- *The augmented raw json data, which was created by delexicalizing the enriched WebNLG corpus then relexicalizing the corpus with new entities, can be found [here](https://drive.google.com/drive/folders/1Q6SGvJRjZP_97o_jBkirUNpe9qmulx1N?usp=sharing).*

- *The relexicalization script can be found [here](https://github.com/ThiagoCF05/webnlg/blob/synthetic/synthetic.py)*

### 2) Pre-training

#### 2.1) Generator
Here is an example of how to pretrain the generator.

  ``` python generator_pretraining.py -- ```
  

#### 2.2) Discriminator
Here is an example of how to pretrain the discriminator.

  ``` python discriminator_pretraining.py -- ```
  
### 3) Adverserial training
Here is an example of how to launch the adverserial training script.
  ``` python adverserial_training.py -- ```
  
### 4) Generate predictions

You can also load in pre-trained weights for the generator, and make predictions on a test set.
The test set is constructed using the same scripts as the training set, found under data_utils directory.

Here is an example of how to generate verbalizations on a test set, and save the reference and hypothesis files for automatic evaluation:
  ``` python generate_verbalizations.py -- ```
  
  

