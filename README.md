# DataAugmentation

This project implements a slightly different version of the [Tri-training algorithm](http://ieeexplore.ieee.org/document/1512038/).
Dealing with classification tasks, is very difficult to obtain a large quantity of labeled data, due to the fact that usually this operation is done manually.
With this algorithm it is possible to expand each time the original dataset exploiting the knowledge on a small labeled set of data.

#### Algorithm

As previously said, this is a variation of the original algorithm.
Three classifiers are trained on the same dataset, then a set of unlabeled data is loaded.
To assign a label we have different case:
* All classifiers predict a pattern with the same label, assign that label to the new unseen pattern.
* Check all possible combinations among three classifiers.
* If two of them agree on the label, check if both predicted the pattern with a high confidence, i.e. threshold.
* Otherwise skip the pattern and take the next.

## Install
You can clone the repository in your local machine

`git clone https://github.com/caleale90/DataAugmentation.git`

or you can install it as Python package

`pip install dataaugmentation`

## Usage
The code can also be used from termina using the command:

`python ExpandTrainingSet ../training.csv ../unlabeled.csv ../out-file.csv --class_index 4 --separator | --threshold 0.9`

where:
* training.csv is the file containing the labeled data. Note that the class must be in the last field of the file
* unlabeled.csv is the file containing the unlabeled data.
* out-file.csv is the destination file
* class_index is an index which identifies the position of the class inside the dataset. All that occurs before that index will be treated as single element.
* separator is a character used to split fields in the csv file
* threshold is a value used to decide if a new labeled pattern must be kept or discarded.


