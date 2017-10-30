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

I first examine the countries with the highest rank of articles to their populations.  Firstly, I note that these are all countries with relatively small populations, meaning that the denominator of the calculation is small.  Of the countries listed, we see one of two characteristics: 1) the country lists English as a primary language, or 2) the country is a relatively affluent country in Western Europe.  It is understandable that countries were English is spoken as a primary language would feature good coverage in English language Wikipedia.  Additionally, English is widely spoken as a second language throughout Western Europe, and therefore good coverage in English language Wikipedia is not terribly surprising.

Next, I examine the countries with the lowest rank of articles to their populations, and there is not a great deal of surpise there either.  Countries with very large populations are represented, and these include major names in Asia and the Indian subcontinent.  In particular, the countries with the largest worldwide populations (the P.R.C, and India) are last and second to last.  English is not a primary language in either.  Other very populous, non-English speaking countries listed are Indonesia, Bangladesh and Vietnam.  Remaining names in the list are primarily in Africa, namely Ethiopia, Zambia, and the Congo.  This may indicate little interest in these countries in the English-speaking world.

In terms of percentage of high-quality articles, we see some surprises on the list.  These are, namely, the Central African Republic, Vanuatu, Guinea-Bissau and Zambia, all of which are in Africa.  I theorize that these countries have smaller populations, and at the same time have one (or a community of) English-speaking author(s) who have interest in the politicians of these countries and have written articles in English language Wikipedia.  At the same time, reasonably populous Saudi Arabia, Vietnam and Singapore are represented, and I wonder if there is a government effort there to appeal to, or inform English speaking audiences.  I theorize either that, or a dedicated English speaking editor corps in these countries.  Two other names in the list are not so surprising: the United States, and Ireland.  I wonder, however, where the more populous commonwealth countries exist in this hierarchy, namely the U.K., Canada, Australia and New Zealand.  Perhaps if the graph included the next ten highest ranking countries, those countries would land there.

The graph showing countries with the lowest percentage of high-quality articles isn't particularly helpful, as the list is alphabetized and probably shows only a subset of countries were the percentage is exactly zero.  Of those listed, we see a smattering of smaller countries.  Of note, we see listed here Andorra, which was also featured on the list of ten countries with the highest percentage of articles compared to population.  It is as if one or more authors sought to create stubs for politicians in Andorra, and then did not take the time to properly fill in the stubs.
