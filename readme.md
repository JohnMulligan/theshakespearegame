# The Shakespeare Game

## Introduction

This is a recommendation system based on the citational practices of published authors in the JSTOR database, specifically with regards to identifiable Shakespeare quotations.

[In this presentation](http://www.johncmulligan.net/blog/2019/10/14/2019-rice-data-science-conference/) I explain how the dataset was constructed.

[Critical Inquiry published my article](https://www.journals.uchicago.edu/doi/10.1086/715982) on the implications of the project for disciplinary knowledge production in the context of big data. (and then they published a brilliant special issue the next quarter on the theme of [surplus data](https://www.journals.uchicago.edu/doi/abs/10.1086/717320))

The only way to understand this form of big humanities data is... to read some Shakespeare :)

## Background

JSTOR ran a fuzzy ngram search of the Folger digital Shakespeare texts (with only a few mistakes regarding indexing line numbers in the prologues, choruses, and epilogues, corrected here) against their own OCR'd corpus, in order to determine who, when and where cited what lines from the Shakespearean _dramatic_ corpus.

Having scraped that lines-to-articles database...

* workflows were run to connect lines to other lines, and then to cluster these, in order to determine which passages had been related to other passages
* to bring out more variety, links _within_ the same play were excluded
* a flask front-end was written to display these passage-to-passage links

This allowed the infrastructure of the published, scholarly understanding of Shakespeare to be brought out as a large but notably finite hypertext.

## Application

When the Critical Inquiry article was published, the library allowed me to publish the SQL dump and codebase, which I built to run in AWS.

However, the Elastic Beanstalk + MySQL database was expensive *and* had performance issues; so in August 2022 I refactored this to run on SQLite, the way the original app had run. It is now much more reliable and portable, with one notable exception: this will not run without the SQLite db, which is too large to post on Github.

### How to obtain the SQLite database:

* You can download the zipped sqlite db from my website at this address
* Or you can email me for a copy: john.connor.mulligan@gmail.com

### How to install & run

```
git clone https://github.com/johnMulligan/theshakespearegame

cd theshakespearegame

python3 -m venv venv

source venv/bin/activate

pip install -r requirements.txt

curl -o ariel.tgz "http://johncmulligan.net/shakespeare/ariel.tgz"

tar -xzvf ariel.tgz

python application.py
```