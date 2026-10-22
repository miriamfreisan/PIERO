## Miriam Freiria Sanjuan

En el siguiente documento se encuantran las explicaciones de cómo se han realizado los códigos para el piero, además de los vídeos de este funcionando, los pechakuchas y los tópicos de cada hito y demás tareas solicitadas.

# Hito 1

En este hito nos centraremos en las partes del Piero, el Arduino 2560 y la programación con Simulink. Una vez conozcamos todo esto programaremos los motores de las dos ruedas del robot, así como las luces LED y los sensores del mismo utilizando MATLAB, más concretamente Simulink.

En primer lugar, tenemos el certificado de Simulink.

![certificate (1)](https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/58ac77ea-36e1-4f40-9307-0a1a76bc7d36)

Seguido de los tópicos de este hito, que en mi caso se trata de Simulink. En el siguiente vídeo se describe cómo se instala Simulink, cómo se instala Arduino Mrga 2560, los modos de ejecución, los bloques más usados y los bloques de visualización de Simulink.
https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/e820102b-9cdf-4980-ba29-0b4fd165e64a

A continuación tenemos los códigos: Comenzaremo con una visión del hito 1 completo, que sería el evitaparedes. El piero debe usar los motores para moverse, mientras esquiva obstáculos con los sensores y dependiendo de estos últimos, enciende una luz LED de un color u otro. Como vemos en la siguiente imagen, los sensores detectan las entradas y a través de un señalizador (que transforma los centímetros en luz verde, amarilla, roja o roja parpadeante) y un controlador (que convierte la distancia en pwm, es decir, a modulación de ancho de pulso), tenemos las salidas, que son las luces LED y los motores.

<img width="1552" alt="Captura de pantalla 2024-01-25 a las 18 39 32" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica-ra2023grupo04/assets/145487813/8ec3292a-7ddb-4efa-bdef-c905e95f6308">

Ahora vamos a explicar uno por uno por los motores y el controlador. En la siguiente imagen podemos observar que a través de un demultiplexor, salen la rueda izquierda y la derecha. Cada una de las ruedas tiene un bloque para ir hacia delante y otro para ir hacia atrás, así como un enable, que nos da juego para controlar el robot hacia delante, hacia atrás, realizar giros cuando una está en enable y la otra no y rotar sobre sí mismo cuando una va hacia delante y otra hacia atrás, pero esto ya lo veremos más adelante en otros hitos.

<img width="1391" alt="Captura de pantalla 2024-01-25 a las 18 18 19" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica-ra2023grupo04/assets/145487813/c31fb391-4f0c-471b-abc2-8f3cd39c27a2">

Como podemos observar, trabajamos con subsistemas. En este caso, la entrada al demultiplexor es un bloque "Constant" desde el que configuraremos lo que hemos explicado anteriormente sobre los motores. A continuación tenemos una imagen donde podemos observar que en este caso ambas ruedas irán hacia delante (ambos números son poditivos) y en línea recta (tenemos la misma cifra tanto para la izquierda como para la derecha). En este punto cabe destacar que tanto en motores como en sensores o cualquier otro dispositivo, el derecho siempre se pone primero por una cuestión de orden y comodidad.

<img width="1239" alt="Captura de pantalla 2024-01-25 a las 18 28 05" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica-ra2023grupo04/assets/145487813/0b8448a0-fd34-4dbf-8860-00e787977209">

A continuación el controlador, que como ya hemos mencionado anteriormente transforma distancia en pwm.

<img width="1552" alt="Captura de pantalla 2024-01-25 a las 18 45 40" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica-ra2023grupo04/assets/145487813/052fca39-c41e-4d19-97ca-a6a6f703a2f6">

Seguimos con las luces LED, cuya entrada al subsistrema viene del señalizador. Nos encontramos con tres opciones, que son amarillo, rojo y verde; sin embargo, en la vida real la luz verde tiene un tono azulado y la roja es más bien magenta. Tenemos un "switch" para indicar si están encendidos o apagados y la función "boolean" que nos indica que los datos son de tipo lógico, es decir, las luces estarán a 1 (encendidas) o a 0 (apagadas).

<img width="1552" alt="Captura de pantalla 2024-01-25 a las 18 49 33" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica-ra2023grupo04/assets/145487813/60c7d4c4-4a05-4b0d-a0c6-9b07ff276351">

