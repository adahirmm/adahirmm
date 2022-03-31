#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Fri Aug 13 13:08:23 2021

@author: dr.guillermo

Simulador Tiro Parabólico

"""
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation
#from mpl_toolkits.mplot3d import axes3d

# Parámetros 
x0= 0
y0= 0

v0y= 26 #velocidad inicial
ang= 40 # angulo del tiro

g= 9.81   # valor de la gravedad
h= 50     # altura

# en consola se debe habilitar
# %matplolib auto    modo ventana
#            inline  modo iterativo
# secuencia de tiempo
t=np.linspace(0,4)
#t= np.arange(0,100)

# Ec. mov en eje y 
y= h+ v0y * np.sin(ang)*t - ((g*t**2)/2)
#y= v0y * np.sin(np.rad2deg(ang))*t - ((g*t**2)/2)

# inicializamos figure
fig= plt.figure()

#tomamos los ejes
ax= fig.gca()

#actualizar la fig
#con el iterador i
def actualizar(i):
    ax.clear() # borrar ejex
    ax.plot(t[:i],y[:i]) #gráfica punto por punto
    plt.title(str(t[i])) # titulo 
    plt.xlabel("Tiempo")
    plt.ylabel("y(t)")
    plt.xlim(0,max(t))   # limites en x 
    plt.ylim(0,max(y))   #limites en y 
    
#animacion
#Hace una animación llamando repetidamente a una función 
ani=animation.FuncAnimation(fig,           # figura
                            actualizar,    # función en cada cuadro 
                            range(len(t)), # num de frames
                            interval=10,   # Retraso entre fotogramas en milise
                            repeat=False)  # repetir la animación 
plt.show() # muestra la gráfica
