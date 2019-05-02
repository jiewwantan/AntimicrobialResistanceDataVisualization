#DAND P6 - Make Effective Data Visualization
#Jiew Wan Tan 
##26th August 2016

##Summary 

Starting from the discovery of antibiotic, bacteria has started to develop resistance towards drugs and chemical. 

Until today many antibiotics developed has subsequently being knocked down as bacteria continues to mutate and multiply. 

It is a serious issues that potentially threathens human existence, unseen by naked eyes and a coherent overview from patient data all over the world is hard to come by.   

This visualization uses isolate test data collected from worldwide hospitals and research institutes, showing how bacteria have came to be more resistant towards their applicable antibiotics over the years in countries where data is available. 



##Design 

###Initial design decision 
The purpose of the design is to communicate the evolving severity (higher resistance) and expansive (to more geogrpahic areas) nature of antibiotic resistance of a number of bacteria. This phenomenon is recognized and being taken seriously within selected circles of medical practice, particularly infectious disease and microbiology fields. However, unlike viral infections such as Ebola and avian flu, it is not an epidemic. It is a slowly advancing threat, so it doesn't generate as much public awareness. This visualization hopes to provide the awareness in a layman understandable manner. 


The challenge of communicating this phenomenon effectively is that the data has multiple-dimensions: countries, year, antibiotc types , bacteria types. Apart from that, data collected from hospitals and research institutes worldwide are non-continuous and non-comparable. A few reasons contribute to the non-comparable and non-continuous nature of the data: 

1. Variation in surveillance practice in different clinic, hospital and institutes worldwide. 

2. The same data source is not consistently available as the patient could have recovered or deceased from the infections. But the resistance strain of bacteria remains or likely transmitted to other hosts: human, animal or other living beings. Often without noticed by naked human eyes, until symptoms and tests show that. 

3. Even though patients may have stayed infected, samples may not be taken in a consistent basis.

4. Not all infectious patient cases are collected for resistance test. 

5. Diffucult to coordinate and obtain up-to-date and standardized data in a global scale.

As such when investigating individual bacteria,  we will not observe from the map, a continuous flow of data from the same countries. What we can observe from this mass of loose data is the eventual increase in resistance in countries as more resistance is reported in recent years. 

The phenomenon looks profound and daunting when all bacteria types' (seven in this visualization) are aggregated and animated throughout year 1987 to 2013 as the page starts.

After the aggregated bacteria resistance animation are done. Users can choose invidual bacteria type to investigate: seven chosen bacteria's resistance towards their applicable antibiotics in percentage. 

Data is collected in the form of isolate test data. Isolates are single-strain culture of bacteria in study isolated from other bacteria. A typical human colon alone contains ~ 5600 strains/species of bacteria. It is then tested with the antibiotic applied on the culture to observe resistance. Isolates can be extracted from blood, urinary or soft tissues. The more isolates used in the test, the more accurate the resistance result is, statistically. 

I have made the decision to remove year 2014 data as data available are mostly from developed countries, mainly European countries. Otherwise it gives the false impression that the other countries has no resistance reported. It is understood that, the data collection and organization for year 2014 and onwards are still in the works. Between year 2010 -2012, where most data are collected (due to more resistance reported as well as collection and cleaning work are mostly done), we can observe the severity of bacteria resistance. Since the condition in 2012 are likely to persist in 2013, I have also made the decision to carry forward 2012 data to 2013 when year 2013 data in countries with 2012 data are yet to be available. The reason being is it is very unlikely for those bacteria strains that developed resistance to be subdued in year 2013 as there are no newly developed antibiotics before and during the period.

The visualization should distinguish the characteristic of each level of these dimensions as well as not losing a general overview. As such a decision has been made to allow users the freedom to choose calculated resistance at different level of the dimensions, by recalculating the weighted average resistance (weighted towards data points with higher number of test isolates)at bacteria level, and then segregate at antibiotic level (if the bacteria has more than one antibiotic), and then further segregate at year level;  with each level of segregation presented for all countries in the map. The tooltip hovering over each country shows the calculated weighted average resistance for different level. 

The initial plan is to show resistance in circle size and later changed to country shaded in color tone. So that the presentation is cleaner as there are too many data points for circles to visualize effectively. 

