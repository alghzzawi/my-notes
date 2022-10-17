# Data Analysis with Pandas

### This is a short introduction to pandas, geared mainly for new users. You can see more complex recipes in the Cookbook.

### Customarily, we import as follows:

    In [1]: import numpy as np
            import pandas as pd

## Object creation
### See the Intro to data structures section.

### Creating a Series by passing a list of values, letting pandas create a default integer index:

    In [2]: s = pd.Series([1, 3, 5, np.nan, 6, 8])
            s
    Out[4]: 
            0    1.0
            1    3.0
            2    5.0
            3    NaN
            4    6.0
            5    8.0
            dtype: float64
### Creating a DataFrame by passing a NumPy array, with a datetime index using date_range() and labeled columns:

    In [3]: dates = pd.date_range("20130101", periods=6)
    dates

    Out[3]: 
            DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
               '2013-01-05', '2013-01-06'],
              dtype='datetime64[ns]', freq='D')

    In [4]  df = pd.DataFrame(np.random.randn(6, 4), index=dates, columns=list("ABCD"))
            df
    Out[4]: 
                            A         B         C         D
            2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
            2013-01-02  1.212112 -0.173215  0.119209 -1.044236
            2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
            2013-01-04  0.721555 -0.706771 -1.039575  0.271860
            2013-01-05 -0.424972  0.567020  0.276232 -1.087401
            2013-01-06 -0.673690  0.113648 -1.478427  0.524988

### Creating a DataFrame by passing a dictionary of objects that can be converted into a series-like structure:

    In [5]: df2 = pd.DataFrame(
                {
                    "A": 1.0,
                    "B": pd.Timestamp("20130102"),
                    "C": pd.Series(1, index=list(range(4)), dtype="float32"),
                    "D": np.array([3] * 4, dtype="int32"),
                    "E": pd.Categorical(["test", "train", "test", "train"]),
                    "F": "foo",
                }
            )
            df2
    Out [5]: 
                A          B    C  D      E    F
            0  1.0 2013-01-02  1.0  3   test  foo
            1  1.0 2013-01-02  1.0  3  train  foo
            2  1.0 2013-01-02  1.0  3   test  foo
            3  1.0 2013-01-02  1.0  3  train  foo

### The columns of the resulting DataFrame have different dtypes:

    In [6]: df2.dtypes
    Out[6]: 
            A           float64
            B    datetime64[ns]
            C           float32
            D             int32
            E          category
            F            object
            dtype: object

### If you’re using IPython, tab completion for column names (as well as public attributes) is automatically enabled. Here’s a subset of the attributes that will be completed:

    In [7]: df2.<TAB>  # noqa: E225, E999
            df2.A                  df2.bool
            df2.abs                df2.boxplot
            df2.add                df2.C
            df2.add_prefix         df2.clip
            df2.add_suffix         df2.columns
            df2.align              df2.copy
            df2.all                df2.count
            df2.any                df2.combine
            df2.append             df2.D
            df2.apply              df2.describe
            df2.applymap           df2.diff
            df2.B                  df2.duplicated

### As you can see, the columns A, B, C, and D are automatically tab completed. E and F are there as well; the rest of the attributes have been truncated for brevity.

---

# How do I read and write tabular data?

    In [1]: import pandas as pd


### I want to analyze the Titanic passenger data, available as a CSV file.

    In [2]: titanic = pd.read_csv("data/titanic.csv")

### pandas provides the read_csv() function to read data stored as a csv file into a pandas DataFrame. pandas supports many different file formats or data sources out of the box (csv, excel, sql, json, parquet, …), each of them with the prefix read_*.

### Make sure to always have a check on the data after reading in the data. When displaying a DataFrame, the first and last 5 rows will be shown by default:

    In [3]: titanic
    Out[3]: 
                PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
            0              1         0       3  ...   7.2500   NaN         S
            1              2         1       1  ...  71.2833   C85         C
            2              3         1       3  ...   7.9250   NaN         S
            3              4         1       1  ...  53.1000  C123         S
            4              5         0       3  ...   8.0500   NaN         S
            ..           ...       ...     ...  ...      ...   ...       ...
            886          887         0       2  ...  13.0000   NaN         S
            887          888         1       1  ...  30.0000   B42         S
            888          889         0       3  ...  23.4500   NaN         S
            889          890         1       1  ...  30.0000  C148         C
            890          891         0       3  ...   7.7500   NaN         Q

            [891 rows x 12 columns]

### I want to see the first 8 rows of a pandas DataFrame.

    In [4]: titanic.head(8)
    Out[4]: 
            PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
            0            1         0       3  ...   7.2500   NaN         S
            1            2         1       1  ...  71.2833   C85         C
            2            3         1       3  ...   7.9250   NaN         S
            3            4         1       1  ...  53.1000  C123         S
            4            5         0       3  ...   8.0500   NaN         S
            5            6         0       3  ...   8.4583   NaN         Q
            6            7         0       1  ...  51.8625   E46         S
            7            8         0       3  ...  21.0750   NaN         S

            [8 rows x 12 columns]

### I’m interested in a technical summary of a DataFrame

    In [5]: titanic.info()
            <class 'pandas.core.frame.DataFrame'>
            RangeIndex: 891 entries, 0 to 890
            Data columns (total 12 columns):
            #   Column       Non-Null Count  Dtype  
            ---  ------       --------------  -----  
            0   PassengerId  891 non-null    int64  
            1   Survived     891 non-null    int64  
            2   Pclass       891 non-null    int64  
            3   Name         891 non-null    object 
            4   Sex          891 non-null    object 
            5   Age          714 non-null    float64
            6   SibSp        891 non-null    int64  
            7   Parch        891 non-null    int64  
            8   Ticket       891 non-null    object 
            9   Fare         891 non-null    float64
            10  Cabin        204 non-null    object 
            11  Embarked     889 non-null    object 
            dtypes: float64(2), int64(5), object(5)
            memory usage: 83.7+ KB

### The method info() provides technical information about a DataFrame, so let’s explain the output in more detail:

* #### It is indeed a DataFrame.

* #### There are 891 entries, i.e. 891 rows.

* #### Each row has a row label (aka the index) with values ranging from 0 to 890.

* #### The table has 12 columns. Most columns have a value for each of the rows (all 891 values are non-null). Some columns do have missing values and less than 891 non-null values.

* #### The columns Name, Sex, Cabin and Embarked consists of textual data (strings, aka object). The other columns are numerical data with some of them whole numbers (aka integer) and others are real numbers (aka float).

* #### The kind of data (characters, integers,…) in the different columns are summarized by listing the dtypes.

* #### The approximate amount of RAM used to hold the DataFrame is provided as well.
