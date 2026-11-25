# Electro Pro — PWA v3.12

Aplicación web progresiva (PWA) preparada para publicarse en GitHub Pages. Incluye proyectos BT/MT en pestañas independientes y una interfaz adaptable a móviles.

## Novedades v3.5
- Selector de tipo de proyecto al crear: BT o MT.
- Pestañas para alternar entre proyectos abiertos; los proyectos permanecen agrupados en pestañas y se puede alternar entre ellos sin cerrar el trabajo anterior.
- En proyectos MT solo se habilitan Resumen, Datos del proyecto, Media tensión y SPT (puesta a tierra y diseño de malla).
- Interfaz móvil mejorada: pestañas desplazables, formularios táctiles y tablas con desplazamiento horizontal.

## Archivos
- `index.html`: aplicación Electro Pro.
- `manifest.webmanifest`: nombre, iconos y configuración de instalación.
- `sw.js`: service worker y caché para uso sin conexión (caché v3.12).
- `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`: iconos de la aplicación.
- `icon-maskable-192.png`, `icon-maskable-512.png`: iconos maskable para Android (logo dentro de la zona segura).

## Publicar en GitHub Pages
1. Crea un repositorio en GitHub (por ejemplo, `electro-pro`).
2. Sube **todos los archivos de esta carpeta** a la raíz del repositorio.
3. En GitHub abre **Settings → Pages**.
4. En **Build and deployment**, selecciona **Deploy from a branch**.
5. Selecciona la rama `main` y la carpeta `/ (root)`, luego guarda.
6. Espera a que GitHub Pages publique el sitio. La dirección será similar a:
   `https://TU-USUARIO.github.io/electro-pro/`
7. Abre esa dirección en Chrome. En Android usa el menú ⋮ → **Instalar aplicación** o **Agregar a pantalla principal**.

## Importante
- La instalación PWA requiere HTTPS. GitHub Pages entrega HTTPS automáticamente.
- No cambies los nombres ni las rutas relativas de `manifest.webmanifest`, `sw.js` y los iconos.
- La primera visita necesita conexión para descargar la aplicación. Después, el service worker conserva los archivos principales para abrirla sin conexión.
- Los proyectos se guardan en el almacenamiento local del navegador/dispositivo. Para moverlos entre dispositivos, usa Exportar/Importar proyecto.
- Esta versión corrige defectos estructurales y de robustez detectados en una revisión estática. No constituye una certificación de los cálculos eléctricos ni reemplaza pruebas funcionales y contraste normativo en terreno.

## Actualizar la aplicación
Cuando publiques una versión nueva, cambia el valor de `CACHE_NAME` en `sw.js` para forzar la renovación de caché.


## Pruebas adicionales de v3.5
- Se corrigió la persistencia de pestañas abiertas.
- Se agregó cierre de pestaña sin borrar el proyecto guardado.
- Se aisló por proyecto el ingreso rápido de Wenner y electrodo vertical.
- Se incorporó el formateador numérico usado por los módulos de cálculo.


Actualización v3.6: se renovó el icono de Electro Pro, se añadieron iconos maskable independientes para Android y se actualizó la caché del service worker para forzar la carga de los nuevos recursos.


Versión 3.7 corregida: se conserva íntegra la lógica funcional de v3.6. Se actualizan iconos, colores del manifiesto y pantalla de inicio. La pantalla de inicio se inserta al final del documento y no modifica funciones ni cadenas de exportación.


## Cambios de validación v3.9
- Se conserva la pantalla de bienvenida de v3.8 y la base de cálculo de v3.6.
- Se eliminan lecturas Wenner y valores de resistividad ficticios en proyectos nuevos.
- El criterio de resistencia de puesta a tierra debe seleccionarse expresamente.
- El cuadro trifásico informa la corriente estimada de la fase más cargada.
- Se advierte que el ajuste de suelo de dos capas no alimenta todavía el cálculo IEEE 80.
- Se mantiene el control del límite de caída por tramo (máximo 3 %) y acumulado (máximo 5 %).

Esta versión es una herramienta de apoyo preliminar; los cálculos de malla y protecciones requieren validación de ingeniería con datos reales, fichas de fabricante y normativa aplicable.


## Cambios v3.10 (correcciones de revisión)
- Se definió `money()`: el módulo Cubicación ya no falla al agregar materiales.
- La memoria/informe ahora toma el resumen de alimentadores y el cobre de la malla.
- Cálculo de malla: se corrige el error de coma flotante en el número de conductores.
- Cuadro de cargas: la caída máxima por circuito se limita a 3 % además del 5 % total.
- Service worker: solo se guarda en caché una navegación con respuesta correcta; caché renovada.
- Iconos maskable rediseñados con margen de zona segura.
- Carga de datos e importación validan tensión, fp, sistema, listas y mallas.
- Se eliminaron definiciones duplicadas de funciones del cuadro de cargas.

## Cambios v3.11
- Al abrir la aplicación todos los campos parten vacíos (proyecto en blanco no guardado).
- Ventana de inicio con los proyectos anteriores: **Continuar** para retomarlos o **Eliminar** para borrarlos definitivamente (con confirmación). También permite crear un proyecto nuevo o importar un archivo.
- Botón «Abrir / eliminar proyectos» en la barra lateral para volver a esa ventana en cualquier momento.
- El proyecto en blanco inicial no se guarda hasta que se crea o se abre uno.

## Cambios v3.12
- Diseño de malla de tierra: la tabla de resistividad permite elegir entre **Wenner** y **Schlumberger** (ρa = π·[(AB/2)² − (MN/2)²]/MN · R). Cada método conserva sus propias lecturas.
- El ajuste de modelo de 2 capas, la curva ρa, la ρ de diseño y la memoria SPT usan el método seleccionado. Se avisa si MN > AB/5.
- Respaldos e importaciones incluyen el método y las lecturas Schlumberger.
