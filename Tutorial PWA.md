# PWA - Progressive Web Apps

## Introducción

Las Progressive Web Apps son una tecnología impulsada por Google que busca juntar lo mejor de los dos mundos entre Web y Mobile.

Si bien es una tecnología que aún está en crecimiento actualmente permite por ejemplo "instalar" una web en el escritorio de un teléfono haciéndolo parecer un poco más una app. A su vez se pueden incluir procesos que permitan no requerir de conexión a internet.

## Uso

Desde un punto de vista simple será necesario hacer 3 pasos para transformar tu Web App en una PWA.

**Paso 1**

El primer paso es incluir un archivo **manifest.json**

Este archivo es el que permite que la web app sea "instalable" aclarando peculiaridades como colores de la PWA, ícono, nombre ,etc.

Un archivo **manifest.json **se ve de la siguiente manera:

﻿{

  "short_name": "Clases",

  "name": "Cronograma de clases",

  "icons": [

    {

      "src": "launcher-icon.png",

      "sizes": "48x48",

      "type": "image/png"

    },

    {

      "src": "launcher-icon-2x.png",

      "sizes": "96x96",

      "type": "image/png"

    },

    {

      "src": "launcher-icon-4x.png",

      "sizes": "192x192",

      "type": "image/png"

    },

    {

      "src": "launcher-icon-8x.png",

      "sizes": "256x256",

      "type": "image/png"

    }

  ],

  "start_url": "./",

  "display": "standalone",

  "orientation": "portrait",

  "theme_color": "#E4133B",

  "background_color": "#E4133B"

}

**Paso 2**

El segundo paso busca generar eventos en Javascript que detecten la conexión online y offline.

Esto se verá similar a algo así:

window.addEventListener('online', function(e) {

	    // Resync data with server.

	    console.log("You are online");

	    hideOfflineWarning();

	    loadData();

	}, false);

	window.addEventListener('offline', function(e) {

	    // Queue up events for server.

	    console.log("You are offline");

	    showOfflineWarning();

	}, false);

	// Check if the user is connected.

	if (navigator.onLine) {

	    loadData();

	} else {

	    // Show offline message

			try {

				loadData();

			} catch (e) {

			}

	    showOfflineWarning();

	}

Las funciones **showOfflineWarning**, **loadData** y **hideOfflineWarning** dependerán de la lógica de tu aplicación.

**Paso 3**

El tercer paso pasa por registrar un Service Worker. Un Service Worker es un script que entre otras cosas nos permite guardar recursos en la memoria del teléfono haciendo que no requiera de conexión a internet para cargar por primera vez.

En un javascript uno debería incluir un código del siguiente estilo:

if ('serviceWorker' in navigator) {

	    navigator.serviceWorker.register('./sw.js').then(function(reg) {

	        console.log('Successfully registered service worker', reg);

	    }).catch(function(err) {

	        console.warn('Error whilst registering service worker', err);

	    });

	}

Por otra parte, crear el archivo **sw.js** con un formato de este estilo aclarando que archivos a guardar en caché:

// use a cacheName for cache versioning

var cacheName = 'v1:static';

// during the install phase you usually want to cache static assets

self.addEventListener('install', function(e) {

    // once the SW is installed, go ahead and fetch the resources to make this work offline

    e.waitUntil(

        caches.open(cacheName).then(function(cache) {

            return cache.addAll([

                './',

                './css/style.css',

                './js/script.js',

                './css/fonts/roboto.woff',

                './offline.html'

            ]).then(function() {

                self.skipWaiting();

            });

        })

    );

});

// when the browser fetches a url

self.addEventListener('fetch', function(event) {

    // either respond with the cached object or go ahead and fetch the actual url

    event.respondWith(

        caches.match(event.request).then(function(response) {

            if (response) {

                // retrieve from cache

                return response;

            }

            // fetch as normal

            return fetch(event.request);

        })

    );

});
