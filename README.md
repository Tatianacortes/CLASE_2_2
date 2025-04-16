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

![Figura de prueba](IMAGES/grafica2.png)

$v=v_0+a(t-t_0)$

$s=s_0+\dfrac{1}{2}(t-t_0)(v_0+a(t-t_0))$

Donde $t_0$ representa el tiempo inicial, $v_0$ la velocidad inicial y $s_0$ la posición en el instante inicial. La aceleración, considerada constante, se denota como $a$.

### Ejemplo

#### 1. 
Encuentre la posición y la aceleración en t=5s  

![Figura de prueba](IMAGES/Ejercicio.png)  

La aceleración sería la pendiente de la velocidad
 $m=\dfrac{10-0}{5-0}=2$
 $a=2$

Posición: 
$s=\dfrac{1}{2}*(10)(5)$
$s= 25\dfrac{in}{s}$

#### 2. 

Un eje está viajando a una velocidad de **10 cm/s**. En **t = 5 s**, empieza a disminuir la velocidad como se ve en el perfil.  ¿Cuál es la posición del eje cuando se detiene?  Asuma que empieza a desacelerar a **25 cm/s²**.

![Figura de prueba](IMAGES/ejercicio2.png)  

La pendiente de la velocidad es la aceleración:  

$$a = \frac{-10 \ \text{cm/s} \cdot \frac{1 \ \text{m}}{100 \ \text{cm}}}{(15 \ \text{s} - 5 \ \text{s})}$$

$$
= \frac{-0.1 \ \text{m/s}}{10 \ \text{s}}
$$

$$
= -0.01 \ \text{m/s}^2
$$

El área del perfil de velocidad triangular es la posición alcanzada en t=15s

$$
S_o = \frac{1}{2} \cdot (15 \ \mathrm{s} - 5 \ \mathrm{s}) \cdot 0.1 \ \frac{\mathrm{m}}{\mathrm{s}} = 0.5 \ \mathrm{m}
$$


#### 3. 

Un eje (axis) lineal comienza su movimiento desde el reposo en la posición 0, con una velocidad de $2\ \text{m/s}$.   Después de moverse durante $5\ \text{s}$, ¿cuál es la posición del eje (axis)?  

![Figura de prueba](IMAGES/ejercicio3.png)  

### Perfiles de movimientos comunes

Los mas usados son perfiles trapeziodal (lineales) y curva en s sigmoidal o gaussiano (no lineales). Estos son los tipos de perfiles que se pueden programar en el controlador. 

## **Trapezoidal**    

