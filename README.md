# Catalogo de leches

Aplicacion web estatica para catalogar productos lacteos por categoria, marca y codigo EAN-13.

## Archivos

- `index.html`: estructura principal.
- `styles.css`: estilos responsive mobile-first.
- `app.js`: datos, imágenes, filtros y generador SVG EAN-13.

## Uso

Abre `index.html` en el navegador o sube la carpeta completa a GitHub Pages.

## Datos

Los productos incluidos tienen codigo EAN-13 validado mediante digito de control.

## Imágenes

Cada registro de `productos` contiene `url_imagen`. Admite una URL directa
HTTPS o una ruta local como `images/pascual-entera.webp`. Si está vacía o
falla, la tarjeta muestra un placeholder. Pascual entera incluye una URL de
ejemplo.

Las tarjetas mantienen una imagen de tamaño uniforme a la izquierda y la
información con el SVG a la derecha. Los textos largos se limitan visualmente
para conservar la misma altura; el contenido completo permanece en `title`.

## Generador temporal

El botón `Generar un código EAN-13` abre el formulario dentro del mismo
`index.html`. Acepta exactamente 13 dígitos y utiliza la misma función SVG del
catálogo. El resultado no se añade a `productos` ni se almacena; desaparece al
cerrarlo, al generar otro o al recargar la página.

El contador indica cuántos de los 13 dígitos se han introducido. Tanto los
códigos del catálogo como el temporal pueden tocarse para ampliarlos.
Al pulsar `Enter/Ir` desde el teclado móvil se envía el formulario, se genera
el SVG y el campo pierde el foco para cerrar el teclado automáticamente.

El campo usa `type="text"` sin `inputmode="numeric"` para no forzar el teclado
numérico reducido de iOS. Es compatible con las herramientas de dictado o
escaneo de texto que ofrezca el teclado del dispositivo; su disponibilidad
depende del sistema. JavaScript elimina caracteres no numéricos y limita el
valor a 13 cifras. No incluye OCR propio, cámara, backend, dependencias ni una
segunda página.

Después de generar correctamente, se ocultan la cabecera, los filtros, las
marcas y el catálogo. Permanecen el formulario y el SVG temporal hasta pulsar
`Volver al catálogo`.

El tema sigue la preferencia del sistema y puede alternarse manualmente durante
la sesión. El selector no guarda información.
