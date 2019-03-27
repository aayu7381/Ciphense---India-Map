import folium
import pandas as pd

# we require only these three fields from the dataset
fields=['name_of_city','population_total','location']
data_frame=pd.read_csv("indian cities.csv",usecols=fields)

#location column of data_frame consist of both latitude and longitude seperated by a ','.
#seperate them into two columns.
new = data_frame["location"].str.split(",", n = 1, expand = True)  
data_frame["Latitude"]= new[0] 
data_frame["Longitude"]= new[1]

#deleting location column as it's no more required
data_frame.drop(['location'],axis=1)

#creating a background map of india
map_india=folium.Map(location=[22.778,80.434],zoom_start=5)

#iterating the whole data_frame
for index,i in data_frame.iterrows():
    #marking the cities on map having population greater than 500000
    if(i['population_total']>500000):
        folium.Marker(location=[float(i['Latitude']),float(i['Longitude'])],  tooltip=i['name_of_city']).add_to(map_india)

        #saving the map as an html file
map_india.save('india_map.html')
