# Caja parametrica de cinco caras - ensamble sin pegamento

**Actividad:** Proyecto de Ingenieria I, caja parametrica con finger joints  
**Estado:** diseno 2D preparado para corte y ensamble de prueba; aun no se ha cortado ni medido el material.

## Proposito

La caja se corta como cinco piezas planas y se arma en 3D con uniones de dedos. Las lenguetas de una cara entran en las ranuras de la cara contigua, por lo que el objetivo es un ensamble mecanico sin pegamento. La parte superior queda abierta. El frente lleva un corte triangular de 26 x 22 mm inspirado en la señal de advertencia del prototipo S6; es una abertura simbolica y su medida se puede ajustar en el generador.

## Medidas y parametros

| Parametro | Valor de partida | Nota |
|---|---:|---|
| Ancho objetivo | 80 mm | Medidas nominales indicadas en la consigna |
| Alto objetivo | 60 mm | Medidas nominales indicadas en la consigna |
| Fondo objetivo | 50 mm | Medidas nominales indicadas en la consigna |
| Frente y fondo | 80 x 60 mm | El frente incluye una ventana triangular 26 x 22 mm para el simbolo de advertencia S6; medida provisional |
| Laterales | 50 x 60 mm | Dos piezas |
| Base | 80 x 50 mm | Una pieza |
| Espesor | 3.00 mm nominal | Medir el MDF real con vernier antes de cortar |
| Kerf | 0.20 mm inicial | Medir con `kerf.dxf` y actualizar el parametro |
| Dedos por arista de union | 3 | La orilla superior permanece abierta |
| Holgura objetivo | 0.10 mm | Valor de ajuste inicial; depende del corte real |
| Separacion entre piezas en DXF | 3 mm | Segun la consigna |

**Calculo parametrico:** para una arista de longitud `L` con 3 dedos, el paso/ancho nominal es `L / (2 x 3)`. La ranura en el DXF se calcula como `ancho_dedo - 2 x kerf + holgura`; la profundidad del dedo se ajusta al espesor. Al cambiar ancho, alto, fondo, espesor o kerf en `caja_parametrica.py` y volver a ejecutarlo, se regeneran ambos DXF y la vista.

Para `kerf = 0.20 mm` y holgura objetivo `0.10 mm`, los anchos nominales de dedo son 13.333 mm en aristas de 80 mm, 10.000 mm en aristas de 60 mm y 8.333 mm en aristas de 50 mm. El ancho de ranura CAD calculado es 13.033, 9.700 y 8.033 mm respectivamente. Son valores iniciales: el kerf real del equipo puede requerir ajustar las ranuras para que el ensamble quede firme sin forzar ni usar adhesivo.

## Archivos

- `kerf.dxf`: contorno de 100 x 20 mm y nueve lineas interiores unicas, que forman diez secciones de 10 x 20 mm. Sirve para medir el kerf real.
- `caja.dxf`: las cinco siluetas cerradas, separadas 3 mm, mas la ventana triangular de la cara frontal; no contiene cotas ni texto.
- `caja_parametrica.py`: fuente parametrica que genera DXF y vista; edita `PARAMS` para recalcular la geometria.
- `caja-vista-parametros.png`: vista generada del diseno 2D con dimensiones y parametros. Es una visualizacion del script, no una captura de un programa CAD ni evidencia de corte.

## Ensamble y validacion

1. Medir con vernier el espesor real de la placa de MDF y actualizar `thickness`.
2. Cortar primero `kerf.dxf` despues de completar la induccion de seguridad del IDIT; medir y calcular el kerf real segun el procedimiento indicado en clase.
3. Actualizar `kerf`, regenerar los DXF y revisar que las cinco caras sigan separadas.
4. Cortar las piezas y probar las uniones de dedos. Si quedan flojas o no entran, corregir holgura y volver a exportar antes de cortar la caja.
5. Ensamblar base, frente, fondo y laterales con las lenguetas y ranuras; no aplicar pegamento.
6. Registrar aqui el espesor medido, kerf, cambios finales y dificultad observada despues de la prueba fisica.

**Medicion real del MDF:** pendiente.  
**Kerf medido:** pendiente de la prueba.  
**Dificultad observada al ensamblar:** pendiente de fabricar y probar.  
**Seguridad:** no operar la cortadora sin la induccion del IDIT y supervision requerida.

## Declaracion de uso de IA

Se utilizo ChatGPT para generar el borrador parametrico de las geometrias DXF, la tira de kerf y la visualizacion inicial. El estudiante debe revisar las medidas y el archivo en el software CAD del laboratorio, medir el material y el kerf real, ajustar el ensamble, realizar la prueba fisica y actualizar este registro con sus resultados. La imagen es una vista generada, no una captura de CAD ni evidencia de fabricacion.
