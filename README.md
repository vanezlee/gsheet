# gsheet
all things about google sheet


1) Connecting gsheets with charts
https://developers.google.com/chart/image/docs/making_charts

2) Create charts on the fly and wrap them with function =IMAGE()to display in sheet. 
For example : 
https://chart.googleapis.com/chart?cht=p3&chs=250x100&chd=t:60,40&chl=Hello|World


3) Use this absolute custom format to shorten and make huge numbers more readable (usually in the millions and more). 
Formatting changes how the figure is displayed on the front end, but does not change the actual figure. Hence making any further computation on the figures accurate.
[<999950]0.0,"K";[<999950000]0.0,,"M";0.0,,,"B"]

3.1) Use the following format to insert currency into a custom format (replace $US)
[$US$][<999950]0.0,"K";[$US$][<999950000]0.0,,"M";[$US$]0.0,,,"B"]

3.2) If the currency is in the negative form, use the following custom format instead (replace $US): 
[$US$][<999950]-0.0,"K";[$US$][<999950000]-0.0,,"M";[$US$]-0.0,,,"B"]

4) Use a combination of sumifs, Indirect and Vlookup to summarise multiple total values by months that meet any criteria. 
// by coding the formula this way, the formula could be quickly replicated across the entire table. 
// Vlookup helps to automate the Indirect formula further by referencing the column location to be summed on a separate table, removing the tedious need to code each location within the final table. 

=sumifs(INDIRECT(vlookup(Column name that matches the raw data table, specify the table where the arguement could be found in the leftmost column, to return the data on the 3rd column of the table, to match the search exactly)), meets criteria 1 of sumifs formula, and meets certeria 2 of sumifs formula. 
=sumifs(INDIRECT(vlookup(C$7,List!$C$2:$E$18,3,false)),Raw!$A:$A,$B8,Raw!$F:$F,$C$4)