De este último tenemos el siguiente tutorial:

https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/cdb0ec26-3bac-433d-b161-b8e6af2cf949

Por último, el señalizador. Su entrada viene de los sensores, ya que depende de estos si la luz es verde, amarilla, roja o roja parpadeante. En este código lo que tenemos es el momento en que se encienden los LEDs y de qué color lo hacen. Si el sensor izquierdo detecta un obstáculo, se encenderá el LED de color azul; si es el izquiero el que detecta algo, se encenderá de color amarillo; yen caso de que sea por ambos lados, parpadeará. Si ninguno de los dos sensores detecta nada, la luz será blanca.

<img width="1552" alt="Captura de pantalla 2024-01-25 a las 18 52 05" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica-ra2023grupo04/assets/145487813/cd09126c-6552-432e-be04-27cf86d8ede7"> 

El siguiente vídeo es una demostración de los sensores, motores y LEDs trabajando en conjunto. Primero desde más cerca y ya después con el piero en el suelo.

https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/d0a2dc4b-bb93-4ef7-918b-685682b0c505

Para terminar con este hito, tenemos el pechakucha del mismo:

[Pechakucha_H1_Grupo04.pdf](https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/files/14056579/Pechakucha_H1_Grupo04.pdf)

# Hito 2

En este hito obtendremos el modelo de los motores del piero y trabajaremos en bucle abierto, es decir, el piero se moverá en línea recta. Los tópicos son las ecuaciones diferenciales y su programación con Simulink, las variables de estado, su formulación y su implementación con Simulink, y SIMSCAPE. En mi caso, yo he tenido que realizar el modelo teórico de las ecuaciones diferenciales, que lo tenemos a continuación:

¿Qué es una ecuación diferencial y por qué son importantes en la ciencia y la ingeniería? Respuesta: Una ecuación diferencial es una ecuación que relaciona una función y sus derivadas. Son fundamentales en la modelización de sistemas dinámicos en ciencia e ingeniería.

¿Cuál es la diferencia entre una ecuación diferencial ordinaria (EDO) y una ecuación diferencial parcial (EDP)? Respuesta: Las EDO involucran derivadas con respecto a una sola variable independiente, mientras que las EDP involucran derivadas parciales con respecto a más de una variable independiente.

¿Qué es Simulink y cuál es su papel en la resolución de ecuaciones diferenciales? Respuesta: Simulink es un entorno de simulación gráfica utilizado en MATLAB para modelar, simular y analizar sistemas dinámicos, incluyendo la solución de ecuaciones diferenciales.

¿Cómo se representan las ecuaciones diferenciales en Simulink? Respuesta: En Simulink, las ecuaciones diferenciales se representan mediante bloques que describen el comportamiento de los sistemas dinámicos y las conexiones entre ellos.

¿Cuál es la importancia de la elección de un solucionador en Simulink al resolver ecuaciones diferenciales? Respuesta: La elección del solucionador en Simulink es crucial, ya que afecta la precisión y la eficiencia de la solución. Diferentes solucionadores son adecuados para diferentes tipos de ecuaciones.

¿Cómo se modela un sistema de segundo orden en Simulink? Respuesta: Un sistema de segundo orden se modela utilizando un bloque de transferencia de segundo orden en Simulink, que representa la función de transferencia de un sistema.

¿Qué es la condición inicial en la resolución de ecuaciones diferenciales en Simulink? Respuesta: La condición inicial es el valor de la variable dependiente en el momento inicial de la simulación. Es esencial para resolver ecuaciones diferenciales.

¿Cómo se puede llevar a cabo la validación de un modelo de Simulink que involucra ecuaciones diferenciales? Respuesta: La validación de un modelo de Simulink implica comparar las salidas simuladas con datos experimentales o teóricos para verificar su precisión y confiabilidad.

¿Cuáles son algunas de las aplicaciones comunes de Simulink en la ingeniería y la ciencia? Respuesta: Simulink se utiliza en una amplia gama de aplicaciones, como el control de sistemas, la simulación de sistemas eléctricos, la dinámica de fluidos, la mecánica y muchas otras áreas.

