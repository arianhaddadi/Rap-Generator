# Rap Generator Model

This repository is for training a model used for generating Persian Rap lyrics. 

## General Methodolgy
At first, rap music lyrics from 32 Persian rappers were crawled. Then, special tokens containing indicators for sentence separators and the beginning of the rap text were added to them. Then, a GPT-2 model was fine-tuned on the crawled data so that it could understand the charactrsitics of Persian rap and the rapping style of those 32 rappers. Afterwards, the model was used to generate rap music for those rappers. GPT generates text in a sentence-by-sentence manner and can generate different sentences for the same base text. In order to enhance the quality of the generated text, a BERT model was used to choose the most suitable sentence between the candidate sentences that the GPT-2 model was able to produce. The reason that the BERT model came in handy was that the BERT model had a feed forward head which was trained for determining whether two sentences are consecutive. This model was fine-tuned on the crawled data and then, both of the models were leveraged to generate the final text.


## Files
- data.csv: This files contains a dataframe containing and entry for each of the crawled rap songs. The texts contain special tokens that separate sentences and indicate the rapper name along with the start of the text.

- prepare_dataset.ipynb: This notebook contains the code for crawling the data and creating the data.csv file.

- bert_notebook.ipynb: This notebook contains the code used for fine-tuning the BERT model.

- notebook.ipynb: This notebook contains the code for fine-tuning the GPT-2 model and also using the already fine-tuned BERT model to generate the final text for any of the rappers.