# udacity-sparkify
*Repository for the Udacity's Data Science Nanodegree Capstone Project, the Sparkify.*

This repository's goal is to manipulate large and realistic datasets with Spark to engineer relevant features for predicting churn, which is a challenging and common problem that Data Scientists and Analysts regularly encounter in any customer-facing business.\
In here you will find a small sample (128 Mb) of the actual data (12 Gb) that can be located at **AWS**.

## Table of contents
* [Technologies]($Technologies)
* [Installation](#Installation)
* [Files](#Files)
* [Usage](#Usage)
* [Analysis](#Analysis)
* [Results](#Results)
* [Possible Improvements](#Possible-Improvements)
* [Collaborating](#Collaborating)
* [Future Work](#Future-Work)

## Technologies

This project uses:

* Python 3.8.7

And the packages:

* Pyspark 2.4.6
* Numpy 1.19.2
* Pandas 1.2.1
* MatplotLib 3.3.2
* Seaborn 0.11.1
* Datetime built-in
* Re 2.2.1

## Installation

```
$ git clone https://github.com/LuisGaravaso/udacity-sparkify
```

## Files

Once you clone the repo, you'll get the following files:

* **Sparkify.ipynb** : Jupyter Notebook with the complete Data Science workflow
* **mini_sparkify_event_data.zip**: Compressed Folder containing the `.json` file
* **README** : This README
* **LICENSE** : MIT License

The mini_sparkify_event_data.json contains 286500 records (with null userIds) and 225 distinct users.

Data schema: \
root:\
|-- artist: string (nullable = true)\
|-- auth: string (nullable = true)\
|-- firstName: string (nullable = true)\
|-- gender: string (nullable = true)\
|-- itemInSession: long (nullable = true)\
|-- lastName: string (nullable = true)\
|-- length: double (nullable = true)\
|-- level: string (nullable = true)\
|-- location: string (nullable = true)\
|-- method: string (nullable = true)\
|-- page: string (nullable = true)\
|-- registration: long (nullable = true)\
|-- sessionId: long (nullable = true)\
|-- song: string (nullable = true)\
|-- status: long (nullable = true)\
|-- ts: long (nullable = true)\
|-- userAgent: string (nullable = true)\
|-- userId: string (nullable = true)

If you wish, the entire dataset (12 Gb) can be found at:
* ```s3n://udacity-dsnd/sparkify/sparkify_event_data.json```

And the medium sized (6 Gb) dataset can be found at:
* ```https://video.udacity-data.com/topher/2018/December/5c1d6681_medium-sparkify-event-data/medium-sparkify-event-data.json```

## Usage

Unzip the data, open the Sparkify Jupyter Notebook and Run All.\
If you wish, use the user defined functions to add more transformations or try different Spark Machine Learning models.\
You can also deploy this notebook to **AWS** or **IBM Cloud** if you wish.

## Analysis

Check the [Medium Post](https://medium.com/@luisgaravaso/this-will-make-us-brazilians-rethink-our-energy-investments-525b9c49a087) about it.

## Models Tuning/Refinement

GridSearch was applied to the models using the `ParamGridBuilder()` and the `TrainValidationSplit()` instances.
On my local machine with the small dataset, the *LogisticRegression* took about 1h30 testing 12 combinations and the *RandomForest* took about 55 minutes testing 9 combinations.

## Results

1. The metric was **AUC** which is default to Spark's `BinaryClassificationEvaluator` and it is widely used in binary and unbalanced classification.
1. The **RandomForest** (0.96605) performed better than the **LogisticRegression** (0.91975)
1. The **RandomForest** gave more importance to *time-related features* such as: `max and avg time between sessions` and did not ignore any feature.
1. The **LogisticRegression** on the other hand gave little or zero importance to features found to be good during the **EDA**, such as: `max and avg time between sessions` and `gender`.

## Possible Improvements

1. **Testing other models**, such as *SupportVectorMachines* and *GradientBoostingMachines*.
1. **Dropping Features**, such as Gender, that was not considered important in the end.
1. **Engineering other features**, such as more time based features, like average song length.

## Collaborating

Send me a connection request on Linkedin: https://www.linkedin.com/in/luisgaravaso/ \
That way you can send me files, urls or advice on the analysis.

## Future Work

I do not have intentions of continuing this work.
