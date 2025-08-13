
# Generador EPIC/STORY (GitHub Pages)

Sitio estático que convierte tu Excel de entregables en **EPIC.csv** y luego toma tu export de Jira para producir **STORY.csv**. Todo se ejecuta **en el navegador** con Pyodide (pandas + openpyxl). No requiere backend, ideal para **GitHub Pages**.

## Uso
1. Escribe el valor **Key Iniciative** (se asigna a `key_Activity` y se usa como `Parent` de los EPIC).
2. Arrastra el Excel (`.xlsx`) con la hoja `ListaControlEntregables` al Paso 1. Se generará **EPIC.csv**.
3. Haz clic en “Continuar al Paso 2” y arrastra el export de Jira (`.csv`) que contenga las columnas `Summary`, `Issue key` y `Parent key`. Se generará **STORY.csv**.

## Publicación en GitHub Pages
1. Crea un repositorio nuevo (por ejemplo `generador-csv-jira`).
2. Sube este `index.html` a la raíz del repo (y este README si quieres).
3. Ve a **Settings → Pages**, elige la rama (por ejemplo `main`) y la carpeta `/root`.
4. Guarda y espera a que se publique. Obtendrás una URL pública.

## Notas
- El Excel debe tener la hoja **ListaControlEntregables** y la columna **ETAPAS**. Las filas **sin** `Checklist` se interpretan como **EPIC** y las **con** `Checklist` como **STORY** (se limpia el texto).
- En el Paso 2, se reemplaza el `Parent` de cada Story por el **Issue key** del Epic correspondiente, buscando coincidencias por `Summary` y validando que el `Parent key` del CSV de Jira sea igual al `key_Activity` proporcionado.
- Todo corre localmente en tu navegador; los archivos nunca salen de tu equipo.
