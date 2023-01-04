# Fake news Analysis and Classification

## Description
We consider the datasets contained within the [Datasets](./Datasets) repository. All the datasets include news from the US presidential periods in 2016 and 2020.
The main goal of this analysis is to develop a model for detecting and classifying news in online articles as fake or real, which will be performed in all three datasets.
For each dataset we will also identify the most common words used that are used in each category.

## Files
Here are the important files (the remaining files should be ignored):

* [Datasets.zip](./Datasets.zip): This .zip foleder contain all the datasets.Included in this folder are:
  * [nela-gt-2020](./Datasets/nela-gt-2020):The dataset can be found in [NELA-GT-2020](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/CHMUYZ)
  * [Random_Political](./Datasets/Random_Political):The dataset can be found in [Random_Political](https://github.com/BenjaminDHorne/fakenewsdata1)
  * [buzzfeed-v02-originalLabels.txt](./Datasets/buzzfeed-v02-originalLabels.txt):The dataset can be found in [MisInfoText](https://github.com/sfu-discourse-lab/MisInfoText#readme)
*[Fake_news_classification.ipynb](./Code/Fake_news_classification.ipynb): The jupyter notebook used for this analysis.
* The base configuration files used in the model training.


## Instructions

In order to run [jupyter notebook](./Fake_news_classification.ipynb), you will need to first download the .zip folder containing the [Datasets.zip](./Datasets.zip).
You can use the base configuration files provided in the [Code](./Code) folder or create a new one using the [widget](https://spacy.io/usage/training#quickstart) provided by spacy.

The text classification models are already trained and can be found in the [outputs](./Code/outputs) folder.You can choose when running the code to not retrain the models and see the results by loading the models.

## Datasets

All the datasets can be found [4TU.ResearchData](https://data.4tu.nl/articles/dataset/Repository_of_fake_news_detection_datasets/14151755).
In particular:

### Random_Political
This dataset was collected as part of the research paper "This Just In: Fake News Packs a Lot in Title, Uses Simpler, Repetitive Content in Text Body, More Similar to Satire than Real News" 
and can be found in this [repository](https://github.com/BenjaminDHorne/fakenewsdata1).
According to the authors, the dataset was randomly collected from three types of sources during 2016 
and "each of these stories is a “hard” news story, and not an opinion piece". 
The sources  that are considered reliable were determined through: Business Insider’s “Most Trusted” list 2014.  
The original article is no longer available, but an updated version can be found [here](https://www.businessinsider.com/most-and-least-trusted-news-outlets-in-america-2017-3). 
For the "fake news" data, Zimdars 2016 [list](https://docs.google.com/document/d/10eA5-mCZLSS4MQY5QGb5ewC3VAL6pLkT53V_81ZyitM/preview) was used. 
The dataset also contains a satire folder that won't be used in this analysis. Some examples of sources are:

* Real: Wall Street Journal, The Economist, BBC, NPR, ABC, CBS, USA Today, The Guardian, NBC, The Washington Post.
* Fake: Ending The Fed, True Pundit, abcnews.com.co, DC Gazette, Liberty Writers News, Before it's News, InfoWars, Real News Right Now.

Each data set's ground truth labels are separated into directories (Fake, Real, Satire). 
The body text and title text for each data set are saved in separate plain text files. 
We will use the folders Real and Fake, which each contain 75 title texts, for this analysis. 
The time frame for collecting the article titles is not mentioned. 
The dataset only contains the text of the titles, and there aren't any missing values.

### MisInfoText
This dataset was used in the original story “Hyperpartisan Facebook Pages Are Publishing False And Misleading Information At An Alarming Rate” 
published in October 20th, \autocite{silverman_2016}. This dataset was originally published on GitHub by 
(BuzzFeed News)[https://github.com/BuzzFeedNews/2016-10-facebook-fact-check].It consists of a sample of news articles
posted on Facebook by nine news organizations during the week leading up to the 2016 American election,
from September 19 to 23 and September 26 and 27.
This dataset was used by researchers in the [Discourse Processing Lab](http://www.sfu.ca/discourse-lab/software_and_data/demo.html), 
to scrap the text by using Facebook post URLs and IDs, and create a dataset that contains the full text of each news 
article and a reliable veracity label indicative of its truth content. 
The dataset, which will be used in this analysis, can be found in the repository [MisInfoText](https://github.com/sfu-discourse-lab/MisInfoText#readme). 
It includes a total of 1380 news articles on a focused topic (US election and candidates) and veracity labels come in 
a four-way classification scheme including 1090 mostly true, 170 mixture of true and false, 64 mostly false and 
56 articles containing no factual content.

### NELA GT 2020
The NELA GT 2020 dataset (NELA stands for News Ecosystem Landscape Analysis) is a dataset that contains information 
about news articles and was presented in 
"NELA-GT-2020: A Large Multi-Labelled News Dataset for The Study of Misinformation in News Articles ".The NELA GT 2020 dataset includes information about news articles that were published in 2020, including the article title, author, publication date, and a link to the full article. It contains labelled news sources that  cover  a  broad  set  of  events,  including  the  COVID-19 pandemic and the 2020 U.S. Presidential Election. More precisely, it contains 1,779,127 news articles from 519  sources between January  1st,  2020 and December 31st,  2020.  This data set that does not annotate the veracity of each news story, but rather the truthfulness of the news source from Media Bias/Fact Check (MBFC).It also contains embedded Tweets found in the news articles that won't be used in this analysis.
The dataset contains a file with the source labels based on Media Bias/Fact Check reports that indicate the credibility label for each sources as reliable-class 0, unreliable-class 1, mixed-class 2. They also provide two folders named Newsdata where each data point collected corresponds to an article and contains ID of the article, date of publication, name of the source, article's headline, article's body text, author, date published, timestamp of publication, timestamp of collection and url of the paper. NELA-GT-2020 contains nearly 1.8M news articles from 519 sources collected between January 1st, 2020 and December 31st, 2020.
Because of this huge size, we will only use some sources provided for each class. In particular, in order to create a balance dataset, we will use for:
* Reliable sources: The Atlantic, the Washington Post, the New York Times and Reuters.
* Unreliable sources:  rt, newswars, infowars, the political insider, cs globe, revolution radio, daily mail, the liberty beacon, clashdaily.


## Hardware and Software Used
- Hardware Overview:The analysis was run on a laptop using the CPU
  - Model Name: MacBook Pro16 
  - Processor Name: Quad-Core Intel Core i5 
  - Processor Speed: 2 GHz 
  - Number of Processors: 1 
  - Total Number of Cores: 4 
  - Memory: 16 GB 3733 MHz
- Software: The software programs used in the analysis are:
  - [DataSpell 2022.2.3](https://www.jetbrains.com/dataspell/)
  - [Jupyterlab : 3.5.2](https://jupyter.org/)
  - [Python version 3.10](https://www.python.org/downloads/release/python-3100/)
  - Libraries:
    - os
    - [spaCy](https://spacy.io/)
    - [re](https://pypi.org/project/regex/)
    - [matplotlib](https://pypi.org/project/matplotlib/)
    - [nltk](https://www.nltk.org/)
    - [numpy](https://numpy.org/)
    - [pandas](https://pandas.pydata.org/)
    - [seaborn](https://seaborn.pydata.org/) 
    - [sklearn](https://scikit-learn.org/stable/)
    - [tqdm](https://tqdm.github.io/)
    - [wordcloud](https://amueller.github.io/word_cloud/)

- Runtime: Indicate the runtime of your analyses, including any relevant parameters such as batch size or number of epochs.


## Usage
As we mentioned above, from the Random Political Dataset, we will only use the title text of the fake and real articles.
The title of a news article often provides a summary or overview of the content of the article,
and can convey the overall sentiment or emotion of the article. 
For example, a news article with a positive or optimistic title might indicate that the article is more likely to 
present a positive view of a particular subject, while a news article with a negative or pessimistic title might 
indicate that the article is more likely to present a negative view. We can use the results to understand the general 
sentiment and gain insights into the emotions and opinions expressed in news articles. 
This can be useful for a variety of purposes, including understanding public sentiment, analysing the tone of media 
coverage, and identifying potential biases or agendas in news reporting. As a result, we will perform sentiment 
analysis in order to extract the polarity and objectivity of the titles.

Moving on to the MisInfoText dataset, we'll start with exploratory data analysis, such as word count, 
finding which source is publishing the majority of fake news, and the most prevalent words by category and source.
Similarly to the preceding, we will do sentiment analysis on the article's text.

Finally, we analyse the NELA-GT-2020 dataset. This dataset, in comparison to the above, is quite large, 
and each article contains a lot of text. As a result, we will extract the summary of each article and use it to 
perform text classification. Moreover, we will also cluster the articles by topic to help identify the topics 
that are conveyed in this dataset.

## References
Gruppi, M., Horne, B. D. & Adalı, S. (2021) NELA-GT-2020: A Large Multi-Labelled News Dataset for
The Study of Misinformation in News Articles. Available from: DOI:10.48550/ARXIV.2003.08444

Taboada, M. & Asr, F. T. (2019) Big Data and Quality Data for Fake News and Misinformation Detection. Big Data and Society. 6 (1). Available from: DOI:10.1177/2053951719843310.
17

## License

MIT. See the LICENSE file for the copyright notice.
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/your-username/project-title/blob/master/LICENSE)