The timeline animation simply allow users the choice to stream through the change of resistance over the years. However, due to non-continuous nature of the collected data, we may not see an obvious trend from the animation, particularly for individual bacteria types. For bacteria types with abundant data, the change is more prominent. 

World health Organization (WHO) is collecting more data in a worldwide scale currently, at the same time recommending standardized surveillance practice. As such, I expect the visualization to show more severity in antibiotic resistance as more data is made available in the near future. It will communicate this unseen phenomenon by human eyes more effectively to the pubic and decision makers with a stake, which is my motivation of constructing this visualization in the begining. It will be a work in progress for as long as it should, as institutes worldwide are working together to standardize and collect surveillance data. 

Note: CSV file with 2014 data is saved as Antimicrobial_Resistance.csv which is called by AMR.html, CSV file without 2014 data is saved as Antimicrobial_Resistance2.csv which is called by AMR2.html
    AMR-first.html is the first version of the html before design improvement. It calls Antimicrobial_Resistance.csv

###Design choice made after feedback
As the mouse hovers over the countries, it is hard to tell which country it is hovering on when the country is small. As such a choice has been made to highlight the borders of the active country with thick white border. Also, changing the opacity to 0.8 enhances the effect of a highlighted country. 

Also a zoom and pan feature has been added to make smaller countries more visible, when user deem it is necessary to zoom in.

Some users has raised concern that the range of colors (from low to high resistance) are not easily distinguishable in a single-hue color tone. As such different color tone is tested out using "colorbrewer.v1.min.js" , and finally 9 classes of multi-hue Yellow Orange Red [range(colorbrewer.YlOrRd[9])] or Blue-Purple [range(colorbrewer.BuPu[9])]are shortlisted. The map is showing Yellow-Orange-Red. 

A decision is also made to include a line of text to describe what is under animation when the animation is ongoing. 


##Feedback

First reviewer:  Some countries are too small to tell if the mouse cursor is hovering on it and the data is about that countries. 

Second reviewer: Color scheme makes it difficult to tell the level of resistance. 

Third reviewer: The lines on the map are making it messy.


##Resources

Data file: 
1. Data extracted from Antibiotic resistance data compiled from WHO surveillance report Annex 2 table & other reports listed in Reference materials #7, #8, #9 & #10: Antimicrobial_Resistance.csv, Antimicrobial_Resistance2.csv

2. World map in topo json format: world-topo-min.json

Javascript library used: 
1. d3.legend.js
2. d3.v3.min.js
3. colorbrewer.v1.min.js
4. topojson.v1.min.js

CSS file - included in html file.

Note: A production version has been put online in my personal site: 

http://www.onsiteintime.com/antimicrobial-resistance-visualized/


##Reference materials: 

1. Antimicrobial resistance: Global report on surveillance 2014, Annex 2 Reported or published resistance rates in common bacterial pathogens, by WHO region - Full report at http://www.who.int/drugresistance/documents/surveillancereport/en/

2. Color scheme picker using ColorBrewer scales, http://bl.ocks.org/pykerl/5637707

3. D3-Tips-and-Tricks.pdf, https://leanpub.com/D3-Tips-and-Tricks

4. D3 Nest Tutorial and examples, http://bl.ocks.org/phoebebright/raw/3176159/

5. Jerome Cukier's site, http://www.jeromecukier.net/

6. Examples in d3js.org

7. Central Asian and Eastern European Surveillance of Antimicrobial Resistance. Annual report 2014 - http://www.euro.who.int/en/health-topics/disease-prevention/antimicrobial-resistance/publications/2015/central-asian-and-eastern-european-surveillance-of-antimicrobial-resistance.-annual-report-2014

8. Antimicrobial resistance surveillance in Europe 2014 - http://ecdc.europa.eu/en/publications/_layouts/forms/Publication_DispForm.aspx?List=4f55ad51-4aed-4d32-b960-af70113dbb90&ID=1400

9. ReAct Antibiotic resistance data - http://www.reactgroup.org/toolbox/category/measure/access-existing-data-measure/access-existing-data-antibiotic-resistance/

10. National Antimicrobial Resistance Monitoring System for Enteric Bacteria (NARMS)Annual Reports - http://www.cdc.gov/narms/reports/index.html



