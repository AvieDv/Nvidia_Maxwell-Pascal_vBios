# Nvidia Maxwell MXM en macOS/Windows
Maxwell es la arquitectura de próxima generación de NVIDIA para aplicaciones informáticas CUDA. Maxwell presenta un diseño completamente nuevo para Streaming Multiprocessor (SM) que mejora drásticamente la eficiencia energética. Las mejoras para controlar la partición lógica, el equilibrio de la carga de trabajo, la granularidad de activación del reloj, la programación basada en el compilador, la cantidad de instrucciones emitidas por ciclo de reloj y muchas otras mejoras permiten que Maxwell SM (también llamado SMM) supere con creces la eficiencia de Kepler SMX.

Maxwell retiene y amplía el mismo modelo de programación CUDA que en las arquitecturas anteriores de NVIDIA, como Fermi y Kepler, y las aplicaciones que siguen las mejores prácticas para esas arquitecturas normalmente deberían ver aceleraciones en la arquitectura Maxwell sin ningún cambio de código.

La arquitectura Maxwell se introdujo en modelos posteriores de la serie GeForce 700 y también se utiliza en la serie GeForce 800M, la serie GeForce 900 y la serie Quadro Mxxx, así como en algunos productos Jetson, todos fabricados con el proceso de 28 nm de TSMC.

Los primeros productos basados en Maxwell fueron GeForce GTX 745 (OEM), GeForce GTX 750 y GeForce GTX 750 Ti. Ambos fueron lanzados el 18 de febrero de 2014, ambos con el número de código de chip GM107. Las GPU de la serie GeForce 700 anteriores habían utilizado chips Kepler con los números de código GK1xx. Las GPU Maxwell de primera generación (números de código GM10x) también se utilizan en las series GeForce 800M y Quadro Kxxx. El 18 de septiembre de 2014 se presentó una segunda generación de productos basados en Maxwell con la GeForce GTX 970 y la GeForce GTX 980, seguida de la GeForce GTX 960 el 22 de enero de 2015, la GeForce GTX Titan X el 17 de marzo de 2015 y la GeForce GTX 980 Ti el 1 de junio de 2015. La tarjeta Maxwell 2.0 final y con la especificación más baja fue la GTX950 lanzada el 20 de agosto de 2015. Estas GPU tienen números de código de chip GM20x.

# Chips
GM200
GM204
GM206

# Nvidia PASCAL MXM en macOS/Windows
La arquitectura se introdujo por primera vez en abril de 2016 con el lanzamiento de Tesla P100 (GP100) el 5 de abril de 2016 y se usa principalmente en la serie GeForce 10, comenzando con GeForce GTX 1080 y GTX 1070 (ambas con GPU GP104), que fueron lanzados el 17 de mayo de 2016 y el 10 de junio de 2016 respectivamente. Pascal se fabricó utilizando el proceso FinFET de 16 nm de TSMC, y luego el proceso FinFET de Samsung de 14 nm.



# Chips
GP100: el acelerador de GPU Nvidia Tesla P100 está dirigido a aplicaciones GPGPU como FP64 de cómputo de doble precisión y capacitación de aprendizaje profundo que utiliza FP16. Utiliza memoria HBM2. 
Quadro GP100 también utiliza la GPU GP100.
GP102: esta GPU se utiliza en TITAN Xp, Titan X2 y GeForce GTX 1080 Ti. También se utiliza en Quadro P60002 y Tesla P40.2
GP104: Esta GPU se utiliza en las GeForce GTX 1070, GTX 1070 Ti y GTX 1080. La GTX 1070 tiene 15/20 y la GTX 1070 Ti tiene habilitados 19/20 de sus SM. Ambos están conectados a la memoria GDDR5, mientras que la GTX 1080 es un chip completo y está conectado a la memoria GDDR5X. También se utiliza en Quadro P5000, Quadro P4000 y Tesla P4.
GP106: esta GPU se utiliza en la GeForce GTX 1060 con memoria GDDR5/GDDR5X.
También se utiliza en la Quadro P2000.
GP107: esta GPU se usa en GeForce GTX 1050 Ti y GeForce GTX 1050. También se utiliza en Quadro P1000, Quadro P600, Quadro P620 y Quadro P400.
GP108: esta GPU se utiliza en GeForce GT 1010 y GeForce GT 1030.
En el chip GP104, un SM consta de 128 ALU de precisión simple ("núcleos CUDA"), en el GP100 de 64 ALU de precisión simple. Debido a la diferente organización de los chips, como el número de ALU de doble precisión, el rendimiento teórico de doble precisión de la GP100 es la mitad del rendimiento teórico de precisión simple; la relación es 1/32 para el chip GP104.

