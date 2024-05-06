# Cartera-de-Valores-de-la-AEAT.-Automatizacion-parcial
Si deseas introducir numerosos movimientos en el programa SERVICIO CARTERA DE VALORES de la AEAT, quizas mi script te puede ayudar.

El programa (AEC.CMD) esta basado en Perl. Usa el extracto en formato 'csv' (comma separated value) que puedes obter en tu aplicacion DEGIRO. Para otros brokers, favor contactarme.

Primeramente leera el archivo que tu le proporcionas, registro por registro. Los ordenara segun ISIN y dentro de ISIN por FECHA Y HORA. Cargados los datos de cada movimiento o registro es capaz de introducirlos en los respectivos campos de la ficha abierta en SERVICIO DE CARTERA DE VALORES (CARTERA), de la AEAT, de 2024 y algunos previos.

AEC.CMD crea una ventana abajo (vease la fotografia anexa), muy alargada, donde te muestra los datos del registro que quieres introducir. Hay diversos botones de control para facilitar la introduccion del Registro, regular velocidad, desplazarse al proximo registro, etc.


Este Readme.md te informa de:
1) Como instalar PERL
2) Como obtener tus datos en DEGIRO en formato CSV
3) Como disponer las tres VENTANAS en tu pantalla
4) Modos de abandonar el programa
5) Como trabajar en CARTERA de valores
6) Limites del programa, algunos consejos y trucos
7) Desinstalacion

AVISO: hay un cierto esfuerzo previo para prepararlo y aprender a usarlo pero despues ahorraras tiempo y trabajo. Y recuerdo que podras usarlo en futuras declaraciones de la renta, pues pretendo actualizarlo y mejorarlo. Una vez funcionando es facil actualizarlo.

SEGURIDAD: AEC.CMD es un script: no tiene archivos compilados ni ejecutables. Lo puedes leer como cualquier texto. Tampoco baja datos ni se conecta a ninguna parte. Simplemente capta los datos que tu le proporcionas mediante el archivo CSV y los vuelca en los campos correspondientes del programa CARTERA. Cualquier persona que sepa PERL puede leerlo y confirmarlo.

1.0 INSTALACION

1.1 PERL

Necesitas tener PERL en tu computador. Si ya lo tienes pasa a la siguiente fase (1.2 MODULOS).

Si no quieres que PERL modifique tu computador, te aconsejo usar la version 'PORTABLE'. Lo bajas aqui (gratuito):

https://strawberryperl.com/releases.html

Elije preferentemente la ultima version (5.38.2.2). Elige 32bit o 64bit segun tu computador (cuanto mas moderno, mas probable que sea 64bit).

1.2 MODULOS

Debes crear un directorio nuevo (ejemplo C:\P\ o D:\PL\ o C:\PERL\). Es importante que este vacio. Dentro extrae todo el contenido del zip que has bajado que sera probablemente: strawberry-perl-5.38.2.2-64bit-portable.zip.

Veras varios subdirectorios. Tu tienes que crear otro nuevo (C:\P\AE, por ejemplo).
Coloca en este subdirectorio unicamente los archivos del programa aec.pl (aec7.pl, bat.cmd, bat2.cmd, findit,cmd, aec.cmd).

Estando conectado con la web, abre el link que encontraras en la instalacion PERL, en el directorio raiz:

portableshell.bat

Se abrira una ventana parecida al de la CMD de windows. Es la VENTANA PERL.
Necesitamos actualizar algunos paquetes de programas. Para ello entra en el programa oficial de actualizacion de Strawberry PERL tecleando:

CPAN<enter>

Tu prompt pasa a ser:

CPAN>

Aqui, pasando las respectivas ordenes, CPAN instalara o actualizara los modulos que el AEC.CMD necesita. (importante: respeta mayusculas o minusculas en las respectivas ordenes o se produciran errores). Hay que esperar a que cada paquete se instale y puede tardar un tanto. Para introducir cada orden usa las flechas vertical y horizontal y completa la orden, ahorras tiempo. Una vez instalada cada orden es util repetirla. Esta vez CPAN te avisara de que tu modulo esta actualizado.

