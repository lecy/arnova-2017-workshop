---
layout: page
title: Open Data
permalink: /OpenData/
---

<br>
<br>

<div class="icon-block">
   <h1 class="center black-text" style="font-size:160px;"><i class="large material-icons">blur_on</i></h1>
   <h1 class="center orange-text">Open Nonprofit Data</h1>
</div>


<br>
<br>
<br>
<br>








------------------------------------------  

### NCCS Data

The Urban Institute's National Center for Charitable Statistics has been a backbone of nonprofit scholarship for two decades, mainly by investing a tremendous amount of time and energy into making IRS 990 data clean and accessible. 

The data has historically been behind a paywall, but starting this past year they have opened up their archives and are now sharing all of their files for free. You can find this data at the [NCCS Data Hub](http://nccs-data.urban.org/index.php).

<br>
<br>

------------------------------------------  

### E-Filer Data

In 2016 the IRS began releasing the 990 e-file tax data for nonprofits as XML files posted on an Amazon Web Server. It is possible to download these files, but the current format makes them challenging to use for research purposes. There are 95 different versions of the data that span three distinct forms (the 990, 990-EZ, and 990-PF) as well as a dozen Schedules. The main documentation that describes the data is contained in xsd schema files, not traditional data dictionaries, which makes them challenging to use.

In response to these issues, a group of academics and industry actors such as Aspen Institute, Charity Navigator, Guidestar, Urban Instite, the Chronicle of Philanthropy, Pro-Publica and others begam collaborating on how to be process the e-filer data in order to make it accessible and well-documented. The primary focus of this collaboration so far has been on creating a "Master Concordance File" which allows programmers to easily translate XML files into flat tables that can be used for research, and provide documentation on the fields. 

Whereas the NCCS 990 data files tradiitionally highlight a couple of hundred financial variables, the e-filer data allows us to access all 4,000 fields from the 990 Forms and Schedules. Approximately 60 percent of all nonprofits currently e-file, including the majority of large organizations, meaning the bulk of revenues and assets in the sector are accounted for. This data provides an opportunity to leverage new and interesting portions of the 990s.

The plan is to process all of the e-file data and make it freely available as CSV files. You can follow progress here:

[Data Dictionary](https://nonprofit-open-data-collective.github.io/irs-efile-master-concordance-file/data_dictionary.html)

[Master Concordance File](https://nonprofit-open-data-collective.github.io/irs-efile-master-concordance-file/)

<br>
<br>

------------------------------------------  

### Miscilaneous IRS Datasets

The IRS has released a number of interesting datasets on nonprofit organizations. They are not always easy to find, in convenient formats to use, or especially well-documented. Examples include:

* A database of all organizations that have lost their nonprofit status
* A spreadsheet with data from the new 1023-EZ forms
* 990-N postcard filers

We have made efforts to catalog these sources and post them to the [Nonprofit Open Data Collective site](https://github.com/Nonprofit-Open-Data-Collective). Each dataset typically contains code that will help you extract data from obscure formats like ASCII files, and export it to reasonable formats like CSV or Stata. This exaple here is from the revocation database:

```r
# download and unzip
file.url <- "https://apps.irs.gov/pub/epostcard/data-download-revocation.zip"
download.file( url=file.url, "revoked.zip" )
unzip( "revoked.zip" )
file.remove( "revoked.zip" )

dat.revoked <- read.delim( file="data-download-revocation.txt", 
            header = FALSE, 
            sep = "|", 
            quote = "",
            dec = ".", 
            fill = TRUE,  
            colClasses="character"
          )

# add header information - variable names
var.names <- c("EIN", "Legal.Name", "Doing.Business.As.Name", "Organization.Address", 
   "City", "State", "ZIP.Code", "Country", "Exemption.Type", "Revocation.Date", 
   "Revocation.Posting.Date", "Exemption.Reinstatement.Date")
names( dat.revoked ) <- var.names

# change Tax.Year from YYYY-MM to YYYY
dat.revoked$Year <- substr( dat.revoked$Revocation.Date, 8, 11 )

```

<br>
<br>

------------------------------------------  

### USA Spending

The federal government mandates that all allocations made through federal agencies are reported back to the US Treasury in a consistent and timely manner. This data is then packaged in the Federal Assistance Awards Data System (FAADS) and the Federal Procurement Data System (FPDS). These databases are available for download on the [USA-Spending.gov](https://www.usaspending.gov/Pages/Default.aspx) website.  

A sizable amount of allocations flow to nonprofits within these datasets, so they have the potential to augment traditional sources data on government funding. It can, however, be challenging to use the data to study nonprofits because (1) the nonprofit codes are not always reliable, and (2) the database does not contain EINs, making it hard to link nonprofit data to their subsector codes and financial information.

The following paper outlines some methods for linking FAADS data to NCCS 990 datasets, and example code is provided:

Lecy, J. & Thornton, J. (2016). “What Big Data Can Tell Us about Government Awards to the Nonprofit Sector: Using the FAADS Dataset.” Nonprofit and Voluntary Sector Quarterly, forthcoming. [ [download](
http://www.lecy.info/s/FAADS-2015-Lecy-Thornton.pdf) ] [ [FAADS to NCCS crosswalk script](https://github.com/lecy/FAADS-NCCS-Crosswalk/blob/master/README.md) ]

<br>

<img src="https://github.com/lecy/arnova-2017-workshop/blob/master/assets/Figure1.png?raw=true" style="width:600px;">


<br>
<br>

------------------------------------------  

### Federal Audit Clearinghouse

Thousands of nonprofits are required to submit a federal audit each year, which are filed in the [Federal Audit Clearinghouse](https://harvester.census.gov/facdissem/SearchA133.aspx). These files are interesting because audits contain financial data that reports operational categories of revenues and expenses in ways that are different from what appears on 990 forms. They can thus provide more detail about financial health than what is currently available.

Marc Joffe has begum collecting all of the nonprofit audits in a [central repository](http://www.govwiki.info/pdfs/Non-Profit/). These will hopefully be discovered by researchers that are looking for alternative types of nonprofit financial data. 




<br>
<br>

------------------------------------------  

### Additional Sources

* New York Times API / Lexus Nexus for longitudinal text studies 
* Twitter API / Twitter statistical sample (contact Urban Institute) 
* Website text 
* Google Trends 
* Canadian tax data 
 
<br>
<br> 
<br>
