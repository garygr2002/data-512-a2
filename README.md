# data-512-a2

Assignment #2, DATA-512-A2, Gary Gregg, University of Washington, Autumn 2017

Goal: The goal of this assignment is to explore the concept of 'bias' through data on Wikipedia articles - specifically, articles on political figures from a variety of countries.  For this assignment, I combine a dataset of Wikipedia articles with a dataset of country populations, and use a machine learning service called ORES to estimate the quality of each article.

Data:

'Politicians by Country from the English-language Wikipedia' (https://figshare.com/articles/Untitled_Item/5513449)
License is CC-BY-4.0, provided at https://creativecommons.org/licenses/by/4.0/

'Population Mid-2015' (http://www.prb.org/DataFinder/Topic/Rankings.aspx?ind=14)
Licensing information has not easily been obtainable.  A note at the provided link states that 'All Rights Reserved.'

API documentation is provided at: https://www.mediawiki.org/wiki/ORES

The code produces a CSV formatted file named 'data-512-a2.csv' with the following fields:

country -           The country related to the article
article_name -      The name of the article
revision_id -       The revision ID of the article
article_quality -   The quality of the article, as retrieved from ORES (see above)
population -        The numeric population of the country named in the first field

The code also produces four graphs in '\*.png' format.  These are entitled:

* article_to_population_high_to_low.png: Article count divided by country population, as a percent, 10 highest
* article_to_population_low_to_high.png: Article count divided by country population, as a percent, 10 lowest
* hq_article_to_article_high_to_low.png: High-quality article count divided by article count, as a percent, 10 highest
* hq_article_to_article_low_to_high.png: High-quality article count divided by article count, as a percent, 10 lowest

'High-quality' articles are defined as those that have a rating of 'FA' (Featured Article) or 'GA' (Good Article).  All others ratings are considered to be below premium quality.  Other possible ratings are: 'B' (B-class Article), 'C' (C-class Article), 'Start' (Start-class Article) or 'Stub' (Stub-class Article).  The countries considered by this project have names that match exactly between the two datasets, or can be sight-verified to reference the same country.  In the second category, the project maps the following countries that have different names in the two datasets:

* Wikipedia name - 'East Timorese'; PRB name - 'Timor-Leste'
* Wikipedia name - 'Hondura'; PRB name - 'Honduras',
* Wikipedia name - 'Rhodesian'; PRB name - 'Zimbabwe'
* Wikipedia name - 'Salvadoran'; PRB name - 'El Salvador'
* Wikipedia name - 'Samoan'; PRB name - 'Samoa'
* Wikipedia name - 'São Tomé and Príncipe'; PRB name - 'Sao Tome and Principe'
* Wikipedia name - 'Somaliland'; PRB name - 'Somalia'
* Wikipedia name - 'South African Republic'; PRB name - 'South Africa'
* Wikipedia name - 'South Korean'; PRB name - 'Korea, South'

In all other cases a country is not considered in the findings if it appears in one dataset, but not the other.

The graph showing the countries with the ten lowest percentage of high-quality articles (see 'hq_article_to_article_low_to_high.png', above) has an alphabetized list of ten countries with a percentage of zero.  Algorithmically, this can be caused by a country with no articles at all (which would normally would produce a divide-by-zero error no matter what numerator were provided).  However, if there are no articles in the Wikipedia data for country, then the country simply will not appear.  Therefore the denominator for any high-quality article percentage must be non-zero, and this implies that the count of high-quality articles for a given country *is* zero.  The ten countries that have the lowest percentage, therefore, do have articles, but none of these are considered high-quality.

Concusions:
