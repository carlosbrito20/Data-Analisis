# Data-Analisis

Visualización de data en con Jupiter usuando Pyhton

## Información 
Levanto dataset con el nombre de dow_jones_index.data \
Uso pandas para visualizar el dataset en formato dataFrame \
Se realiza modelado y limpieza de datos
Realizo visualización de los datos con matplotlib

## Visualización de los procesos. 

## Ejecución
Para ejecutar la notebook uso jupiter que viene integrado en anaconda navigator.

## Codigo proceso 

import pandas as pd
from matplotlib import pyplot as plt
%matplotlib inline

data_raw = pd.read_csv(r"C:\UBICACION-DEL-ARCHIVO\dow_jones_index.data")
data_raw.head()

data = data_raw.copy()

print("Creo una lista con las variables numericas")
price_vars = ["open","high","low","close","next_weeks_open","next_weeks_close"]
print(price_vars)
print ("")
print("Elimino el caracter $ de la lista")
data_floats = data_raw[price_vars].applymap(lambda x: x.replace("$","")).astype("float")
# visualizo la salida
print(data_floats.head())
# Aplico las operaciones al dataframe
data[price_vars]  = data_floats
print ("")
# formateo la fecha y verifico la salida
data["date"] = pd.to_datetime(data.date, format="%m/%d/%Y")
print(data["date"].head())
# selecciono el stock que sea = AA
AA_data = data[data["stock"]=="AA"]
# tomo del dataframe la fecha y el high para ver su comportamiento graficamente y a su le coloco el label de color azul
plt.plot(AA_data.date,AA_data.high, label ="high", c="blue")
# tomo del dataframe la fecha y el low para ver su comportamiento graficamente y a su le coloco el label de color amarillo
plt.plot(AA_data.date,AA_data.low, label ="low", c="yellow")
# incrustar la leyenda
plt.legend(loc="best")
# muestro el objecto
plt.show()

## Test view
Insert here an image of the preview if your project has one. The image can be into the project, you have to indicate the route and look like this.

![](/preview.jpg)
