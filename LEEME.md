# Dos Calles

App de entrenamiento para dos perfiles: plan de natación, registro de sesiones,
estimación de calorías y seguimiento de peso. Se instala en el iPhone y funciona
sin conexión. Todos los datos se guardan en el propio móvil.

## Ficheros

| Fichero | Para qué |
|---|---|
| `index.html` | La app entera: interfaz, planes y lógica |
| `manifest.webmanifest` | Nombre, icono y modo pantalla completa |
| `sw.js` | Service worker: hace que funcione sin conexión |
| `icon-*.png`, `apple-touch-icon.png` | Iconos |
| `.nojekyll` | Necesario para que GitHub Pages sirva los ficheros tal cual |

## Publicarlo en GitHub Pages

1. En github.com, **New repository**. Nombre: `dos-calles`. Marca **Public**
   (Pages gratuito requiere repositorio público). Crea el repositorio.
2. En el repositorio vacío: **uploading an existing file**. Arrastra **todos**
   los ficheros de esta carpeta (los ficheros, no la carpeta). Confirma con
   **Commit changes**.
3. **Settings → Pages**. En *Source* elige **Deploy from a branch**, rama `main`
   y carpeta `/ (root)`. Guarda.
4. Espera un minuto y recarga esa página: aparecerá la dirección, con la forma
   `https://<usuario>.github.io/dos-calles/`.

El fichero `.nojekyll` puede no verse al arrastrarlo porque empieza por punto.
Si tu sistema lo oculta, no pasa nada: sin él también funciona en este caso.

## Instalarlo en el iPhone

1. Abre esa dirección **en Safari** (no en Chrome: en iOS solo Safari puede
   instalar en la pantalla de inicio).
2. Botón **Compartir** → **Añadir a pantalla de inicio** → **Añadir**.
3. Ábrelo desde el icono nuevo. Se abre a pantalla completa, sin barra de Safari.

Repite lo mismo en el otro móvil. Cada teléfono guarda sus propios datos.

Al abrirla por primera vez, ve a **Perfil**, pon nombre, altura y peso, y
guarda. Cambia arriba al otro perfil y haz lo mismo.

## Actualizarla

Sube el `index.html` nuevo al repositorio y **sube el número de versión en
`sw.js`** (la línea `const CACHE = 'dos-calles-v1';` pasa a `v2`, `v3`...). Sin
ese cambio los móviles seguirán abriendo la versión guardada en caché.

## Editar la rutina

Cada sesión se puede editar desde **Plan → Editar sesión**: renombrarla, cambiar
de día, ajustar minutos e intensidad, y añadir, reordenar, editar o eliminar
ejercicios. También puedes crear sesiones nuevas en cualquier día.

De cada ejercicio se puede editar el nombre, las series, el descanso, el
material, el texto de "cómo se hace", la búsqueda de vídeo y un enlace propio.

En **Perfil → Revisión de la rutina** eliges cada cuántas semanas quieres que la
app te recuerde revisarla. Cuando toque, aparece un aviso en la pestaña Hoy.

Si te lías, **Perfil → Restablecer rutina original** devuelve los ejercicios al
plan de partida sin borrar tus sesiones registradas ni el peso.

## Los vídeos

Cada ejercicio tiene un botón que abre YouTube con una búsqueda ya escrita. Se
hace así a propósito: un enlace fijo a un vídeo concreto se rompe cuando el
canal lo borra, y no hay material libre de derechos para los ejercicios de
natación.

Cuando encuentres un vídeo que te convenza, pega su enlace en el campo **Enlace
propio** de la ficha del ejercicio. A partir de entonces el botón abrirá ese
vídeo directamente. Acepta también la dirección de un GIF.

## Copia de seguridad

En **Perfil → Copia de seguridad** hay un botón para exportar todo a un fichero
JSON y otro para restaurarlo. La copia incluye también tu rutina editada.

Hazlo de vez en cuando. iOS borra el almacenamiento de las apps web que se usan
poco cuando el teléfono va justo de espacio, y esa es la única forma de que se
pierdan los datos. Guardar el fichero en iCloud Drive es suficiente.

## Cómo se calculan las calorías

`kcal = MET × peso en kg × horas`

Los valores MET vienen del Compendium of Physical Activities: natación a crol
suave 5,8; a crol rápido y vigoroso 9,8; espalda en entrenamiento 10,3;
calistenia moderada 3,8. A cada sesión se le asigna un valor intermedio,
ajustado a la baja porque parte del tiempo se pasa parado en la pared, y se
multiplica por 0,85 / 1 / 1,15 según el esfuerzo que marques.

**Es una estimación, no una medición.** El gasto real depende de la técnica, la
temperatura del agua y la eficiencia de cada persona, y puede desviarse un
20-30 %. Sirve para comparar tus semanas entre sí, no como cifra absoluta.
