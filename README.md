# Data-Wrangling-Challenge
This  project is about  normalised version of the European union Road Safety Facts and Figures, year is assumed to be 2018
The project entails a number of data manupulations
Some columns of the frame were exempted
A few illustrative charts are included
Data used for the project was sourced from the European union Road Safety Facts and Figures
link to data source https://en.wikipedia.org/wiki/Road_safety_in_Europe


## Requirements
The project was built using  Python script
The project requires the folowing modules:
Pandas
Matplotlib
Numpy(optional)



## Code

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib.style as style
import warnings

#Loading data
#data = https://en.wikipedia.org/wiki/Road_safety_in_Europe
data = pd.read_excel(r'C:\Users\EMMANUELLA\Desktop\Web-dev\DWC\RSFF.xlsx')
data
#Converting data to CSV format
data4 = data3.to_csv('RSFF.csv')
data5= pd.read_csv(r'C:\Users\EMMANUELLA\Desktop\Web-dev\DWC\RSFF.csv')
data5
#Removing exempted columns
data1= data.drop('Number of People Killed',axis = 1)
data2 = data1.drop('Number of Seriously Injured in 2017/2018[30]',axis = 1)
data3= data2.drop('Road Network Length',axis = 1)
data3
#Adding Year column
data3.insert(1,'Year',2018 ,True)
#Sorting data by Road daeths per Million Inhabitants 
new_data= data5.sort_values( by ='Road deaths' )
new_data

#Bar graph representation of  Average Population Density per Country
style.use('Solarize_Light2')
nn.groupby('Country')['Population density'].mean().sort_values(ascending = False).plot(kind ='bar',title= ' Average Population Density per Country')
plt.xlabel('Country')
plt.ylabel('Population density')
plt.legend()
plt.savefig('Chart1.png', dpi =300 ,bbox_inches ='tight')
plt.show()

#Bar graph representation of  Average Road deaths  per Country
style.use('ggplot')
nn.groupby('Country')['Road deaths'].mean().sort_values(ascending = False).plot(kind ='bar',title= ' Average Road deaths per Country')
plt.xlabel('Country')
plt.ylabel('Road deaths')
plt.legend()
plt.savefig('Chart2.png', dpi =300 ,bbox_inches ='tight')
plt.show()

#Pie chart visualizationof  Average Vehicle ownership per Country
new_data.groupby('Country')['Vehicle ownership'].mean().sort_values(ascending = False).plot(kind = 'pie',title= 'Average Vehicle ownership per Country')
plt.xlabel('Country')
plt.ylabel('Vehicle ownership')
plt.savefig('Chart3.png', dpi=300 , bbox_inches ='tight')
plt.show()