Cuando cada modulo esta listo, el prompt vuelve ser 'CPAN>'.

Introduce una orden de instalacion y espera: 

install Win32<enter>

install Win32::GUI<enter>

install Win32::GuiTest<enter>

install Win32::Clipboard<enter>

install Time::HiRes<enter>


Si todo ha ido bien la instalacion de PERL ya esta completa.

Para terminar y salir de CPAN introduce: 

exit<enter>

Y para cerrar la VENTANA PERL de nuevo:

exit<enter>

2.0 TUS DATOS DE DEGIRO

El programa AEC.CMD lee exclusivamente los registros de tus operaciones tal como los emite DEGIRO.
Para obtenerlos entra en tu aplicacion DEGIRO, seccion buzon, seccion transacciones.

Introduce fechas que te interesan. Ejemplo: 

(01/01/2023 hasta 31/12/2023). 

Una vez seleccionadas, en la misma linea horizontal de las fechas tienes una flecha apuntando hacia abajo a un guion bajo '_'. Accionandola aparecera la pantalla exportar: 

elige la opcion 'CSV' (comma separated value).

Accionandola te ofrece Download y si lo aceptas tendras en tu directorio de Downloads un archivo llamado:

'Transactions.csv'.

Ya tienes los registros de todos tus movimientos. Por supuesto si lo necesitas puedes obtener los de ejercicios anteriores e introducirlos.

Pon este archivo (Transactions.csv) en el directorio donde esta el programa AEC.PL (en nuestro ejemplo c:\p\ae\).

IMPORTANTE: el archivo, para ser reconocido tiene que llamarse 'deg.csv'. Renombra Transactions.csv para DEG.CSV.

3.0 PUESTA EN MARCHA: VENTANAS

Para trabajar comodamente necesitas 3 ventanas al mismo tiempo (vease la foto aec.pl.jpg):

Abre tu navegador (he experimentado con EDGE y FIREFOX) , entra en el sitio de la AEAT, reducelo para que quede arriba a la izquierda y deje 4 dedos a la derecha y 2 dedos abajo.

Abre el link:

portableshell.bat

que tienes en la raiz de la instalacion de PERL. Se abre la VENTANA PERL. Colocala a la derecha y reducela para que se encaje en los 4 dedos que le hemos reservado. Asi no se superpone con el navegador. Podras pasar de una a otra sin que se minimicen ni desaparezcan. 
Si te agrada, puedes ampliar la letra de la VENTANA PERL para ver mejor los datos. 
En el encabezamiento de la patalla haz clik para ir a 

>propiedades
>fuentemd

Para mi gusto, la fuente 20 esta bien.
Salva.

En el prompt teclea:

cd ae<enter>

para entrar en tu directorio, donde estan los archivos (aec.pl, bat.cmd, bat2.cmd, deg.csv, aec.cmd, findit.cmd).

Teclea:

perl aec.cmd<enter>
 
Acabas de iniciar el programa AEC.CMD. 
En esta fase, dependiendo de cuantos registros tenga tu 'deg.csv' tardara un poco y al acabar encontraras junto al programa AEC.CMD un nuevo archivo llamado 'DEG12.CSV'. Tiene las mismas lineas que el original ('Transactions.csv') sin el encabezamiento y con una ultima linea. Pero ahora los registros estan ordenados por ISIN y FECHA/HORA.

Poco despues se abre una pantalla alargada bajo tu browser (VENTANA DE DATOS), en los dos dedos de espacio que han quedado.

Ya tenemos las tres ventanas en su posicion.

IMPORTANTE: Las proximas veces que inicies el programa, si el archivo DEG12.CSV ya se encuentra junto al programa AEC.CMD, se saltara la fase que hemos visto, creara la VENTANA DE DATOS e ira directamente al primer registro. Sera mucho mas rapido, instantaneo.

