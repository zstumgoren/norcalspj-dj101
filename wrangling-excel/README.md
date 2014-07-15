# Data Wrangling for Journos 101 (Excel)

## Reference Links

* Cal-Access
    * [Candidate data portal][cal-access-campfin]
    * [data documentation][cal-access-datadict]
    * [campaign finance forms][cal-access-campfin-forms] ([Form 460][form-460])
    * [Brown for Gov 2014 Contributions][brown-2014-contribs]
* [Fair Political Practices Commission][fppc]
* [FPPC Contribution Limits][fppc-contrib-limits]
* [My Favorite (Excel) Things](http://extra.twincities.com/car/mj/ExcelClassHandout.pdf), MaryJo Webster

## Overview

### DJ Process Review

The [data journalism process][dj-process-skelton] most often starts with a question. For example:

*How much campaign money has Jerry Brown raised during his current (2014) gubernatorial bid?*

To answer the question, we hunt down [data][brown-2014-contribs], making sure to understand its origin, quirks and context. For example:

* What are the [state limits on campaign contributions][fppc-contrib-limits]?
* What are the filing deadlines?
* Are contributor names standardized?
* What do individual fields mean?
* Does Cal-Access validate data? E.g. requiring employer information for individual contributors?

So you've acquired and vetted some data. Now what?

### Introducing Structured Data

CSV stands for [comma-separated values][wikipedia-csv], but often used generically to refer to any kind of structured data in a tabular -- or table-like -- format.

* CSV flavors
    * standard (comma-delimited, quoted fields)
    * non-standard delimiters (tabs, pipes, semi-colons, etc.)
    * fixed-width

 Other data formats you'll often encounter are:
 
* Excel
* Database dumps
* JSON
* XML

### Importing data

Use *File -> Import*  to open CSVs. This method will normally auto-import files with *.csv* extension, and trigger an Import Wizard for files with *.txt* or other extensions (e.g. *.tsv*).

Import Wizard gives granular control over field delimiters and column types. *This is especially important if Excel's auto-correcting behavior borks you data.* 

For example, in sample.csv, the *zip* code field must be imported as text to prevent leading zeros from being clipped.

We'll be working with an Excel file, which can make things easier. Download the [Brown campaign contributions file now][brown-2014-contribs] and open it using Excel.

### Sorting data

Sorting can give a feel for data:

* boundaries of columns (min/max of dates and numbers)
* missing values
    
Freeze the header row, then perform a few sorts on:

* contributor
* transaction date to get sense of range
* amount

Multi sorts

* Contributor *and* date
* Contributor *and* date (reverse)

### Filtering data

Filtering can let you focus on a set of related records.

Filter by:

* Contributor name to see all contribs
* Transaction date to find all contribs on a certain date

Complex filters:

* Transaction date range
* Amount ranges

### Summary numbers

Using aggregate functions such as "sum".

### Filter/Copy/Paste

To work with filtered data, copy/paste it to new tab. You can sum, apply formulas, etc.

### Pivot tables

Pivot tables let you calculate aggregate numbers across different data attributes. For example, calculate total
contribution amounts by contributor, or by contrib *and* year.

### Final thoughts

We worked with relatively clean data, but in many cases, you'll spend the majority of time cleaning and/or annotating data to support analysis.

For example, what if we wanted to only analyze contributions from individual donors? This problem becomes really tricky if donor names are not standardized (e.g. misspellings, non-standard capitalization, full name in a single field, no additional attributes such as employer/address).

Such data quality issues are common and require careful clean-up before analysis can begin.

Excel or more specialized tools such as [OpenRefine](http://openrefine.org/) or [Dedupe](http://datamade.us/civic-apps/dedupe/) can help with such clean-ups.

[cal-access-campfin]: http://cal-access.sos.ca.gov/Campaign/Candidates/
  
[brown-2014-contribs]: http://cal-access.sos.ca.gov/Campaign/Committees/Detail.aspx?id=1333789&session=2013&view=received

[cal-access-datadict]: http://www.sos.ca.gov/prd/cal-access/

[cal-access-campfin-forms]: http://www.sos.ca.gov/prd/campaign-info/forms-instructions/compend-camp-forms.htm

[form-460]: http://www.sos.ca.gov/prd/forms/460.pdf

[fppc]:http://www.fppc.ca.gov/index.php?id=446

[fppc-contrib-limits]: http://www.fppc.ca.gov/bulletin/007-Dec-2012StateContributionLimitsChart.pdf

[wikipedia-csv]: http://en.wikipedia.org/wiki/Comma-separated_values

[dj-process-skelton]: http://bit.ly/1jINouj "Data Journalism Process, by Chad Skelton"