![Figura de prueba](IMAGES/Trapezoidal.png)*Tomado de: [https://www.libreservo.com/es/articulo/curvas-movimiento]([https://ejemplo.com](https://www.libreservo.com/es/articulo/curvas-movimiento))*

Cuando hace el trayecto del punto A al punto B, se tienen tres etapas:

1. En la primera, la velocidad aumenta (aceleración positiva).
2. Luego, se mantiene constante para cumplir con los requerimientos de tiempo.
3. Finalmente, antes de llegar al punto B, se desacelera (aceleración negativa).

**Tiempo total** = tiempo de aceleración + tiempo de movimiento + tiempo de desaceleración

Para hallar la posición B, se calcula el área bajo la curva de la velocidad (gráfica velocidad vs. tiempo), que forma un **trapezoide**. Este se compone de:

- Dos triángulos (aceleración y desaceleración)
- Un rectángulo (movimiento a velocidad constante)

La aceleración se comporta de la siguiente manera:

- Es constante y positiva mientras la velocidad aumenta (pendiente positiva).
- Es cero durante la etapa de velocidad constante.
- Es constante y negativa durante la fase de frenado (pendiente negativa).

> Un perfil de velocidad **no necesariamente es simétrico**.  
> Por eso se utilizan **trapezoides** y no trapecios, ya que se puede necesitar más tiempo para acelerar y menos para desacelerar, o viceversa, dependiendo de los requerimientos del proceso.  
> El trapezoide permite **ajustarse a las condiciones específicas** de cada aplicación.


 **Jerk**  
 
![Figura de prueba](IMAGES/jerk1.png)  

El **jerk** es la derivada de la aceleración con respecto al tiempo. Representa **la tasa de cambio de la aceleración**. En este perfil trapezoidal:

- En los puntos donde la aceleración cambia bruscamente (inicio y fin de aceleración o desaceleración), el jerk es **infinito o muy alto**, ya que el cambio es instantáneo.
- Este comportamiento puede provocar vibraciones o esfuerzos mecánicos si no se controla adecuadamente.
- Para que el jerk no sea muy alto y no genere daños en los motores, la solución es dimensionar bien el motor, puesto que cuando las cargas son muy grandes o estan cerca a los valores nominales, se experimenta el jerk que generalmente lo que daña es el sistema mecanico, pueden ser torsiones o flexiones en los ejes. 

### Ejemplo 
#### 1. 
Para el eje(axis) de la figura se desea calcular tm  

![Figura de prueba](IMAGES/motor1.png)  

**Geométrico**

$t_a = t_d = \frac{v_m}{a}$  

$t_{total}=t_a+t_m+t_d$  

Usando reglas geométricas se calcula el recorrido total L  

$L=\frac{t_av_m}{2}+t_mv_m+\frac{t_dv_m}{2}$  
$=v_m(t_a+t_m)$

Entonces el tiempo de movimiento tm es:

$t_m=\frac{L}{v_m}-t_a$

**Analítico**

Para 0<t<ta

$t_0=0,\ v_0=0,\ s_0=0$

$s(t)=\int_0^{t_a}at\ dt=\frac{1}{2}at^2\bigg|_0^{t_a}=\frac{1}{2}at_a^2$

Para ta<t<(ta+tm)

$t_0=t_a,\ v_0=v_m,\ s_0=s(t_a),\ a=0$

$s(t)=s(t_a)+\int_{t_a}^t v_m\ dt=s(t_a)+v_mt\bigg|_{t_a}^t$

$=s(t_a)+v_m(t-t_a)$  

Para (ta+tm)<t<ttotal

$t_0=(t_a+t_m),\ v_0=v_m,\ s_0=s(t_a+t_m)$

$s(t)=s(t_a+t_m)+\int_{t_a+t_m}^t -a*(t-(t_a+t_m))+v_m\ dt$

$s(t)=s(t_a+t_m)+\left[v_mt-\frac{1}{2}a(t-(t_a+t_m))^2\right]_{t_a+t_m}^t$

#### 2. 

El eje x de un robot Gantry debe moverse 10 cm. La máxima aceleración permitida en este eje es 1 cm/s².  Si se desea mover el eje a una velocidad máxima de 2 cm/s, ¿cuánto tiempo tomará hacer este movimiento?

![Figura de prueba](IMAGES/a.png)  


$t_a = t_d = \frac{v_m}{a} = \frac{2\ \text{cm/s}}{1\ \text{cm/s}^2} = 2\ \text{s}$  
$t_m = \frac{L}{v_m} - t_a = \frac{10\ \text{cm}}{2\ \text{cm/s}} - 2\ \text{s} = 3\ \text{s}$  

$t_{total} = t_a + t_m + t_d = 2 + 3 + 2 = 7\ \text{s}$

#### 3. 

Dado el perfil de velocidad de la figura, calcule $S_A, S_B, S_C$ usando las reglas geométricas y el método analítico del perfil de movimiento.

![Figura de prueba](IMAGES/ejercicio3.png)  

$$
S_A = \int_0^{0.5} 8t \, dt = \frac{8t^2}{2} \Big|_0^{0.5} = 4t^2 \Big|_0^{0.5}
$$

$$
S_A = 1 \, \text{cm}
$$  

$$
S_B = 21 \, \text{cm}
$$

$$
S_C = 22 \, \text{cm}
$$