3.1 VENTANA DE DATOS
Observa la ventana de abajo, VENTANA DE DATOS:

3.1.1 Botones:

'Prox Registro' 
	Presionando este boton cargara el siguiente registro.

'INTROD: press+Raton 1er Box' 
	Presionalo y delplaza el mouse para el 1er campo de la ficha. Abandona el mouse. AEC va a rellenar uno por uno los campos. Mas detalles abajo.

'Regis Previo'
  Retrocede al registro previo (si lo hubiere).

'Introd ISIN y NOMBRE'
	Introduce los dos valores en la ficha correspondiente del programa CARTERA.

'BUSCA'
  Si introduces una secuencia del ISIN que buscas y presionas saltara al primer registro de ese ISIN.

'+Rapido' '+Lento'
	Es posible acelerar o decelerar la velocidad con que AEC.CMD introduce los datos. La conexion con la AEAT es un tanto variable. Si una velocidad funciona bien en una ficha puedes acelerar un poco para la proxima y verificar el resultado. Si te da algun problema (mete mal los datos), desacelera, limpia la ficha abierta en CARTERA e INTRODUCE de nuevo.

'Ir al Registro >>'
	Si colocas en el campo al lado el numero de registro al que quieres ir y presionas 'Ir al Registro', va directo a este registro.

'Avanza +10 Regs' '+50 Regs' '-10 Regs'
	El programa, al reiniciarse, va al registro 1. Con los botones puedes avanzar o retrocecer hasta el registro que quieres procesar.

'TOTAL'
  Si introduces el numero de acciones que tenias el 31/12 anterior te mostrara las adquisiciones o transmiones del valor en foco sus respectivos totales. Muy util para compararlos con los que tiene CARTERA DE VALORES. 

'SALIR'
	Sale del programa.


3.1.3.Textos: significado

En el texto principal (letras mayores) te aparecen los datos del Registro que vas a introducir:

-Reg 21: es la linea 21 del archivo generado DEG12.CSV
-Nombre del valor
-ISIN del valor
-A o T: Adquisicion de valores o Transmision
-Fecha y hora de la operacion
-1 o 2: Campo 'Clave de mercado' (segun sean operaciones en el mercado nacional o europeo)
-Cuando se trata de trasmision hay otro campo que sera rellenado, 'Clave de Origen'. 
-NUM: numero de valores que se adquieren o transmiten
-Tot: valor total de la operacion
-Unit: valor unitario de cada valor
-Gas: gastos de la operacion.


En la linea secundaria, arriba, en letra menor, aparecen los datos de Registro previo, la anterior ficha que el programa ha cargado. Es util para salir de dudas si no hemos saltado algun registro (en los intradias a veces te queda duda). La fecha y hora son vitales para no perderse.


4.0 MODOS DE SALIR DEL PROGRAMA

Para salir del programa lo ideal es hacer clik en el boton 'SALIR'.Esto es muy rapido. La VENTANA DE DATOS desaparece, pero la VENTANA PERL continua en su lugar.

Tecleando (o, muy comodamente, con la flecha superior te vuelve aparecer la orden):

AEC.CMD<ENTER>

Si la ejecutas, vuelve a cargarse la VENTANA DE DATOS, en el ultimo registro visualizado.

Tambien se puede salir desde la VENTANA PERL:

ctrl C
s<enter>




5.0 TRABAJANDO EN EL PROGRAMA CARTERA DE VALORES

RECORDANDO

Crea la VENTANA PERL partiendo del link:

portableshell.bat<enter>

Redimensionala (4 dedos de ancha) y ponla arriba a la derecha. 

Introduce:

cd ae<enter>
aec.cmd<enter>

Estas en el registro 1

Redimensiona tu NAVEGADOR y entra en la AEAT, en el programa CARTERA DE VALORES.

Localiza el valor que quieres introducir (ejemplo Pharmamar).

5.1 Si el valor todavia no existe:

