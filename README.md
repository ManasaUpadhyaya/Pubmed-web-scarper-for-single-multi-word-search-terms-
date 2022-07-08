Description : This script is a PubMed scarper designed to take search word/search words and the number of searches from the user and return a .csv file with the results.

Requirememnts:
Libraries:
Pandas 
Beautiful soup 
requests 
Urllib
ssl
Json
calendar

Input - Search keyword/two keywords, number of search results

Output - .csv file is generated with the name as follows : keyword_number of results. 
The results are sorted based on relevant search hits,starting from the highest to the lowest.
The columns in the final .csv output file are:
['authors', 'ArticleTitle', 'journal_title', 'volume', 'date', 'pubmed', 'doi_pii_str', 'abstract']

Common errors to avoid : Do not enter a space before the keyword input, or the number of searches. (the input doesn't get recognised)

Basic functioning of the code:

The code first retrieves the IDs of the required searched term and number of results. This first snippet of code 
uses the eutils(esearch in specific) offered by Entrez. The IDs are retrieved in JSON format and stored in a list.
The strip brackets strips the brackets from the article title, which is later used in the script.
Once the IDs are retreieved, efetch(again from eutils) is used to extract the required page in xml. The xml data is scraped using Beautiful soup and is fed to the get_bibiliography function.
Get_bibliography creates an empty variable for each required column, i.e., author, article title, jounal, volume, abstract, etc. The information is then sorted and edited to remove extra characters and split it into required columns. 
The get_bibliography returns the articles object which is then converted to a list and further to a pandas dataframe. This is sorted into various columns on a final .csv file. 
The script has an additional functinality(added if with an if/else block) to include double search words.