¿Cuáles son los recursos recomendados para aprender a usar Simulink y resolver ecuaciones diferenciales en este entorno? Respuesta: Puedes aprender Simulink a través de tutoriales en línea, cursos en MATLAB y documentación oficial. También es útil consultar libros de referencia sobre simulación y ecuaciones diferenciales en Simulink.

Una vez explicada la parte teórica, podemos proceder a los códigos y vídeos de este hito. 

Empezamos por el test de encoders, para el cual daremos diez vueltad a una de las ruedas y el resultado será el denominador en la ganancia, tal como podemos ver en la siguiente imagen. En cuanto al numerador, este corresponde con el diámetro de la rueda.

<img width="555" alt="testencoders" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/8e9d5687-636a-437b-badf-f13ebe4b7edd">

Ahora, con el mismo valor que hemos sacado de 1434, ya podemos realizar el código para la distancia:

<img width="1092" alt="Captura de pantalla 2024-01-26 a las 17 10 23" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/9f0c0a12-04a5-4bcb-b0b0-e5c7eba31939">

Y la velocidad, que es la derivada de la distancia:

<img width="1092" alt="Captura de pantalla 2024-01-26 a las 17 13 14" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/1d6d44fd-a463-4444-98e0-b17ded50cb11">

A continuación, tenemos el test de distancia, en el que el piero tiene que recorrer 4.1m. Para ello utilizaremos el subsistema de motores creado en el hito 1 y el "encoderdistancia" creado en el hito 2. La rueda izquierda va ligeramente más rápido que la derecha, por lo que lo ideal sería ponerle una ganancia al encoder. En este caso no lo he hecho porque se puede apreciar que la distancia es correcta. Más adelante, en el hito 4, esro sí será necesario.

<img width="1552" alt="Captura de pantalla 2024-01-26 a las 17 15 17" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/2167bf44-d638-418b-8001-2b627bdf885a">

Y un vídeo demostración de que el código funciona (cada baldosa son 40 centímetros aproximadamente, por lo que el robot debe recorrer 10 baldosas y un cuarto de la siguiente):

https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/4133e7b4-66fc-4f72-9b5b-88e46ee8b6ac

Ahora dbemos crear un subsistema de piero Hardware para implementar los códigos en el piero, y un piero model para las simulaciones. Empezamos con el Hardware, en que usaremos esta vez el "encodervelocidad" y nuevamente, por supuesto, los motores:

<img width="1092" alt="Captura de pantalla 2024-01-26 a las 17 19 25" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/b31bc060-6712-44f0-b06f-0be3a8d5997d">

Lo siguiente será crear el "TomaDatos", que es un código en el que tendremos dos posibles entradas pwm. La primera es una rampa, de la que obtendremos las zonas muertas; y la segunda un pulso, el cual llevaremos al System Identification. Empezamos por la rampa, con su respectiva demostración de que funciona:

<img width="1432" alt="Captura de pantalla 2024-01-26 a las 17 24 22" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/51703b61-4d37-400e-9bde-104c12a94973">

https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/2da47992-38e9-4ed0-ae23-a1175c2e38f3

En cuanto a las zonas muertas, si hacemos zoom en la imagen podemos observar que es aproxic¡madamente de 5 a 5.33:

![zonamuerta](https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/ec54f7f5-fc8f-4b2e-b937-977aa4fa3d7c)

Los valores de la rampa los enviamos al workspace y vamos mirando los que coincidan con 250, 200, 150,100, 50, 0, -50, -100, -150, -200 y -250 ara crear el controlador en buble abierto.

<img width="1092" alt="Captura de pantalla 2024-01-26 a las 18 09 12" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/457f9b5a-6d12-465a-91c9-d9965a301347">

Esta sería la rueda izquierda, relacionando cada valor de pwm con su respectiva velocidad en m/s:

<img width="1312" alt="Captura de pantalla 2024-01-26 a las 18 10 02" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/f8198c63-18b9-4017-bd1b-7f15b63c1fc3">

Y la derecha:

<img width="1312" alt="Captura de pantalla 2024-01-26 a las 18 10 19" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/be078c9c-3465-427a-947e-fda804f615a4">

Ahora, con el controlador, ya podemos crear un control en bucle abierto.

<img width="1106" alt="Captura de pantalla 2024-01-26 a las 18 15 19" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/e5b21d41-bdcb-4546-9c64-d220ab9dae6a">

