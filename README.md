# FARest-API
Filmaffinity REST API for get info about films or series.

## URL

```
http://elcabezon.es:3200/api
```

### Detail
Get the detail from a film with id (Give as result on search) with images and trailers.

````
http://elcabezon.es:3200/api/film
````

##### Parameters
* **id** - id film
* **lang** (optional) - Lang of result. Could be 'es' (Spanish) or 'en' (English). Default is Spanish

##### Example

````
//URL: http://elcabezon.es:3200/api/film?id=932476&lang=en

//RESPONSE
{
    "success": true,
    "data": {
        "url": "http://www.filmaffinity.com/en/film932476.html",
        "imageUrl": "https://pics.filmaffinity.com/the_matrix-155050517-large.jpg",
        "imageUrlMed": "https://pics.filmaffinity.com/the_matrix-155050517-mmed.jpg",
        "rating": "7.9",
        "votes": "185181",
        "title": "The Matrix",
        "titleOrig": "The Matrix",
        "year": "1999",
        "running": "131 min.",
        "country": {
            "imgCountry": "http://www.filmaffinity.com/imgs/countries/US.jpg",
            "country": "United States"
        },
        "directors": [
            {
                "name": "Hermanas Wachowski",
                "request": {
                    "query": "Hermanas Wachowski",
                    "type": "DIRECTOR",
                    "lang": "en"
                }
            },
            ...
        ],
        "screenwriter": [
            "Lilly Wachowski",
            "Lana Wachowski",
            "Hermanas Wachowski"
        ],
        "music": [
            "Don Davis"
        ],
        "cinematography": [
            "Bill Pope"
        ],
        "cast": [
            {
                "name": "Keanu Reeves",
                "request": {
                    "query": "Keanu Reeves",
                    "type": "CAST",
                    "lang": "en"
                }
            },
            ...
        ],
        "production": "Warner Bros / Village Roadshow Pictures / Groucho II Film Partnership. Producer: Joel Silver",
        "genre": [
            {
                "name": "Sci-Fi",
                "request": {
                    "query": "C-F",
                    "type": "GENRE",
                    "lang": "en"
                }
            },
            ...
        ],
        "synopsis": "In the near future, Computer hacker Neo is contacted by underground ...",
        "id": 932476,
        "images": [
            {
                "large": "https://pics.filmaffinity.com/The_Matrix-155050517-large.jpg",
                "thumbnail": "https://pics.filmaffinity.com/The_Matrix-155050517-s200.jpg"
            },
            ...
        ],
        "trailers": [
            "https://www.youtube-nocookie.com/embed/UM5yepZ21pI?rel=0&iv_load_policy=3&showinfo=0&autoplay=0"
        ]
    }
}

````

### Preview
Get simplified info from an array of ids. The result object array is like as result of search.

##### Parameters
* **id** - Array of ids
* **lang** (optional) - Lang of result. Could be 'es' (Spanish) or 'en' (English). Default is Spanish

##### Example`

````
//URL: http://elcabezon.es:3200/api/film/preview?id=[932476]&lang=en

//RESPONSE
{
    "success": true,
    "data": [
        {
            "id": 932476,
            "url": "http://www.filmaffinity.com/en/film932476.html",
            "thumbnail": "https://pics.filmaffinity.com/the_matrix-155050517-msmall.jpg",
            "year": "1999",
            "title": "The Matrix",
            "directors": [
                {
                    "name": "Hermanas Wachowski",
                    "request": {
                        "query": "Hermanas Wachowski",
                        "type": "DIRECTOR",
                        "lang": "en"
                    }
                },
                ...
            ],
            "cast": [
                {
                    "name": "Keanu Reeves",
                    "request": {
                        "query": "Keanu Reeves",
                        "type": "CAST",
                        "lang": "en"
                    }
                },
                ...
            ],
            "country": {
                "imgCountry": "http://www.filmaffinity.com/imgs/countries/US.jpg",
                "country": "United States"
            },
            "rating": "7.9",
            "votes": "185182",
            "cache": 1507496292682
        }
    ]
}

````

### Search
Search films, series, directors or actors from query.

##### Parameters
* **query** - query param
* **lang** (optional) - Lang of result. Could be 'es' (Spanish) or 'en' (English). Default is Spanish
* **type** (optional) - Search type
* **start** (optional) - Default is 0

###### Search types
There are four type of search (Must be in uppercase)

* **TITLE** (default) - Search by title.
* **DIRECTOR** - Search by director
* **CAST** - Search by actor
* **GENRE** - Search by genre (the code is inside response or get from filmaffinity)
* **TOPIC** - Search by topic (the code is inside response or get from filmaffinity)


##### Example

````
//URL: http://elcabezon.es:3200/api/search?query=matrix&lang=en&start=0&type=TITLE

//RESPONSE
{
    "success": true,
    "data": {
        "more": false,
        "count": 9,
        "result": [
            ...
            {
                "id": "932476",
                "url": "http://www.filmaffinity.com/en/film932476.html",
                "country": {
                    "imgCountry": "http://www.filmaffinity.com/imgs/countries/US.jpg",
                    "country": "United States"
                },
                "year": "1999",
                "thumbnail": "https://pics.filmaffinity.com/the_matrix-155050517-msmall.jpg",
                "title": "The Matrix",
                "directors": [
                    {
                        "name": "Hermanas Wachowski",
                        "request": {
                            "query": "Hermanas Wachowski",
                            "type": "DIRECTOR",
                            "lang": "en"
                        }
                    },
                    ...
                ],
                "cast": [
                    {
                        "name": "Keanu Reeves",
                        "request": {
                            "query": "Keanu Reeves",
                            "type": "CAST",
                            "lang": "en"
                        }
                    },
                    ...
                ],
                "rating": "7.9",
                "votes": "185,182 "
            },
            ...
           
                ],
                "rating": "--",
                "votes": ""
            }
        ]
    }
}

````

### Notes
Directors, actors and genre contains a request object which could send as a search request.

## Author
* **Alberto Espinilla**