5.1.1) Abre la ficha NUEVO VALOR. Tiene tres posibles campos (NIF,ISIN,NOMBRE) pero solo dos son necesarios -Degiro proporciona los dos ultimos. 
5.1.2 Ve a VENTANA DATOS, haz clik en el boton 'Introd ISIN y NOMBRE'
5.1.3 Vuelve a tu NAVEGADOR y lleva el mouse dentro del campo ISIN. No lo muevas mas. AEC.COM introducira sucesivamente el ISIN y NOMBRE. Y se PARARA.
5.1.4 Verifica si esta correcto y aprieta GUARDAR en la ficha de CARTERA.
5.1.5 Todavia en CARTERA presiona en AGRUPACIONES. Crea una e introduce el % que sea de tu propiedad.

5.2 Si el valor ya existe o lo acabas de crear:

5.2.1 En CARTERA abre la AGRUPACION donde quieres introducir la nueva operacion.
5.2.2 Ve abajo al final de las operaciones  (usa la tecla FIN de tu teclado) haz clik en '+NUEVA OPERACION'. 
5.2.3 Acomoda la ficha para que veas sus 7 u 8 campos comodamente. En EDGE puedes usar el ZOOM para reducir un tanto la pantalla (75% suele ser optima).
5.2.4 Ahora ve a VENTANA DATOS y presiona el boton 'INTROD: Press+Rato 1er.Box' y acto continuo desplaza el mouse por el Browser hasta dentro del primer campo (TIPO DE OPERACION) y no lo muevas mas. AEC.CMD introducira, saltando de campo en campo: Adquisicion o Transmision, Fecha y Hora, Clave de mercado, (si es transmision, Clave de origen), Numero de titulos, Importe, Nominal unitario y Gastos. Hecho esto salta hasta GUARDAR y se para.
5.2.5 Atencion: esta operacion aun no esta guardada. Si la abandonas sera como si no existiese.
5.2.6 Ahora tu puedes verificar que los datos estan correctos:
      5.2.6.1 Si no estan correctos:
	5.2.6.1.1 Si lo unico incorrecto es la hora, limpia esa casilla y con 'Ctrl V' introduces de nuevo la Fecha y la hora. AEC ha colocado en tu clipboard la 		fecha y hora de esta operacion para facilitarte el trabajo.
	5.2.6.1.2 Si hay otros errores:
	En CARTERA haz clik en 'limpiar'. Esto elimina los datos.
	En la VENTANA DATOS disminuye la velocidad un poco con el boton '+Lento'
	Ve al punto 5.2.4 para volver a introducir los datos de nuevo. Es bueno recordar que mientras no se ha presionado GUARDAR los posibles errores no quedan 	registrados en la AEAT.
      5.2.6.2 Si la ficha ha sido introducida correctamente:
  Salva esa ficha en el programa CARTERA haciendo clik en 'GUARDAR'
  CARTERA te devuelve a la primera ficha de la agrupacion que has abierto. Usa la tecla FIN para ir al final. Ahi debe estar la operacion que acabas de introducir.
  En VENTANA DATOS aprieta el boton 'Prox Registro'. Se carga el siguiente registro.
  Verifica si es el mismo ISIN. Si lo es, en CARTERA abre otra 'Nueva Operacion' y procede como en el punto 5.2.4 de la misma forma.
  Si es otro ISIN, en CARTERA haz clik en 'Listado de valores' y busca el nuevo valor o crealo.

6.0 LIMITACIONES Y TRUCOS
Por ahora el programa introduce unicamente las operaciones de ADQUISICION y TRANSMISION. Estoy programando para ampliar a Acciones liberadas, etc.

