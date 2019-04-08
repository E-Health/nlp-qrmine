# :flashlight: QRMine

QRMine is a suite of qualitative research (QR) support tools in Python using Natural Language Processing (NLP) and Machine Learning (ML). QRMine is still work in progress and is not ready for use.

## What it does

### NLP
* [x] Lists common categories for open coding.
* [x] Create a coding dictionary with categories, properties and dimensions.
* [x] Topic modelling.
* [x] Arrange docs according to topics.
* [x] Compare two documents/interviews.
* [x] Select documents/interviews by sentiment, category or title for further analysis.
* [x] Sentiment analysis
* [ ] Network analysis
* [ ] Co-citation finder

### ML
* [x] Accuracy of a neural network model trained using the data
* [x] Confusion matrix from an support vector machine classifier
* [x] K nearest neighbours of a given record
* [x] K-Means clustering
* [x] Principal Component Analysis (PCA)
* [ ] Association rules

## How to use

* Download/clone this repository
* pip install -r requirements.txt
* python qrmine.py ( --help to display all command line options)
* input files are transcripts as txt files and a single csv file with numeric data. The output txt file can be specified.

* The coding dictionary, topics and topic assignments can be created from the  entire corpus (all documents) using the respective command line options.

* Categories (concepts), summary and sentiment can be viewed for entire corpus or specific titles (documents) specified using the --titles switch. Sentence level sentiment output is possible with the --sentence flag.

* You can filter documents based on sentiment, titles or categories and do further analysis, using --filters or -f

* Many of the ML functions like neural network takes a second argument (-n) . In nnet -n signifies the number of epochs, number of clusters in kmeans, number of factors in pca, and number of neighbours in KNN. KNN also takes the --rec or -r argument to specify the record.

* Variables from csv can be selected using --titles (defaults to all). The first variable will be ignored (index) and the last will be the DV (dependant variable). 


### Command-line options

| Command | Alternate | Description |
| --- | --- | --- |
| --inp | -i | Input file in the text format with <break> Topic </break> |
| --out | -o | Output file name |
| --csv |   | csv file name |
| --num | -n  | N (clusters/epochs etc depending on context) |
| --rec | -r  | Record (based on context) |
| --titles | -t | Document(s) title(s) to analyze/compare |
| --codedict |   | Generate coding dictionary |
| --topics |   | Generate topic model |
| --assign |   | Assign documents to topics |
| --cat |   | List categories of entire corpus or individual docs |
| --summary |   | Generate summary for entire corpus or individual docs |
| --sentiment |   | Generate sentiment score for entire corpus or individual docs |
| --nlp |   | Generate all NLP reports |
| --sentence |   | Generate sentence level scores when applicable |
| --nnet |   | Display accuracy of a neural network model -n epochs(3)|
| --svm |   | Display confusion matrix from an svm classifier |
| --knn |   | Display nearest neighbours -n neighbours (3)|
| --kmeans |   | Display KMeans clusters -n clusters (3)|
| --cart |   | Display Association Rules |
| --pca |   | Display PCA -n factors (3)|


## Input file format

### NLP
Individual documents or interview transcripts in a single text file separated by <break>Topic</break>. Example below

```
Transcript of the first interview with John.
Any number of lines
<break>First_Interview_John</break>

Text of the second interview with Jane.
More text.
<break>Second_Interview_Jane</break>

....
```

Multiple files are suported, each having only one break tag at the bottom with the topic.
(The tag may be renamed in the future)

### ML

A single csv file with the following generic structure.

* Column 1 with identifier. If it is related to a text document as above, include the title.
* Last column has the dependent variable (DV). (NLP algorithms like the topic asignments may provide the DV)
* All independent variables (numerical) in between.

```
index, obesity, bmi, exercise, income, bp, fbs, has_diabetes
1, 0, 29, 1, 12, 120, 89, 1
2, 1, 32, 0, 9, 140, 92, 0
......

```

## Author

* [Bell Eapen](https://nuchange.ca) (McMaster U) |  [Contact](https://nuchange.ca/contact)
* This software is developed and tested using [Compute Canada](http://www.computecanada.ca) resources.
* See also:  [:fire: The FHIRForm framework for managing healthcare eForms](https://github.com/E-Health/fhirform)
* See also: [:eyes: Drishti | An mHealth sense-plan-act framework!](https://github.com/E-Health/drishti)

## Citation

Please cite QRMine in your publications if it helped your research. Here
is an example BibTeX entry:

```

@misc{eapenbr2019qrmine,
  title={QRMine -Qualitative Research Tools in Python.},
  author={Eapen, Bell Raj and contributors},
  year={2019},
  publisher={GitHub},
  journal = {GitHub repository},
  howpublished={\url{https://github.com/dermatologist/nlp-qrmine}}
}

```

Publication with the theoretical foundations of this tool is being worked on. QRMine is inspired by [this work](https://github.com/lknelson/computational-grounded-theory) and the associated [paper](https://journals.sagepub.com/doi/abs/10.1177/0049124117729703).


## Demo

[![QRMine](https://raw.github.com/dermatologist/nlp-qrmine/develop/notes/qrmine.gif)](http://nuchange.ca)