El pulso, con una velocidad de 0.205 m/s, también con su demostración:

<img width="1409" alt="Captura de pantalla 2024-01-26 a las 17 24 37" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/594b867c-32d8-4676-8355-7860e1bfcfc6">

https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/70b34d35-0142-4862-af67-88facd203d3f

Lo siguiente será llevar los valores del pulso al System Identification, llevando las gráficas al model output y eligiendo la más adecuada para cada rueda. A continuación tenemos el system identificacion, seguido de las gráficas de rueda izquierda, un zoom de la misma, e igual para la derecha, todo en ese orden:

<img width="478" alt="systemidentification" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/fa490f7f-77a1-4605-b7e0-ab3f44eb70dd">

<img width="620" alt="izqcont" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/21fd232d-2e69-4605-95df-0c2889fea62a">

<img width="512" alt="izqcontzoom" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/b03f526f-7d71-4cc4-9525-6a65f7c83423">

<img width="512" alt="dchacontzoom" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/3173a997-ab39-4a62-9631-a6a4ac2827ce">

<img width="512" alt="Captura de pantalla 2024-01-30 a las 18 58 03" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/a39b7952-851d-4d89-9b30-71794263f4e8">

Al igual que hicimos con la rampa, ahora cogeremos las gráficas más adecuadas de rueda izquierda y derecha, en este caso "tfi21" y "tfd21", las enviaremos al workspace y de ahí sacaremos el numerador y denominador de las funciones de transferencia correspondientes al piero model (simulación).

<img width="1092" alt="Captura de pantalla 2024-01-26 a las 18 17 01" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/b652b07e-88dc-4393-a807-42a5633f9c80">

Ahora que ya tenemos los códigos de "piero_Hardware" y "piero_model", es decir, en Hardware y en simulación, vamos a realizar una comparativa de ambos modelos:

<img width="1109" alt="Captura de pantalla 2024-01-26 a las 18 20 49" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/3fb3e8fa-64f1-444c-94fb-f18867e738a0">

Y por último realizaremos un modelo híbrido en el que según el modo de ejecución (si es simulado o en Hardware), se seleccione uno de los dos de manera automática. Esto lo conseguiremos gracias a un bloque "variant source":

<img width="1106" alt="Captura de pantalla 2024-01-26 a las 18 22 17" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/fe3cbd1d-2991-462e-ac6b-3c89150ab990">

Para terminar este hito, tenemos el pechakucha del mismo:

[Hito 2 - V2 (1).pdf](https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/files/14067673/Hito.2.-.V2.1.pdf)

# Hito 3

Este hito va sobre el control de los motores y los errores del modelado. Inlcuiremos el control en bucle cerrado, es decir, el piero moviéndose en círculos. Los tópicos son la resolución obtenida en la velocidad lineal de las ruedas, el error de discretización y su origen, los tipos de controladores y su implementación con Simulink y hallar los posibles controladores P, I, D, PI, PD, PID aplicables para unas especificaciones de 0.55 tiempo establecimiento, tiempo de subida > 0.3 y sobreoscilación < 5% con la RLtools. En mi caso, yo me he encargado de los tipos de controladores y su implementación en Simulink, siendo estos los siguientes:

1) ¿ Que es en Controlador??
Compara el valor real de la salida de una planta con la entrada de referencia, determina la desviación o error, y produce ena señal de control que reducirá la velocidad a 0 ó un valor pequeño.

2) TIPOS De controlador.
- P, controlador Proporcional: multiplica el error; es el controlador mas simple.
- I, controlador Integral: Disminuye o elimina el error en el estado estacionario. El tiempo de respuesta es más lento que los P. 
- PI, contolador proporcional integral. Combina el compontamiento de los des anteriores.
- PD, controlador proporcional derivativo. Halla la derivada del error con respecto al tiempo y lo multiplica por una constante
- PID, controlador proporcional integral derivativo. Calcula la desviación o error entre en valor medido y el real. Aprovecha las ventajas de cada uno de los controladores anteriores. Ofrece ena respunta muy rápida, sin embargo este sistena es muy propenso a oscilar. Los parámetros con dificiles de ajustar.
  
3) PARAMETERS:Ajustar los valores de las ganancias y  otros valores
OPTIONS:Configurar opciones avanzadas,como la saturación del controlador o el tiempo de muestreo
BOTONES: ejecutar simulaciones, guardar configuraciones personalizadas, o abrir ventanas de visualización y análisis

