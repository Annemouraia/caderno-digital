const CACHE_NAME = 'caderno-digital-v2';
const urlsToCache = [
  '/caderno-digital/',
  '/caderno-digital/index.html',
  '/caderno-digital/manifest.json',
  '/caderno-digital/service-worker.js'
];

// Instalação do Service Worker
self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME).then((cache) => {
      console.log('✅ Cache aberto');
      return cache.addAll(urlsToCache).catch((err) => {
        console.log('⚠️ Alguns arquivos não puderam ser cacheados:', err);
        return Promise.resolve();
      });
    })
  );
  self.skipWaiting();
});

// Ativação do Service Worker
self.addEventListener('activate', (event) => {
  event.waitUntil(
    caches.keys().then((cacheNames) => {
      return Promise.all(
        cacheNames.map((cacheName) => {
          if (cacheName !== CACHE_NAME) {
            console.log('🗑️ Deletando cache antigo:', cacheName);
            return caches.delete(cacheName);
          }
        })
      );
    })
  );
  self.clients.claim();
});

// Estratégia de fetch: cache-first com fallback de rede
self.addEventListener('fetch', (event) => {
  // Ignorar requisições POST (formulários, API)
  if (event.request.method !== 'GET') {
    return;
  }

  event.respondWith(
    caches.match(event.request).then((response) => {
      // Retorna do cache se encontrado
      if (response) {
        return response;
      }

      // Caso contrário, tenta fazer a requisição
      return fetch(event.request).then((networkResponse) => {
        // Não cachear respostas inválidas
        if (!networkResponse || networkResponse.status !== 200 || networkResponse.type !== 'basic') {
          return networkResponse;
        }

        // Clona a resposta para cachear
        const responseToCache = networkResponse.clone();
        caches.open(CACHE_NAME).then((cache) => {
          cache.put(event.request, responseToCache);
        });

        return networkResponse;
      }).catch(() => {
        // Se falhar, tenta servir a página em cache
        return caches.match('/caderno-digital/index.html');
      });
    })
  );
});

// Push notifications (opcional)
self.addEventListener('push', (event) => {
  const options = {
    body: event.data ? event.data.text() : 'Nova notificação do Caderno Digital',
    icon: '/caderno-digital/icon-192.png',
    badge: '/caderno-digital/icon-192.png'
  };

  event.waitUntil(
    self.registration.showNotification('Caderno Digital', options)
  );
});

// Sincronização em background (opcional)
self.addEventListener('sync', (event) => {
  if (event.tag === 'sync-dados') {
    event.waitUntil(
      // Aqui você pode sincronizar dados com backend
      Promise.resolve()
    );
  }
});

console.log('✅ Service Worker v2 carregado com sucesso!');
