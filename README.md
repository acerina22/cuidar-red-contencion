# Cuid.ar — Red de Contención Argentina

Sitio estático inicial para pruebas. Publica la interfaz desde `index.html`.

## Estructura

- `index.html`: página responsiva y buscador.
- `assets/cuidar-logo.svg`: símbolo de Cuid.ar.
- `data/instituciones.json`: directorio local de instituciones.

## Directorio de instituciones

El archivo `data/instituciones.json` contiene un array JSON. Está vacío en la primera versión para no publicar datos inventados.

Los desplegables de provincia y localidad utilizan la API Georef de Datos Argentina (`https://apis.datos.gob.ar/georef/api`), que ofrece el catálogo geográfico oficial de provincias y localidades. CABA se muestra separada de la Provincia de Buenos Aires. Si la API geográfica no está disponible, queda una lista de respaldo de las jurisdicciones y la persona puede recurrir a Google Maps. Cada registro puede seguir este esquema:

```json
[
  {
    "name": "Nombre de la institución",
    "type": "Hospital o guardia",
    "situations": ["Crisis emocional o riesgo de suicidio"],
    "address": "Calle y número",
    "locality": "Localidad",
    "city": "Ciudad",
    "province": "Provincia",
    "lat": -34.60,
    "lon": -58.38,
    "phone": "Número oficial",
    "website": "https://sitio-oficial.gob.ar",
    "source": "https://fuente-oficial.gob.ar",
    "verifiedAt": "AAAA-MM-DD"
  }
]
```

Cargar solo instituciones reales, con fuente y fecha de verificación. Los teléfonos, horarios, cobertura geográfica y criterios de acceso deben contrastarse con fuentes oficiales antes de mostrar un recurso como confirmado.

## Publicación en Render

Crear un **Static Site** enlazado a este repositorio:

- Branch: `main`
- Root Directory: dejar vacío
- Build Command: vacío
- Publish Directory: `.`

No necesita backend para servir esta primera versión. Las búsquedas del directorio consultan `data/instituciones.json`; como está vacío, no se mostrarán establecimientos propios hasta cargar registros verificados. Google Maps es una alternativa externa, no el directorio verificado de Cuid.ar. Una búsqueda externa puede mostrar resultados incompletos o no verificados; no debe presentarse como listado oficial de Cuid.ar.

## Límites y seguridad

- Geolocalización solo tras acción y permiso explícitos de la persona.
- No se guardan las coordenadas de quien visita en esta versión.
- No introducir datos personales de personas que pidan ayuda.
- Salida rápida y teléfonos de emergencia deben probarse en escritorio y móvil antes de difundir.
