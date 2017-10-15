# Fishing with Pearls: The Value of Lending Relationships with Prestigious Companies

This repository replicates the results of Muermann, Rauter & Scheuch (2017) and consists of the following two parts:

1. The sample construction implemented in R. The code cleans raw data from various sources and constructs the loan-level, deal-level and bank-level samples used in the empirical analysis.
2. The empirical analysis implemented in Stata. The code reads the pre-cleaned samples and implements all tests described in the paper. The results are exported to latex tables.

Note that variable labels in the code might differ from the labels actually used in the paper.

## Sample Construction

The sample construction is implemented in the open source statistical computing language [R](https://www.r-project.org/). To construct the samples used in the empirical analysis, you need the following CSV files in the `sample_construction/raw` folder.

* Dealscan
	- `dealscan_facility.csv`: Facility-level information from WRDS.
	- `dealscan_package.csv`: Package-level information from WRDS.
	- `dealscan_currfacpricing.csv`: Current facility pricing schedule from WRDS.
	- `dealscan_lendershares.csv`: Lender information from WRDS.
	- `dealscan_financialcovenant.csv`: Information about financial covenants from WRDS (can only be accessed via [direct connection to the WRDS cloud](https://github.com/ckscheuch/rWRDS)).
	- `dealscan_performancepricing.csv`: Performance pricing schedule from WRDS (can only be accessed via [direct connection to the WRDS cloud](https://github.com/ckscheuch/rWRDS)).
	- `dealscan_borrower_link.csv`: [Michael Robert's](http://finance.wharton.upenn.edu/~mrrobert/styled-9/styled-12/index.html) borrower linking table available on his homepage or via WRDS.
	- `dealscan_lender_link.csv`: [Michael Schwert's](https://sites.google.com/site/mwschwert/) lender linking table available on his homepage in XLSX format.
	- `dealscan_tcb.csv`: The total cost of borrowing measure developed by Tobias Berg, Anthony Saunders and Sascha Steffen. Available on [Tobias Berg's](http://www.tobias-berg.com/) homepage in DTA format.
* Compustat North America
	- `comp_firms_funda_annual.csv`: Annual firm fundamentals.
	- `comp_bank_funda_annual.csv`: Annual bank fundamentals.
	- `compm_adsprate.csv`: S&P ratings.
* CRSP
	- `crsp_banks.csv`: End of fiscal-year stock prices for Compustat bank fundamentals need to be retrieved from CRSP. The file `prep_compustat.R` therefore exports a list of bank CUSIPs (`bank_cusips.txt`) which can be used to extract the relevant data from WRDS. Note that the whole CRSP sample is large.
* Markit
	- `cds_raw.csv`: Daily CDS spreads (incl. ticker, date, 5-year spread, 10-year spread and recovery). Note that the full sample has more than 15 GB.
* Fortune's Most Admired Companies Survey
	- `prestige.csv`: Manually-collected data on firm-level prestige. The data will be available online at a later stage.

To construct the samples, first run `prep_dealscan.R`, then all other preparation files (order does not matter) and lastly `prep_samples.R`. Then transfer the output from `sample_construction/samples` to `empirical_analysis/samples`.
	
## Empirical Analysis

The empirical analysis is implemented in the statistical software [Stata](https://www.stata.com/).

Under construction...