6.1.Cuando vas a iniciar el volcado de datos en la ficha 'Nueva Operacion' y has situado el mouse en el primer campo 'Tipo de Operacion' no puedes mover mas el mouse hasta que haya introducido todos los datos y llegue a 'GUARDAR'. Si lo haces el programa aborta. Queda a la espera de repetir la operacion. Es una medida de seguridad.
Y es muy util: Si por exceso de velocidad el volcado de datos 'enloquece' y saltan pantallas que no deben, etc, moviendo  el mouse abortas el proceso. Ahora puedes limpiar la ficha, disminuir la velocidad con el boton '+Lento' y volver a rellenar la ficha.

6.2 Por razone que desconozco el programa CARTERA acepta la fecha con facilidad pero anula sistematicamente la hora y la deja a 0:00:00.
Esto es pesimo: sin la hora, las fichas introducidas seran ordenadas como a CARTERA le parezca. Pondra TRANSMISIONES delante de ADQUISICIONES, provocando un error a la hora de guardar el movimiento: IMPOSIBLE VENDER LO QUE NO TENIAS.
La solucion que he encontrado es introducir fecha y hora, saltar de campo, volver a fecha y hora, limpiar, introducirla de nuevo. En mi trabajo --ya he introducido todos mis movimientos-- la segunda vez acepta la hora correctamente.
Si en tu trabajo aun asi no acepta la hora, he puesto en tu CLIPBOARD la fecha y hora por lo que si limpias el campo y aplicas 'Ctrl V' tendras fecha y hora introducidas. Suerte


6.3 Socorro: he apretado el boton 'introducir...' pero me he olvidado de abrir la ficha en CARTERA.... 
No, no te dara tiempo a abrirla. Hay que abrirla antes y solo despues hacer clik en el boton 'INTRODUCIR' e ir al primer campo. 
Que hacer???? 
Si llevas el  mouse al terreno del browser, AEC.CMD intentara introducir datos, abriendo ventanas inconvenientes. Pero si vas moviendo el mouse, en seguida para y aborta. Haz click en el browser y va moviendo el mouse.
Si no has salido de la VENTANA DE DATOS todavia, no subas el mouse. Dirigelo por abajo hacia la derecha al maximo, al final sube hacia la VENTANA PERL, haz click, Ctrl C y el programa se parara. Aunque hagas clik en el boton introducir, mientras no penetres en el terreno del browser no introducira datos.



7.0 DESINSTALACION

Recuerdo que en realida el programa no se instala. Si no lo quieres mas, simplemente borra directorios que has creado (c:\p\ en nuestro ejemplo). En tu computador no quedara nada mas.



Es todo por ahora. Espero que te ayude en tu trabajo.

Quejas, consultas, observaciones:

Francisco A. Barrau

pitalpitoke@gmail.com

========================================


Todos los derechos reservados a Francisco A Barrau

Se prohibe distribuir, reproducir o modificar este programa sin autorizacion.

Este programa no es FreeWare, no es gratuito.
1) Este programa es "CafeWare": usalo cuanto quieras durante el 2022 pero por favor si te resulta util comprame un cafe: 

2 euros (dos euros).

(los programas que hago son mi unico gana-pan).

Hazme un traspaso a mi cuenta en Openbank:
ES4200730100550656454041
(si quieres ayudar mas, muchas gracias)

No traspases NADA hasta que finalices tu trabajo. Si te ha resultado util, paga. Si no, no pagues.

Y si tu situacion economica es mala, intentas ahorrar....
no pagues. Si en el futuro mejora...

2) Ademas te pido comentar en redes tu experiencia. Si muchos colaboran un poquito puedo sobrevivir y seguir programando.

A todos los que colaboren y me comunique en mi email los datos del deposito les enviare las actualizaciones y mejoras.

Ayudame a continuar programando y 'te ayudaras' en futuras declaraciones de la renta.

Se admiten sugerencias o criticas. Tambien puedo adaptar los programas a tus necesidades.

Gracias.

Disclaimer: Atencion. Este programa es esperimental. No me responsabilizo de los males que pueda ocasionar en tu computador. Usa este programa bajo tu responsabilidad, tu asumes los riesgos y males ocasionados. (Aunque francamente no creo haga nada de grave).

