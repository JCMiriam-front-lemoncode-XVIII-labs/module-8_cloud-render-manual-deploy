# Lemon Orbit: despliegue manual en Render

## Objetivo de la práctica

Preparar Lemon Orbit para publicarlo como Static Site en Render y realizar las actualizaciones mediante despliegues manuales. La aplicación es una web estática en HTML, CSS y JavaScript sin dependencias.

## Pasos seguidos

1. Se revisó la estructura del proyecto y se identificaron los archivos públicos `index.html`, `styles.css` y `script.js`, situados en la raíz.
2. Se eligió un Static Site como tipo de servicio, ya que la aplicación no necesita un servidor propio ni un contenedor.
3. Se definió el comando de construcción `mkdir -p dist && cp index.html styles.css script.js dist/`, que prepara una carpeta con los tres archivos que se publicarán.
4. Se estableció `dist` como directorio de publicación previsto.
5. Se definió la rama `main` como origen y **Auto-Deploy: Off** para que las actualizaciones se publiquen mediante una acción manual en Render.
6. Se comprobó localmente la sintaxis JavaScript mediante `node --check`, pasando el contenido de `script.js` por la entrada estándar. La comprobación terminó correctamente.

El comando de construcción está preparado para el entorno Linux de Render. No requiere instalar paquetes. `.nojekyll` se conserva como archivo heredado de GitHub Pages y no forma parte de los archivos que se publicarán.

## Configuración definida para Render

Se documentaron los siguientes valores para la creación del sitio mediante **New → Static Site**, conectado al repositorio de GitHub:

| Campo | Valor previsto |
| --- | --- |
| Name | `module-8_cloud-render-manual-deploy` |
| Branch | `main` |
| Root Directory | Vacío, con el proyecto en la raíz del repositorio |
| Build Command | `mkdir -p dist && cp index.html styles.css script.js dist/` |
| Publish Directory | `dist` |
| Auto-Deploy | Off |

Esta configuración todavía no se ha aplicado en el panel de Render. El sitio no necesita comando de arranque ni configuración de puerto.

## Flujo de actualización definido

Se estableció que los cambios se guardarán mediante commit y push a `main`. Con el despliegue automático desactivado, su publicación se iniciará desde **Manual Deploy → Deploy latest commit** en Render.

La verificación de cada despliegue incluirá la revisión de **Events** y los logs de construcción, la apertura de la URL pública y la comprobación de los controles y de la carga de CSS y JavaScript. Se identificaron también las opciones **Deploy a specific commit** para publicar un commit concreto y **Clear build cache & deploy** para reconstruir sin caché.

## URL del sitio

[Abrir Lemon Orbit en Render](https://module-8-cloud-render-manual-deploy.onrender.com)
