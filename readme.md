# Prosper Loan Data Exploration
## by Arshi Saleh


## Dataset

> The dataset which I will be exploring is the Prosper Loan dataset. The dataset has 113937 rows and 81 columns. I will not be using 
all the columns for exploration. Prosper is an online platform for peer-to-peer lending. It connects borrowers to investors directly. 

> We will be looking into data in the following columns:
'ListingKey','Term','LoanStatus','EstimatedReturn','LenderYield','Occupation','EmploymentStatus','EmploymentStatusDuration',
'ListingCreationDate','CreditScore' (we have created this column by calculating the average of CreditScoreRangeUpper and CreditScoreRangeLower,'AmountDelinquent','DelinquenciesLast7Years','InquiriesLast6Months','BankcardUtilization',
'DebtToIncomeRatio','IncomeRange','IncomeVerifiable','StatedMonthlyIncome','OnTimeProsperPayments','PublicRecordsLast10Years','PublicRecordsLast12Months','ProsperPrincipalBorrowed','ProsperPrincipalOutstanding',
'TotalCreditLinespast7years','FirstRecordedCreditLine','TotalProsperLoans','ProsperPaymentsLessThanOneMonthLate',
'ProsperPaymentsOneMonthPlusLate'.
This dataset is of interest to both borrowers and investors but my exploration will be focused on which factors will help the investors get better returns and hold a diverse portfolio with minimum risk.

## Summary of Findings

> I started my exploration process by analysing the Occupation column. As this column has an Outlier Other which is not explanatory we plotted the chart without the outlier to identify the top 30 most common Occupations of the borrowers.
> The EmploymentStatus plot had three catgories Employed, Full-time and Part-time which I have merged into one since Employed did not specify whether it was full-time or part-time. We can now see that more than 80% of the borrowers are employed.
> Debt Consolidation is the most common Listing Category for the borrowers followed by home improvement, business and auto. A little less than 25% of the listings fall in the NotAvailable and Other category which are non-specific.
> Around 47% of loans have status completed followed by about 34% of current loans. Loan status Charged off is about 10%, followed by about 4-5% of Defaulted and a small % of loans which are past due. This gives a confidence that there is a high chance of the loan being paid.
> The 36 month term has the maximum count. This means that more number of borrowers borrow for 36 months. At a later stage I would like to explore if there is a relationship between term and risk.
> The count for InquiriesLast6Months reflects the number of inquiries/credit checks in the past 6 months at the time the credit profile was pulled. A higher count might reflect greater risk of default. 
> The count for ProsperCreditRating is maximum for 'C', followed by 'B' and 'D'. Higher ratings mean lower risk but also lower returns. Investors like to maintain a mixed portfolio so that they can get higher returns, hence this will be an important feature to explore further.
> From the IncomeRange plot we can see that most of the borrowers have an income above 25,000(dollars).
> From the IncomeVerifiable plot we can see that most of the Income stated has been verified.
> In the PublicRecordsLast10Years we have limited the plot to a value of 10 because we don't want to invest with people having higher number of Public Records.
> In the PublicRecordsLast12Months we have an outlier at 20.0. Again we would like to avoid people with public records as chances of default increases. It would be interesting to see if people having higher number of PublicRecordsLast10Years have records in the last 12 months.
> The dataset has two columns for CreditScore, CreditScoreRangeLower and CreditScoreRangeUpper. To make evaluation easier I have created a new column CreditScore(average of the upper and lower range values). The graph has been plotted in 2 subplots , with and without limits. A CreditScore closer to value 0 is an outlier. We can see that most of the CreditScore values lie in the range between 500-900 with peaks around 700.
> Plotting the Original Loan amount in bins we can observe that the frequency of borrowers who have originally borrowed an amount less than 5000 is more. We have spikes around 10,000 and 15,000. The graph shows that there are a few borrowers who have borrowed more than 15,000 but most of the borrowers have borrowed a smaller amount. The range of loans is observed to be within 1000-35000 dollars.
> In the DebtToIncomeRatio plot we can observe that most of the borrowers have a ratio less than 1.0 with most values between 0.1-0.4. This increases investor confidence as a high count of high values of DebtToIncomeRatio makes investing in Prosper very high risk.
> The counts for ProsperPaymentsLessThanOneMonthLate and ProsperPaymentsOneMonthPlusLate having value zero is very high. To get a better idea we remove the value zero and plot the chart again. The number of two time defaulters for payments delayed for less than a month is almost around 700, three time defaulters is more than 250. The number of two time defaulters for payments delayed for more than a month is around 70 and for three time defaulters is around 50. So while the count of non-defaulter is quiet high we also need to explore defaulter information in more detail.
> Most of the loans have an Estimated Return between the range 0.0-0.2 with peaks between 0.05 to 0.15. We can also see negative returns which indicate a chance of loss. 
> The count of borrowers having zero amountdelinquent is quiet high, on closer observation we find that lower values of AmountDelinquent have higher count though there are outliers where the amountdelinquent is quiet high.
> We can observe that number of borrowers who have been delinquent once in last 7 years is maximum with a count of more than 3800. We can also observe that borrowers have been delinquent upto 99 times in last 7 years(outlier). It would be interesting to find the common features for borrowers who have more number of delinquencies.
> Lender Yield is the interest rate less the servicing fee. We can see that the yield has a peak at 0.3 which is 30%, with most of the values between 0.05 and 0.35.
> To have a better understanding of the borrowers that have successfully closed their loans I have explored the CreditScore, ProsperCreditRating, IncomeRange and LoanOriginalAmount for borrowers who have already closed their loans and we can see that creditscore peaks at around 700, more number of borrowers have Prosper Credit Ratings of D and above, income range between mostly lies above 25,000 dollars and loan original amount is less than 5000 in most cases.
> To have a better understanding of the borrowers that have successfully closed their loans I have explored the CreditScore, ProsperCreditRating, IncomeRange and LoanOriginalAmount for borrowers who have already closed their loans and we can see that creditscore peaks at around 700, more number of borrowers have Prosper Credit Ratings of D and above, income range between mostly lies above 25,000 dollars and loan original amount is less than 5000 in most cases.
> We have plotted a heatmap to investigate the relationship between ListingCategory and LoanStatus and our observations were:
- 1.The listing category Debt Consolidation has the maximum number of current and completed loans and second largest number of charged off loans, the first being a category which is no longer available.
- 2.The category which is no longer available has the worst performance in terms of defaulted and chargedoff loans.
- 3.DebtConsolidation comes a close second in defaulted and charged of loans, but as we can see from the current and completed loans the volume of this category is very high and hence the % of defaulted and charged off loans would be much lower values.
- 4.Business , Other and Personal loans are categories which have large number off chargedoff and defaults.
> We can observe that DebtConsolidation has peaks around 0.15 and 0.3, but most of the yield values range between 0.1 and 0.2. Medical/Dental, Other, Auto, Business, Home Improvement, Household Expense have peaks at 0.3. This shows a probability of getting interest at around 30%. Personal Loan has a peak around 0.35. For Debt Consolidation the range for yield is from 0.04 to 3.5
> Debt Consolidation has Credit Scores in the range 600-800 which are good scores and indicate lower risk factor. Business. Home Improvement , Other all have peaks at the range 600-800. Boats have a credit score range of 700-800 which is quiet high, indicating that it is a luxury item and people taking loans to buy it are financially more stable.
>  We have observed that the average Delinquencies in Last 7 Years is maximum for EmploymentStatus 'not available' followed by retired and other. Self-employed and employed borrowers have relatively lower delinquencies and short error bars. Surprisingly not employed borrowers have the lowest mean delinquencies but the error bar is second longest with retired borrowers having the longest error bar. The errorbars represent uncertainity in mean based on variance and sample size.
> Borrowers who are not employed have the highest debt to income ratio followed by 1-24,999 dollar income range. 75,000-99,999 and 50,000-74,999 dollars Income range borrowers have low Average Debt-to-Income ratio and smaller average ProsperPaymentsOneMonthPlusLate value. We can also observe that the error bars are longer for not employed in both plots.
> We can see that the Loan Term of 36 months has the most frequency followed by 60 months. From the plot we can see that 12 months term is only available for completed loans hence there is a high probability that 12 month loans are no longer available.
> When we plot ProsperCreditRatings v/s EstimatedReturn and v/s LenderYield as subplots we observe that Estimated Return has better returns for ProsperRatings B, C and D. HR has a higher peak than B, and C but it also has a huge number of outliers with low and negative results.
LenderYield gives us a different picture where HR has the best returns followed by E and D. Since LenderYield does not consider the estimated loss the risk factor of the HR category is not clearly visible in this plot.
> There is a decrease in the average Delinquencies in Last 7 Years with increase in loan amount but the for loan amounts above 30k the standard error of the mean increases.
> The estimated return is higher for smaller values of LoanOriginalAmount but the standard error of mean is more for amounts greater than 30,000 dollars.
> Borrowers in the Construction field have lower creditscores and maximum outliers in the lower range. Attorney and Professors have maximum scores above 700. Computer Programmer, Executive , Analyst, Nurse, Engineer Mechanical and Electrical being other occupations where borrowers have good creditscores.
> Borrowers having ProsperCreditRatings HR and E have the highest Amount Delinquent followed by D. Borrowers having rating AA have the least amount of borrowers having high delinquencies. The surprise factor is the borrowers with rating C have lower numbers in high delinquent amount as compared to A and B.

## Key Insights for Presentation

> I have chosen a few of the plots of the key features to share in the presentation. I have added titles, labels and kept the data to ink ratio high in the explanatory charts.
> Based on the exploratory charts and the aim of our analysis I have shared the plots LoanStatus Distribution, Distribution of CreditScore, ProsperCreditRating, IncomeRange and LoanOriginal Amount for LoanStatus='Completed', IncomeRange v/s Average Debt To Income Ratio & Average ProsperPaymentsOneMonthPlusLate, LoanOriginalAmount v/s mean of Estimated Return, LoanOriginalAmount v/s AmountDelinquent v/s DelinquenciesLast7Years, ListingCategory v/s CreditScore, LoanStatus v/s Occupation v/s Estimated Return and Explore Relation between IncomeRange, ProsperCreditRating ProsperPaymentsOneMonthPlusLate, ProsperPaymentsLessThanOneMonthLateLoanOriginalAmount and InquiriesLast6Months in the Presentation
> They key findings are that borrowers having higher creditscores (600-800) , ProsperCreditRatings (AA, C, D), income range above 25,000 dollars (though above 50,000 dollars is lower risk), DebtToIncomeRatio less than 0.4, LoanOrignalAmount between 20,000-28,000 (OriginalLoanAmount less than 10,000 dollars is very high risk) have good EstimatedReturn,lesser delinquencies and lower delinquent amount. ListingCategory DebtConsolidation has lower range of DebtToIncomeRatio which makes it lucrative. Attorney and Professors have best Credit Scores above 700. Computer Programmer, Executive , Analyst, Nurse, Engineer Mechanical and Electrical being other occupations where borrowers have good creditScores.


## Prosper Investor Glossary
> This glossary will explain the financial terminology used in the dataset:
-ListingKey:
Unique key for each listing, same value as the 'key' used in the listing object in the API.
-Term:
The length of the loan expressed in months. #min is 12 months, max is 60 months
-LoanStatus:
The current status of the loan: Cancelled,  Chargedoff, Completed, Current, Defaulted, FinalPaymentInProgress, PastDue. The PastDue status will be accompanied by a delinquency bucket.
-BorrowerAPR:
The Borrower's Annual Percentage Rate (APR) for the loan. #conventional measurement of loan costs, this includes all charges including interest.
-LenderYield:
The Lender yield on the loan. Lender yield is equal to the interest rate on the loan less the servicing fee.
#1. Yield is the annual net profit that an investor earns on an investment.
#2. The interest rate is the percentage charged by a lender for a loan.
#3. The yield on new investments in debt of any kind reflects interest rates at the time they are issued.
-Occupation:
The Occupation selected by the Borrower at the time they created the listing.
-EmploymentStatus:
The employment status of the borrower at the time they posted the listing.
-EmploymentStatusDuration:
The length in months of the employment status at the time the listing was created.
-CreditGrade:
The Credit rating that was assigned at the time the listing went live. Applicable for listings pre-2009 period and will only be populated for those listings.
-ProsperRating (Alpha):
The Prosper Rating assigned at the time the listing was created between AA - HR.  Applicable for loans originated after July 2009.
-ListingCreationDate:
The date the listing was created.
-CreditScoreRangeLower:
The lower value representing the range of the borrower's credit score as provided by a consumer credit rating agency.
-CreditScoreRangeUpper :
The upper value representing the range of the borrower's credit score as provided by a consumer credit rating agency.
-AmountDelinquent:
Dollars delinquent at the time the credit profile was pulled.
-TradesNeverDelinquent	(percentage):
Number of trades that have never been delinquent at the time the credit profile was pulled.
-DelinquenciesLast7Years:
Number of delinquencies in the past 7 years at the time the credit profile was pulled.
-InquiriesLast6Months:
Number of inquiries in the past six months at the time the credit profile was pulled.
The number of times a bank or other business has requested the borrower’s credit profile from a consumer credit rating agency, excluding certain duplicate inquiries, as defined by the credit bureau.
-BankcardUtilization:
The percentage of available revolving credit that is utilized at the time the credit profile was pulled. The sum of the balances owed on open bankcards divided by the sum of the cards’ credit limits.
-DebtToIncomeRatio:
The debt to income ratio of the borrower at the time the credit profile was pulled. This value is Null if the debt to income ratio is not available. This value is capped at 10.01 (any debt to income ratio larger than 1000% will be returned as 1001%).
-IncomeRange:
The income range of the borrower at the time the listing was created.
-IncomeVerifiable:
The borrower indicated they have the required documentation to support their income.
-StatedMonthlyIncome:
The monthly income the borrower stated at the time the listing was created.
-OnTimeProsperPayments:
Number of on time payments the borrower had made on Prosper loans at the time they created this listing. This value will be null if the borrower has no prior loans.
-PublicRecordsLast10Years:
Number of public records in the past 10 years at the time the credit profile was pulled.
-PublicRecordsLast12Months:
Number of public records in the past 12 months at the time the credit profile was pulled.
The number of negative public records reported by the credit bureau for the last 24 months or up to 10 years, as applicable. Public records may include bankruptcies and liens.
-TotalProsperLoans:
Number of Prosper loans the borrower at the time they created this listing. This value will be null if the borrower had no prior loans.
-ProsperPrincipalBorrowed:
Total principal borrowed on Prosper loans at the time the listing was created. This value will be null if the borrower had no prior loans.
-ProsperPrincipalOutstanding(active loan):
Principal outstanding on Prosper loans at the time the listing was created. This value will be null if the borrower had no prior loans.
-TotalCreditLinespast7years:
Number of credit lines in the past seven years at the time the credit profile was pulled.
-FirstRecordedCreditLine:
The date the first credit line was opened.
-TotalProsperLoans:
Number of Prosper loans the borrower at the time they created this listing. This value will be null if the borrower had no prior loans. 
-ProsperPaymentsLessThanOneMonthLate:
Number of payments the borrower made on Prosper loans that were less than one month late at the time they created this listing. This value will be null if the borrower had no prior loans. 
-ProsperPaymentsOneMonthPlusLate:
Number of payments the borrower made on Prosper loans that were greater than one month late at the time they created this listing. This value will be null if the borrower had no prior loans.
