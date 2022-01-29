# temprature-vs-iceCream

from statistics import correlation
import plotly_express as px
import csv
import numpy as np


def getDataSource(data_path):
    ice_cream_sales = []
    cold_drink_sales = []
    with open(data_path) as csv_file:
        csv_reader = csv.DictReader(csv_file)
        for row in csv_reader:
            ice_cream_sales.append(float(row["Temprature"]))
            cold_drink_sales.append(float(row["Ice-cream Sales( ₹ )"]))

    return {"x":ice_cream_sales, "y": cold_drink_sales}

def findCorrelation(datasource):
    correlation = np.corrcoef(datasource["x"], datasource["y"])
    print("Correlation between Temprature vs Ice Cream Sales :- \n---> ", correlation[0,1] )


def setup():
    data_path =  "./data/Ice-Cream vc Cold-Drink vc Temprature - Ice Cream Sale vs Temprature data.csv"

    datasource = getDataSource(data_path)
    findCorrelation(datasource)

setup()