En cuanto a los códigos, comenzaremos con el controlador en bucle cerrado, que tiene dos controladores tipo PI. 

<img width="1078" alt="Captura de pantalla 2024-01-26 a las 19 01 47" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/fdba53ae-6b7a-4a8a-b6a3-2faafe114c43">

Los controladores tienen que cumplir las siguientes especificaciones: tiempo de establecimiento de 0.55, tiempo de subida > 0.3 y sobreoscilación < 5% y han de ser iguales. No hemos conseguido que sean al 100% iguales pero la diferencia es mínima. Estas son las gráficas del controlador izquierdo y derecho, respectivamente, después de sintonizarlos:

<img width="425" alt="izquierda" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/630b6929-e81e-403b-9850-69809c55d336">

<img width="425" alt="derecha" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/014a9b4c-32aa-4aa9-aaca-3c73312d777d">

Con el subsistema anterior y el "pieromfs", que es el nombre que le hemos dado al modelo híbrido, crearemos el código de control continuo, con el que comprobaremos el error de discretización.

<img width="1078" alt="Captura de pantalla 2024-01-26 a las 19 06 52" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/9d333f9e-9660-435b-976c-16df96e89155">

Ahora tenemos el vídeo donde comprobamos dicho error de discretización:

https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/31569d4e-514a-4b9a-aa32-5492e892ef8e

El control continuo lo convertiremos en un subsistema, que se llamará "PieroControlado" y será uno de los cuatro subsistemas necesarios para crear el código con el que el piero dará vueltas en círculo. El código es el siguiente:

<img width="1552" alt="Captura de pantalla 2024-01-26 a las 19 10 09" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/1c2bf33f-c0f0-41b3-a10c-76bc8a1d6629">

Respecro al MCD (modelo cinemático directo) y el MCI (modelo cinemático indirecto), los valores de estos se sacan de los apuntes teóricos de cinemática y los códigos son los siguientes (el MCI primero y el MCD después):

<img width="1552" alt="Captura de pantalla 2024-01-26 a las 19 12 25" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/02269f92-b69e-4dd3-99c4-ca53cc910837">

<img width="1552" alt="Captura de pantalla 2024-01-26 a las 19 12 33" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/a782a1c0-c7af-4519-b7a8-5690f35bda04">

El último subsistema, la odometría, la usaremos para comprobar el gráfico del movimiento que realiza el piero al ejecutar el código.

<img width="1552" alt="Captura de pantalla 2024-01-26 a las 19 13 40" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/db9b7bab-e110-4868-a35d-b0c1f5169e1b">

<img width="437" alt="graficoodometria" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/b27ef3b1-f749-48bc-95d7-1cc9cd73604d">

Y por último el vídeo del piero en bucle cerrado:

https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/5011dc72-a556-4371-a633-2f55612704d4

Para terminar este hito, tenemos el pechakucha del mismo:

[Pechakucha_H3_ V1 (2) (1).pdf](https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/files/14068109/Pechakucha_H3_.V1.2.1.pdf)

# Hito 4

En este hito el objetivo es mover al piero con control discreto y consignas de velocidad. En cuanto a los tópicos, yo me he encargado de realizar una comparativa entre las transformadas de sistemas continuos y de sistemas discretos:

1- ¿Qué son?
CONTINUOS: Son aquellos cuyas variables evolucionan continuamente con el tiempo.
DISCRETO: Aquel que cambia su estado en intervalos de tiempo variado y no de forma constante
HIBRIDOS: Combina continuos y discretos 

2- Tipos de señales: 
Un Sistema continuo tiene como entrada señales continuas, o lo que viene a ser lo mismo señales analógicas convirtiendola en señales continuas de salida. Utilizan la transformada de Laplace.
un Sistema discreto tiene como entrada señales discretas, o lo que viene a ser lo mismo señales digitales convirtiendola en señales discretas de salida. Utilizan la transformada z.

3- Análisis de Estabilidad:
Sistemas Continuos:
La estabilidad se analiza en función de los polos en el plano complejo-s.
Si todos los polos tienen parte real negativa, el sistema es estable.
La estabilidad se asocia con la región izquierda del plano-s.
Sistemas Discretos:
La estabilidad se analiza en función de los polos en el plano complejo-z.
Si todos los polos están dentro del círculo unitario, el sistema es estable.
La estabilidad se asocia con el interior del círculo unitario en el plano-z.

