# CLASE 2 II CORTE
# PERFILES DE MOVIMIENTO
Se define como una trayectoria, es la distacia que debe moverse el mecanismo desde un punto A  hasta un punto B. Si se tiene un solo eje, ese perfil de movimiento serìa una lìnea recta, es de aclarar que cuando se tiene mas ejes, se tendran trayectorias mas complejas, ademàs interactuan entre ellos para lograr tareas especìficas. Desde le controlador se debe garantizar que el perfil de movimiento se cumpla. 
En muchas aplicaciones, no basta solo con mover algo de un punto A a un punto B, en las plantas modernas se requiere que esta trayectoria tenga una velocidad y aceleraciòn determinada, con el objetivo de proteger la planta o el mismo producto. 

## Conceptos básicos
**Cinemática:** Tener claro el estudio de la posiciòn, velocidad, aceleraciòn y tiempos para el cálculo de perfil de movimiento y el dimensionamiento de motores. 

-Si se considera un solo eje, la posiciòn será *s(t)*, en funciòn del tiempo, puesto que se requiere saber en cada momento la posiciòn, para asi optimizar las trayectorias y por ejemplo buscar la menor distancia posible, o mejorar la eficiencia del proceso a partir del control. Y en su forma integral $s=\int v(t)\,dt$. 

-La velocidad *v(t)* la razón de cambio con respecto al tiempo. Y en su forma integral $v=\int a(t)\,dt$.  

-La aceleraciòn *a(t)* la razòn de cambio de la velocidad. 

## Curvas
Cuando se diseña un perfil se obtienen las siguientes curvas, estas curvas son diseñadas por el usuario, puesto que se hacen para un caso especifico de acuerdo a las necesidades y movimiento que se quiera en el controlador. Dependiendo de lo que se conozca del proceso se puede comenzar con la curva de posiciòn, sin embargo en la mayoria de procesos se comienza con la curva de velocidad, pues se necesita garatizar cierto desplazamiento por unidad de tiempo, para posteriormente realizar las de posiciòn y aceleraciòn. 

![Figura de prueba](IMAGES/curvas.png)

## Reglas geométricas

-La posición es el área bajo el perfil de velocidad.

-La acelaración pendiente de el perfil de velocidad. 

![Figura de prueba](IMAGES/grafica.png)