# Rendimiento y funciones en Windows 10-11

Desafortunadamente, Apple nunca admitió estas tarjetas en las versiones más recientes de macOS. En caso de que planee usar una GPU de este tipo, deberá instalar los llamados controladores web de NVIDIA para obtener soporte para High Sierra.


Por otro lado, estas GPU son perfectamente capaces de ejecutar Windows y probablemente alguna distribución de Linux con soporte completo para controladores.

La potencia teórica de procesamiento de precisión simple de una GPU Maxwell en FLOPS se calcula como 2 (operaciones por instrucción FMA por núcleo CUDA por ciclo) × número de núcleos CUDA × velocidad de reloj del núcleo (en Hz).

La potencia teórica de procesamiento de doble precisión de una GPU Maxwell es 1/32 del rendimiento de precisión simple (que se ha señalado como muy bajo en comparación con la generación anterior de Kepler).


# Para admitir tarjetas Maxwell y Pascal en el iMac 2009-2011.

Las tarjetas Maxwell y Pascal no funcionarán con aceleración en MacOS más allá de High Sierra debido a la falta de compatibilidad con controladores, pero funcionarán perfectamente bien en Windows y Linux.

Todas las tarjetas MXM-B admitidas actualmente requieren el iMac de 27'' con disipador de calor de 3 tubos modificado (pulido y modificado) correctamente.


Todas las tarjetas Maxwell y Pascal requieren vbios flashing para funcionar en el iMac.
En las tarjetas Maxwell, esto se puede hacer desdewindows o linux usando un nvflash parcheado.
En las tarjetas Pascal, se requiere un programador de hardware para colocar el chip eeprom en la tarjeta para flashear a 1.8v. 
Puede usar un programador simple basado en ch341a con adaptador de voltaje y un flashrom parcheado en Linux o AsProgrammer / NeoProgrammer en Windows.

Las tarjetas funcionarán en MacOS hasta High Sierra (usando los controladores web de Nvidia ) y son totalmente compatibles con Windows y Linux. El control de despertar, dormir y brillo funciona bien.

Necesitará un Opencore/OCLP correctamente configuradopara habilitar la pantalla en el arranque, tener control de brillo en MacOS, tener un selector de arranque emulado y habilitar la salida de altavoces internos en UEFI Windows.

El control de brillo en Windows requiere un parche regedit después de instalar los controladores de Nvidia.

Algunas tarjetas tienen más de un ROM para vBios disponible, generalmente con una versión overclockeada.
Las versiones overclockeadas de Pascal son muy seguras, ya que "gpu boost" evita el sobrecalentamiento reduciendo los relojes y la potencia según sea necesario.

* La tarjeta P3200/P4200 en iMac 12,2 necesita un truco de aislamiento de smbus para funcionar correctamente. Además, la mayoría de las tarjetas vienen sin el chip eeprom soldado a bordo (tiene que soldar uno o pedirle al vendedor que lo haga por usted).

** HP Turing T1000 necesita un mod de retroiluminación de hardware para habilitar la retroiluminación y no hay controladores macOS para ello.

Otras tarjetas de interés que deberían funcionar: HP Turing RTX 3000 y RTX 4000.


![71CoFDN88eL _AC_SY355_](https://github.com/AvieDv/Nvidia_Maxwell_vBios/assets/43917721/1d2bf947-cf86-4150-93c8-5fa216fdf575)

