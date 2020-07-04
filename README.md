---
description: >-
  Documentación oficial de la API de CubaPod, la plataforma cubana de
  podcasting.
---

# Referencia de la API

## Introducción

La API de [CubaPod](https://cubapod.net) se basa en el esquema [GraphQL](https://graphql.org) y consta de distintos **tipos**, **consultas** y **mutaciones**. Existen diferentes consultas públicas que por el momento se pueden consumir sin una llave API. Explicaremos esas consultas en esta documentación.

La API se expone en el siguiente URL: [https://api.cubapod.net](https://api.cubapod.net)

## Tipos GraphQL

Los objetos que maneja la API están definidos en los siguientes tipos:

### CategoryType

`CategoryType` define una categoría bajo la cual se agrupan podcasts.

| Campo | Tipo de dato | Descripción |
| :--- | :--- | :--- |
| `name` | `String` | Nombre de la categoría |
| `slug` | `String` | Slug de la categoría |
| `description` | `String` | Descripción de la categoría |
| `img` | `String` | Imagen de portada de la categoría |

### PodcastType

`PodcastType` define un podcast.

| Campo | Tipo de dato | Descripción |
| :--- | :--- | :--- |
| `slug` | `String` | Slug del podcast |
| `url` | `String` | URL del feed RSS del podcast |
| `title` | `String` | Título del podcast |
| `subtitle` | `String` | Subtítulo del podcast |
| `image` | `String` | Imagen de portada del podcast |
| `link` | `String` | Enlace a sitio web del podcast |
| `summary` | `String` | Sumario del podcast |
| `generator` | `String` | Plataforma que genera el feed RSS |
| `author` | `String` | Autor del podcast |
| `rights` | `String` | Derechos de autor del podcast |
| `category` | `CategoryType` | Categoría del podcast |
| `itunesType` | `String` | Tipo de podcast según estándar iTunes |
| `itunesExplicit` | `Boolean` | Contiene o no lenguaje explícito |
| `hashtag` | `String` | Hashtag del podcast para redes sociales |
| `telegramHandler` | `String` | Usuario del canal de Telegram del podcast |
| `telegramURL` | `String` | URL del canal de Telegram del podcast |
| `twitterHandler` | `String` | Usuario de Twitter del podcast |
| `twitterUrl` | `String` | URL de Twitter del podcast |
| `applePodcastsUrl` | `String` | URL del perfil del podcast en Apple Podcasts |
| `episodes` | `EpisodeType[]` | Listado de episodios del podcast |
| `episodesCount` | `Int` | Cantidad de episodios del podcast |

### EpisodeType

`EpisodeType` define a un episodio perteneciente a un podcast.

| Campo | Tipo de dat | Descripción |
| :--- | :--- | :--- |
| `guid` | `String` | ID único del episodio |
| `title` | `String` | Título del episodio |
| `summary` | `String` | Sumario del episodio |
| `enclosure` | `String` | URL del archivo de audio del episodio |
| `link` | `String` | Enlace del episodio en la plataforma original |
| `image` | `String` | Imagen de portada del episodio |

## Consultas GraphQL

La API permite realizar diferentes consultas que por el momento son públicas. En el futuro requeriremos una llave API para consumir los diferentes endpoints.

### Analytics

El endpoint `analytics` permite consumir ciertas métricas de la plataforma como el número de podcast, número de episodios, entre otros datos públicos. El endpoint devuelve un `String` codificado en formato JSON.

{% tabs %}
{% tab title="Query" %}
```graphql
query analytics {
    analytics
}
```
{% endtab %}

{% tab title="Ejemplo de salida" %}
```javascript
{
  "data": {
    "analytics": "{\"metrics\": {\"podcasts_count\": 76, \"episodes_count\": 1046, \"telegram_audio_files_count\": 3279, \"categories_labels\": [\"Crimen real\", \"Comedia\", \"Deportes\", \"Historia\", \"Negocios\", \"Sociedad y cultura\", \"Educaci\\u00f3n\", \"Noticias\", \"Religi\\u00f3n y espiritualidad\", \"Cine y TV\", \"Tecnolog\\u00eda\", \"Artes\", \"Salud y bienestar\", \"M\\u00fasica\", \"Ciencia\", \"Ocio\", \"Gobierno\", \"Ficci\\u00f3n\"], \"categories_series\": [0, 2, 12, 0, 1, 15, 2, 7, 1, 0, 16, 7, 4, 3, 1, 2, 1, 1]}}"
  }
}
```
{% endtab %}
{% endtabs %}

### Categories

El endpoint `categories` permite obtener el listado de objetos `CategoryType` que define las categorías de podcasts de la plataforma.

{% tabs %}
{% tab title="Query" %}
```graphql
query {
    categories {
        name
        slug
        description
        img
    }
}
```
{% endtab %}

{% tab title="Ejemplo de salida" %}
```javascript
{
  "data": {
    "categories": [
      {
        "name": "Crimen real",
        "slug": "crimen-real",
        "description": "",
        "img": "categories/true-crime.png"
      },
      {
        "name": "Comedia",
        "slug": "comedia",
        "description": "",
        "img": "categories/comedy.png"
      },
      {
        "name": "Deportes",
        "slug": "deportes",
        "description": "",
        "img": "categories/sports.png"
      },
      {
        "name": "Historia",
        "slug": "historia",
        "description": "",
        "img": "categories/history.png"
      },
      {
        "name": "Negocios",
        "slug": "negocios",
        "description": "",
        "img": "categories/businesses.png"
      },
      {
        "name": "Sociedad y cultura",
        "slug": "sociedad-y-cultura",
        "description": "",
        "img": "categories/society-and-culture.png"
      },
      {
        "name": "Educación",
        "slug": "educacion",
        "description": "",
        "img": "categories/education.png"
      },
      {
        "name": "Noticias",
        "slug": "noticias",
        "description": "",
        "img": "categories/news.png"
      },
      {
        "name": "Religión y espiritualidad",
        "slug": "religion-y-espiritualidad",
        "description": "",
        "img": "categories/religion-and-spirituality.png"
      },
      {
        "name": "Cine y TV",
        "slug": "cine-y-tv",
        "description": "",
        "img": "categories/tv-and-films.png"
      },
      {
        "name": "Tecnología",
        "slug": "tecnologia",
        "description": "",
        "img": "categories/technology.png"
      },
      {
        "name": "Artes",
        "slug": "artes",
        "description": "",
        "img": "categories/arts.png"
      },
      {
        "name": "Salud y bienestar",
        "slug": "salud-y-bienestar",
        "description": "",
        "img": "categories/health-and-wellbeing.png"
      },
      {
        "name": "Música",
        "slug": "music",
        "description": "",
        "img": "categories/music.png"
      },
      {
        "name": "Ciencia",
        "slug": "ciencia",
        "description": "",
        "img": "categories/sciences.png"
      },
      {
        "name": "Ocio",
        "slug": "ocio",
        "description": "",
        "img": "categories/leisure.png"
      },
      {
        "name": "Gobierno",
        "slug": "gobierno",
        "description": "",
        "img": "categories/government.png"
      },
      {
        "name": "Ficción",
        "slug": "ficcion",
        "description": "",
        "img": "categories/fiction.png"
      }
    ]
  }
}
```
{% endtab %}
{% endtabs %}

### Category

El endpoint `category` permite obtener los detalles de un objeto `CategoryType` conociendo su `slug`.

{% tabs %}
{% tab title="Query" %}
```graphql
query category($slug: String!) {
    category(slug: $slug) {
        name
        slug
        description
        img
    }
}
```

Ejemplo de datos de entrada:

```javascript
{
  "slug": "tecnologia"
}
```
{% endtab %}

{% tab title="Ejemplo de salida" %}
```javascript
{
  "data": {
    "category": {
      "name": "Tecnología",
      "slug": "tecnologia",
      "description": "",
      "img": "categories/technology.png"
    }
  }
}
```
{% endtab %}
{% endtabs %}

### Podcasts

El endpoint `podcasts` permite obtener el listado de objetos `PodcastType` cuya categoría es conocida.

{% tabs %}
{% tab title="Query" %}
```graphql
query podcasts($categorySlug: String!) {
  podcasts(categorySlug: $categorySlug) {
    title
  }
}
```

Ejemplo de datos de entrada:

```javascript
{
  "categorySlug": "tecnologia"
}
```
{% endtab %}

{% tab title="Ejemplo de salida" %}
```javascript
{
  "data": {
    "podcasts": [
      {
        "title": "AFTP"
      },
      {
        "title": "Como lo pienso lo digo"
      },
      {
        "title": "El Bache"
      },
      {
        "title": "Error en el Sistema"
      },
      {
        "title": "La mente creativa"
      },
      {
        "title": "RadioAtenas Podcast"
      },
      {
        "title": "Pantalla de Carga"
      },
      {
        "title": "PodcastInside"
      },
      {
        "title": "Podcasting con Albert"
      },
      {
        "title": "StartupCuba"
      },
      {
        "title": "SystemInside Podcast"
      },
      {
        "title": "SWL-X Podcast>"
      },
      {
        "title": "TecnoLike Plus"
      },
      {
        "title": "TecnoCode+"
      },
      {
        "title": "Tech_Junkies Podcast"
      },
      {
        "title": "TuPodcast"
      }
    ]
  }
}
```
{% endtab %}
{% endtabs %}

### Podcast

El endpoint `podcast` permite obtener los detalles de un objeto `PodcastType` conociendo su `slug`.

{% tabs %}
{% tab title="Query" %}
```graphql
query podcast($slug: String!) {
  podcast(slug: $slug) {
    title
    author
    link
    url
    generator
  }
}
```

Ejemplo de datos de entrada:

```javascript
{
  "slug": "la-mente-creativa"
}
```
{% endtab %}

{% tab title="Ejemplo de salida" %}
```javascript
{
  "data": {
    "podcast": {
      "title": "La mente creativa",
      "author": "Carlos Lugones",
      "link": "https://lugodev.com/podcast",
      "url": "https://anchor.fm/s/164f2390/podcast/rss",
      "generator": "Anchor Podcasts"
    }
  }
}
```
{% endtab %}
{% endtabs %}

## ¿Qué hay para el futuro?

La API de CubaPod se encuentra en desarrollo activo y la estamos mejorando día por día, puede ser que su esquema cambie, introduzcamos mutaciones y mucho más.

Mientras tanto, puedes ir jugando con ella y si quieres desarrollar una aplicación, nos gustaría saber de ti, [contáctanos](https://cubapod.net/contact).

