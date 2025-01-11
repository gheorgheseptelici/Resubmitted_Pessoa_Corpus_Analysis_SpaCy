# Digital Corpus Processing of Fernando Pessoa's work with Python's spaCy module

![alt text](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*_KkW3OElfRLDBX1DijsWNQ.png)


## Project Description:
Fernando Pessoa was a Portuguese writer and one of the most important poets of the 20th century in Europe. An enigmatic figure, Pessoa's work is divided between his orthonymous writing and his writing under various aliases or, as he was calling them, heteronyms (of which there are around seventy-five). The writer firmly believed that there were multiple consciousnesses living inside him, each with their own biographies, passions and views on life. This is reflectled in the various themes and perspectives explored by Pessoa and his heteronyms in poetry and prose. For further reading on Pessoa and his heteronyms, https://poetrysociety.org/poems-essays/tributes/fernando-pessoa-his-heteronyms is a good resource.

Unfortunately, a rather modest part of Pessoa's (or his heteronyms) body of work is translated into English and an even smaller part is available digitally. This project aims to incentivize digital humanities scholars, but also scholars from other disciplines who are interested in the computational analysis of large corpora of texts, to build a digital, annotated corpus of Pessoa and his heteronyms' work in order to open new avenues of exploring his writing using text processing and distant viewing techniques performed by digital humanists. In order to create the annotations, the Jupyter Notebooks in this repository shall serve as a guide to anyone interested. Within it there is a detailed description on how to use the spaCy module in Python to perform advanced Natural Language Processing on the texts within the corpus. The bulk of the code is written there, but meaningful changes could be made depending on the research questions that scholars come up with.

An important digital resource of Pessoa's work can be found at https://www.pessoadigital.pt/en/index.html. While in Portuguese, this resource gathered a large part of Pessoa's (and his heteronyms') corpus and digitized them in machine readable format, along with each text's transcription. This resource could serve as a starting point for translating Pessoa's works into English and using annotation tools as the ones presented in the code below, in order to process and extract important linguistic features from his work. For speakers of Portuguese, the spaCy module that we will use in the code below (which for our case is set to the English pipeline) can be used with the Portuguese pipeline and perform similar tasks of text processing and annotation.

### Corpus Description and Text Selection Criteria:
The corpus in this repository contains a small dataset of three collections of Fernando Pessoa's work: [35 Sonnets](https://www.gutenberg.org/ebooks/19978), [English Poems: Volume 01 (of 2)](https://www.gutenberg.org/ebooks/66039), [English Poems: Volume 02 (of 2)](https://www.gutenberg.org/ebooks/66040), all taken from the Project Gutenberg website. The choice of these works is not arbitrary though: these are three works that did not need to be translated, since Pessoa wrote them in English originally and published under his own name. Some hypotheses could be explored already on this dataset, without running into the issue of having to account for the translation on which the analysis was done. 

### Target Audience and Intedend Use of the Corpus:
As mentioned briefly in the Project Description, the target audience are digital humanities scholars or scholars from other disciplines that have a passion for doing text analysis using computational tools. The corpus is intended to serve the production of knowledge by analyzing Pessoa's works through methods that were difficult or practically impossible before, i.e computational processing of large corpora of texts. Given Pessoa's rich literary universe, I believe that a lot of interesting research questions can be posed on the basis of this (developing) corpus. The most important thing is that researchers or other people using this corpus and the tools presented here are aware of the limitations of this corpus at any given moment and that responsible contribution or extraction of information from this repository is performed.

### Data Collection Process:
I downloaded the files directly from the Project Gutenberg website. The Project Gutenberg resource from which I extracted the metadata the works in the corpus was downloaded from https://www.gutenberg.org/cache/epub/feeds/.

### Cleaning and Preprocessing steps:
Since I downloaded the works in my initial corpus directly from the Project Gutenberg website I needed to perform some processing before I could get to the annotation, since Project Gutenberg includes a lengthy description of its licensing policy and other information that would impede a successful annotation of the texts. I used the simple-cleaner module from the gutenberg-cleaner package which was designed to do remove any information from the documents besides anything specifically relevant for the texts that they contain. Furthermore, I had to remove some unwanted characters like new lines (\n) or tabs (\t) in order to avoid the processing with spaCy to pick up on them and affect the annotation process. This was done using the regular expressions (re) package in Python.

### Annotations:
The processing done with spaCy in the original Notebook of this repository does a couple of annotation tasks such as: tokenization, lemmatization, extracting parts-of-speech for each token. I used the simple English Language model from spaCy but more accurate results could have been obtained using the more advanced Language models. To get the mentioned annotations I used spaCy functions such as token.text, token.lemma_, token.pos_.

### Further Analysis and Visualizations:
There is an additional Notebook in this repository, called 'Further_Analysis_and_Visualizations.ipynb', in which an exploration of spaCy's capabilities for Named Entity Recognition (NER) and Part-of-Speech tagging (POS) was explored and visualized. The results show that even the basic English language model used performed well with POS tagging. It did though encounter difficulties in the (NER) task, such as labeling wrong tokens as works of art or persons. This might be due to various factors, such as a limited dataset that the language model was trained on, the capital letters at the beginning of each poem line which were probably confusing the algorithm, as well as the poetic nature of the corpus, which uses words metaphorically and might further mislead the labeling process.

### Format of the Files:
The format of the files in the repository are: .txt for the text documents, .csv for the tables with the annotated data (Corpus_data_and_annotations.csv) and the corpus metadata (generated through the code in the Notebook), and .ipnyb for the Jupyter Notebooks.

The columns in the annotated .csv file and their descriptions are illustrated in the table below:
| Header        |Description            |
| ------------- |:-------------:|
| Filename| The name of the file  |  
| Type|The type of the file   |    
| Issued |The date when the document was created on Project Gutenberg. Note: not the original date when Pessoa's texts were published       |     
| Title |The official title of the work      |
| Language |Language of the work in the corpus        |
| Authors |Authors of the work in the corpus       |
| Subjects |The genre of the works in the corpus      |
| LoCC |Library of Congress Classification that the works from the corpus fit in      |
| Bookshelves |Project Gutenberg Bookshelves that have similar works to the one in the corpus      |
| Document |The original document as downloaded from the Project Gutenberg website     |
| Raw_text |The processed document with unnecessary characters and information removed      |
| Doc |The Doc object that gets created when spaCy is implemented and on which it operates      |
| Tokens |All the tokens contained in the corpus' texts      |
| Lemmas |The lemmas of the tokens contained in the corpus' texts     |
| POS |The detected parts-of-speech of the tokens contained in the corpus' texts      |

### Python packages used:
Please note that in order to run the code in these Notebooks you will need to install the following Python packages: spaCy, pandas, plotly, nbformat, gutenberg-cleaner, re.

## License:
The dataset is available under the terms of the [Project Gutenberg License](https://www.gutenberg.org/policy/license.html).