4- Métodos de Ruth-Hurwitz y de Jury:
El teorema de Ruth-Hurwitz proporciona un criterio capaz de determinar en cuál semiplano (izquierdo o derecho) del plano complejo están localizadas las raíces del denominador de la función de transferencia de un sistema; y en consecuencia, conocer si dicho sistema es estable o no. También se utiliza para el trazado del lugar de las raíces. Su objetivo es determinar el límite en el que los polos del sistema en bucle cerrado pasan al semiplano derecho complejo y por lo tanto el sistema se vuelve inestable.Los resultados obtenidos quedarán en función dela ganancia de k.
El criterio de estabilidad de Jury es un método para determinar la estabilidad de un sistema de tiempo discreto lineal mediante el análisis de los coeficientes de su polinomio característico.Es análogo al metodo de Ruth, Con la diferencia de que el criterio de estabiliddad de juryrequiere que los polos del sistema estén ubicados dentro del círculo unitario centrado en el origen, mientras que el criterio de estabilidad de Routh-Hurwitz requiere que los polos estén en la mitad izquierda del
plano complejo.

Respecto a los códigos, comenzaremos por pasar cada uno de los subsistemas de los anteriores hitos de control continuo a control discreto. 

<img width="1092" alt="Captura de pantalla 2024-01-27 a las 18 49 30" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/9746084c-5077-41dd-a4d9-b03e73e1064e">

Y las gráficas del controlador discreto en bucle cerado cumpliendo las especificaciones del hito 3. En primer lugar la rueda izquierda y después la derecha:

<img width="1044" alt="Captura de pantalla 2024-01-30 a las 19 27 28" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/1722100b-f6f4-4801-b580-ea733c7a98b3">

<img width="1047" alt="Captura de pantalla 2024-01-30 a las 19 28 22" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/bc6be12f-7476-46b9-839e-1b47559df6e7">

En cuanto a las funciones de transferencia, las hemos sacado, como en el hito 2, del system identification y, llevando las gráficas al model output, hemos elegido la más adecuada para cada rueda. Después hemos cogido esa elegida, la hemos puesto en el workspace y de ahí hemos sacado los valores de numerador y denominador de las funciones. A continuación tenemos el system identificacion, seguido de las gráficas de rueda izquierda, un zoom de la misma, e igual para la derecha, todo en ese orden:

<img width="796" alt="system_identification" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/19496c31-afe7-4dff-b430-eb6978d3b88e">

<img width="512" alt="izqdis" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/b541e973-abf2-43c9-8205-922c33f55670">

<img width="512" alt="izqdiszoom" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/ad7923e6-9612-4e1e-9f2e-0e1836182899">

<img width="512" alt="dchadis" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/84b29bbd-6ec2-4ceb-bff4-48a3297d7f7b">

<img width="512" alt="dchadiszoom" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/21c340f6-5a37-4df4-a160-732d6f3b797f">

En las imágenes podemos observar que los valores más adecuados son los de "tfiz10" y "tfdz20", que serán los llevados al workspace, donde podemos observar que coinciden con los valores de las funciones anteriores (primero la izquierda y luego la derecha, como siempre):

<img width="432" alt="Captura de pantalla 2024-01-30 a las 19 18 37" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/04a228a0-c2a7-45bb-836f-4ead8a92a55f">

<img width="432" alt="Captura de pantalla 2024-01-30 a las 19 18 29" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/073556d2-78d0-4f91-8979-db664c1f9d30">

<img width="1092" alt="Captura de pantalla 2024-01-27 a las 18 51 00" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/b706c122-8bde-452d-8995-0a5bea168767">

Y seguimos con el resto de subsistemas:

<img width="1092" alt="Captura de pantalla 2024-01-27 a las 18 50 12" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/bbf04b51-6159-4de3-bd08-6122bf059be5">

<img width="1092" alt="Captura de pantalla 2024-01-27 a las 18 49 56" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/20aabdda-befd-4d5a-bc28-2066ba4d5b19">

