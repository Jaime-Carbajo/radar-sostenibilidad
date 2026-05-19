# Radar de Sostenibilidad Calidalia — guía de puesta en marcha

Este repositorio contiene el sitio completo, ya con la marca Calidalia. Tiene
dos partes:

1. **El sitio** (GitHub Pages + Jekyll): la estructura ya está programada. No
   hay que volver a tocar código para publicar contenido.
2. **El editor** (Pages CMS): donde las personas sin perfil técnico crean
   radares y noticias rellenando formularios. Sin Git, sin Markdown, sin código.

---

## PARTE A — Configuración inicial (se hace UNA sola vez)

> La hace una persona con cuenta de GitHub (tú). Tiempo: ~20-30 min.

### Paso 1. Crear el repositorio
1. Entra en GitHub con la cuenta/organización **calidalia**.
2. Crea un repositorio **nuevo**, **público**, llamado exactamente:
   **`radar-sostenibilidad`**
   (Recomiendo uno nuevo y dedicado, no reutilizar el actual, para que las
   URLs sean limpias y estables.)
3. No añadas README ni .gitignore desde GitHub (ya vienen incluidos).

> Si usas otro nombre de repo, abre el archivo `_config.yml` y cambia la línea
> `baseurl: "/radar-sostenibilidad"` poniendo `/el-nombre-de-tu-repo`.
> Si algún día pones un dominio propio, esa línea debe quedar `baseurl: ""`.

### Paso 2. Subir los archivos
1. Descomprime el ZIP que te he entregado. Verás carpetas como `_layouts`,
   `_radares`, `assets`, y archivos como `_config.yml` y `.pages.yml`.
2. En tu repo vacío: botón **Add file → Upload files**.
3. Arrastra **todo el contenido** de la carpeta descomprimida (incluidos los
   archivos que empiezan por punto, como `.pages.yml`).
4. Abajo, en "Commit changes", pulsa **Commit changes**.

### Paso 3. Activar GitHub Pages
1. En el repo: **Settings → Pages**.
2. En "Build and deployment", **Source: Deploy from a branch**.
3. Branch: **main** y carpeta **/ (root)**. Guarda (**Save**).
4. Espera 1-3 minutos. GitHub mostrará la dirección pública, será:
   **`https://calidalia.github.io/radar-sostenibilidad/`**
5. Ábrela. Debes ver el sitio con dos radares de ejemplo.

### Paso 4. Conectar el editor visual (Pages CMS)
1. Entra en **https://app.pagescms.org** e inicia sesión con la cuenta de
   GitHub de **calidalia**.
2. Autoriza el acceso **solo al repositorio `radar-sostenibilidad`**.
3. El proyecto aparecerá en la lista. Ábrelo: verás "Radares",
   "Subsecciones / Noticias" y "Ajustes del sitio".

### Paso 5. Invitar a los editores (sin que necesiten cuenta de GitHub)
1. Dentro del proyecto en Pages CMS, ve a la gestión de colaboradores
   (**Settings / Collaborators**).
2. Invita por **email** a cada persona que vaya a editar.
3. Recibirán un acceso por enlace mágico al email. **No necesitan cuenta de
   GitHub ni saber nada técnico.**

A partir de aquí, la configuración está terminada y no hay que repetirla.

---

## PARTE B — Cómo se publica contenido (lo hacen los editores)

> Todo desde **https://app.pagescms.org**, sin tocar este repositorio.

### Crear un radar nuevo
1. Abre el proyecto → sección **Radares** → **Add an entry**.
2. Rellena: **Número** (p. ej. 7), **Título**, **Mes de publicación**,
   **Introducción** (opcional).
3. Deja **Publicado** activado y pulsa **Save**.

### Añadir noticias a ese radar
1. Sección **Subsecciones / Noticias** → **Add an entry**.
2. **Número del Radar al que pertenece**: el mismo número del radar (p. ej. 7).
3. **Orden**: 1, 2, 3… (el orden en que se listan dentro del radar).
4. **Título** y **Contenido** (editor visual: negritas, listas, enlaces,
   imágenes, tablas).
5. Opcional: adjuntar un **PDF** o un **enlace externo**.
6. **Save**.

En 1-2 minutos el contenido está publicado en la web.

### Obtener el enlace para Zoho Campaigns
1. En la web pública, abre la noticia.
2. Al final hay un recuadro **"Enlace para la newsletter"** con botón
   **Copiar enlace**.
3. Pega ese enlace en el resumen correspondiente de Zoho Campaigns.

### Regla única importante (para que los enlaces no se rompan)
- El **Número del Radar** y el **Título de la noticia** definen la dirección
  web. Una vez que has enviado un enlace por Zoho, **no cambies el título de
  esa noticia ni el número del radar**. El texto del contenido sí se puede
  editar libremente; la dirección no cambia.
- Si necesitas corregir un título ya enviado, cambia el texto dentro del
  contenido, no el campo "Título".

---

## Notas técnicas (para quien mantenga el sitio)

- **Tipografía:** la corporativa es Gill Sans MT (licencia Monotype, no
  incrustable para lectores externos). El sitio la usa si está instalada y,
  si no, aplica una alternativa humanista próxima (Hanken Grotesk). Si se
  adquiere licencia web de Gill Sans MT, se sustituye en `assets/css/style.css`
  y `_includes/head.html`.
- **Colores:** azul `#003057`, amarillo `#FFD100`, blanco `#FFFFFF`
  (definidos en `assets/css/style.css`).
- **Modelo de URL:** cada noticia es una página propia con dirección estable
  (`/r/...`); el radar es la página que las agrupa (`/radar/Nº/`). No se usan
  anclas, así los enlaces enviados sobreviven a reordenaciones.
- **Build:** GitHub Pages compila Jekyll automáticamente en cada cambio. Si un
  cambio no aparece, revisa **repo → pestaña Actions / Pages** por si el build
  falló.
- **Dependencia externa:** el editor usa app.pagescms.org (gratuito, open
  source). Es autoalojable en Vercel si algún día se quiere eliminar esa
  dependencia.
