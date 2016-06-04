#Scraping 13F Filings

As part of my undergraduate thesis, I learned R and wrote code to catalog 13F filings from the SEC to analyze the similarity between the long equity portfolios of institutional investment funds. In the following sections, I will explain how I scraped the 13F filings, the steps I had to take to clean and smooth the data, and provide some potential future applications of the data.  


##Section 1: Scraping the 13F Filings (get13f2015q4.Rmd)    

You can manually search the [SEC's Edgar Database](https://www.sec.gov/edgar/searchedgar/companysearch.html) by fund name or CIK (the latter of which is best for accuracy and consistency). However, if you want to collect large amounts of data on all of the funds in a number of quarters it is best to scrape the filings.  

The first bit of code you need to run is the "get13f2015q4.Rmd" file. For the purpose of this model, we are going to download all of the positions in 2015 Q4. The commentary in the file is important for understanding what each piece of code is doing and will be helpful to know for why certain subsequent code is structured as it is.  

##Section 2: Cleaning and Smoothing the Data (clean13f2015q4.Rmd)    

One of the biggest issues with scraping the files using the parseXML commands to fill in the holdings information is funds filing incosistently, incomplete;y, or just incorrectly. Each quarter, roughly 80 funds over-report the values of their holdings by a factor of 1,000. Some filings have missing data in certain columns and there are a lot of holdings that have incorrectly labeled CUSIPs, which are how the 13f securities are identified. These and more issues will be addressed in the "clean13f2015q4.Rmd" file.  

##Section 3: Applications (cs2015q4.Rmd and cs2015_q3q4.Rmd)    

In this section, I am going to run through one potential analysis option that I used specifically for my thesis. I used a cosine similarity algorithm to measure portfolio overlap. This section will show you how to calculate cosine similarity and incorporate it into the existing data. You can find the code for this section in the "cs2015q4.Rmd" file. 

Additionally, while the above code calculates the contemporaneous cosine similarity, that is it looks at how overlapped funds are in the same quarter, another valuable slice of the data would be to look at intertemporal cosine similarity, fund overlap across different quarters. This code can be found in the "cs2015_q3q4.Rmd" file. 

##Section 4: Exploring the Data (summary2015q4.Rmd)  

The final section provides an overview of more cuts and slices of the data that you can use to better understand and visualize the data. This section will touch upon useful plotting techniques using the ggplot2 package, as well as some summary statistics and information. This code can be found in the "summary2015q4.Rmd" file. 