<img width="1092" alt="Captura de pantalla 2024-01-27 a las 18 50 50" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/833d274d-832b-4be2-bbbe-36d8afe9dc01">

<img width="1092" alt="Captura de pantalla 2024-01-27 a las 18 50 31" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/26d20a6f-053c-4d24-982c-9afb6ce977ab">

En cuanto al encoder de velocidad, este tiene una ganancia en el ziquierdo, ya que iba torcido y sin ella no lograría salir de clase.

<img width="1092" alt="Captura de pantalla 2024-01-27 a las 18 49 42" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/8ea6ee57-9721-4660-8917-4037f6869e90">

Una vez tenemos los subsistemas en control discreto, ya podemos comenzar con los códigos de este hito, que tiene cuatro partes: Primero el Piero deberá caminar un metro, después dar una vuelta completa en diez segundos, luego girar sobre sí mismo y por último salir del aula dando tres giros de 90º. 

Comenzamos con los códigos y las gráficas de los controladores de las ruedas izquierda y derecha (en ese orden) del piero recorriendo un metro:

<img width="1092" alt="Captura de pantalla 2024-01-27 a las 18 59 34" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/75022295-6897-4fa2-b4b8-eba152db60e2">

<img width="1092" alt="Captura de pantalla 2024-01-27 a las 18 55 53" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/a690579a-773d-405d-9a62-a9788100d8ef">

<img width="1092" alt="Captura de pantalla 2024-01-27 a las 18 56 00" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/47c4d527-4e84-43fe-b799-664ea4212b63">

<img width="1435" alt="Captura de pantalla 2024-01-27 a las 19 03 39" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/b2d0fca5-4e35-42c0-b870-77b5f0842d8e">

<img width="1068" alt="Captura de pantalla 2024-01-27 a las 19 04 32" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/6b1e4898-f8a0-4b1d-ae59-4a669bceadfd">

A continuación os códigos y las gráficas de los controladores de las ruedas izquierda y derecha (en ese orden) del piero dando una vuelta en 10s:

<img width="1254" alt="Captura de pantalla 2024-01-27 a las 19 08 28" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/f81058c0-88b9-4a87-acb2-866a2c20e263">

<img width="1064" alt="Captura de pantalla 2024-01-27 a las 19 13 47" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/1cdf4350-29c3-4f71-8af9-2997b3a1ef61">

<img width="1065" alt="Captura de pantalla 2024-01-27 a las 19 14 36" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/2b3a6974-c4f1-4ded-8d7a-8004f8bb3067">

Ahora el giro sobre sí mismo en 8 segundos. En este caso se ha hecho con un P y después con un PI. La gráfica adjuntada será la del PI, puesto que es la que tiene los valores más precisos. Aun así, en ninguna de las dos cumplía todas las especificaciones. Por lo tanto, vamos a hacerlo primero de manera que cumpla el tiempo de establecimiento y seguidamente cumpliendo el de subida, en ambos casos tratando de no diferir mucho el otro:

<img width="1254" alt="Captura de pantalla 2024-01-27 a las 19 16 58" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/38d17560-9cb7-42c3-a1b6-db240821407c">

<img width="1059" alt="Captura de pantalla 2024-01-30 a las 18 39 55" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/f27edf08-cd54-40f9-a002-49014b663893">

<img width="1254" alt="Captura de pantalla 2024-01-27 a las 19 17 12" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/3fcdaa29-9841-4d0e-a682-1f0d5157a02a">

![giro8s](https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/8f259876-f6be-43ea-a889-85b093e1b1a0)

Por último, el piero saliendo de clase dando tres giros de 90º:

<img width="1552" alt="Captura de pantalla 2024-01-27 a las 19 23 51" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/64b62ba7-2bac-4676-b686-5c0dff81e533">

<img width="979" alt="Captura de pantalla 2024-01-27 a las 19 23 46" src="https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/2652d427-89f9-45bf-a37b-0959fd045fec">

Y el vídeo del piero haciéndolo:

https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/assets/145487813/895147df-6204-4599-8ae2-0ed52003f546

Para terminar este hito, tenemos el pechakucha del mismo:

[Pechakucha_H4_V1 2.pdf](https://github.com/Escuela-de-Ingenierias-Industriales/RegulacionAutomatica23-miriamfreisan/files/14073350/Pechakucha_H4_V1.2.pdf)



