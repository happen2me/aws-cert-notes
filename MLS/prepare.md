# Data Prepare

### Concepts

**Options for Data Preparation**

Ad hoc: SageMaker Jupyter Notebook

Reusable: ETL Jobs in AWS Glue

### Categorical Encoding

**Order matters?**

- Nominal: no
  - One-hot
- Original: yes (L, M, S)
  - Encode to continuous values

**One-hot**

- When there are many categories
  - Grouping by similarity
  - Mapping rare values to 'other'

### Text Feature Engineering

**Bag-of-words**

Text represented by words and their counts, ignoring order.

- Tokenize raw text and creates statistical  representation of the text
- Breaks up text by white space into single words

**N-gram**

Groups of words of n-size

**Orthogonal Sparse Bigram (OSB)**

Creates groups of words of size *n* and output every pair of words that includes the first word.

- Useful for finding common word combination

Example:

```
Raw text: He is a Jedi and he will save us
OSB window size: 4
Encoding:
{He_is, He__a, He___Jedi}
{is_a, is__Jedi, is___and}
...
```

**TF-IDF**

IMU: Frequent words across documents are less important.
$$
idf(t, D) = log\frac{N}{|d∈D:t∈d|}
$$
$$
tf-idf(t, d, D) = tf(t,d) * idf(t, D)
$$

**Feature Engineering**

- Remove punctuation
- Lowercase

**Cartesian Product Transformation**

Creates new features from the combination of two or  more text or categorical values.

IOW: Multipy a set of words by another set of words to create new features

Example:

```
Textbooks:
Python Data Science
Label:
softcover
Cartesian product:
{Python_softcover, Data_softcover, Science_softcover}
```

**Dates** - translate dates into useful information

Example:

```
Date:
2015-06-17
Encoding:
is_weekend: 0
day_of_week: 2
month: 6
year: 2015
```

### Numeric Feature Engineering

**Feature Scaling**

Change numeric values to the same scale

- Normalization:
  -  *i.e.* scale prices to [0, 1]
  - Problem: outlier kills
  - Solution: random cut forest
- Standardization
  - Put average price to 0, and use z-score to handle remainder values
  - take account into average and standard deviation
  - $z=\frac{x - \bar{x}}{\delta}$

**Binning** - values to categoric

Change numeric values into groups or buckets of similar values, to reduce small increments of the data

- when the numbers don't have linear relation with results
- *i.e.* age 40 and 41 are all groupped to 30~50 years old.

- Quantile binning: assign the same number of features to each bin

### Other Feature Engineering

- Image Feature Engineering
  - *i.e.* image to 0,1 values
- Audio Featuring Engineering
  - *i.e.* Sample at equal interval

**Dataset Formats**

- File: load all data from s3 onto training volume
  - Csv, parquet, json, images...
- Pipe: Stream data directly from s3
  - RecordIO-protobuf (it creates tensor)

### Handle Missing Values

**Missingness Mechanism**

- Missing at Random (MAR)
- Missing Completely at random (MCAR)
- Missing Not at Random (MNAR)

**Handles**

- Fill by supervised learning
  - most difficult, best result
- Repalce with mean, median (middle) or mode (most common)
- Drop rows

First two are called **imputation**

### Feature Selection

**Manual Selection**

- Human takes to reduce features

**Principal Component Analysis**

- Unsupervised learning to reduce feature dim

### AWS Data Preparation Tools

**AWS Glue** - Reusable

- Managed ETL service
- Python or Scala code to transform dataset
- Output to a given S3
- One-stop shop for ETL

![AWS Glue（分析用データ抽出、変換、ロード (ETL) ）| AWS](https://d1.awsstatic.com/aws-glue-graphics/Product-page-diagram_AWS-Glue_Elixir%402x.6511bc93abc20bb7bc8d03ebe2be1cbb7f2623fe.png)

- Crawler: scan input, comes up with metadata information or infer schema
- ETL Job
  - Spark job

**SageMaker** - Ad Hoc

**EMR**

We can do all data preparation in EMR.

**Athena**

Run SQL-like query on S3. Can the used for data preparation.

**Data pipeline**

Move data between AWS sources

**Which to use?**

![comparision from acloud guru](https://i.imgur.com/pvkCy0D.png)

### Exam Tips

