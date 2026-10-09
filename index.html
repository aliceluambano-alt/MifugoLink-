/* ═══════════════════════════════════════════════════════════
   MifugoLink EA — Service Worker (v10.6)
   By A. C. Luambano
   ═══════════════════════════════════════════════════════════ */

const CACHE_NAME = 'mifugolink-v10.6';
const RUNTIME_CACHE = 'mifugolink-runtime-v10.6';

const PRECACHE_URLS = [
  './',
  './Mifu.A.%20C.%20L%20(1).html',
  './manifest.json'
];

self.addEventListener('install', event => {
  event.waitUntil(
    caches.open(CACHE_NAME).then(cache => {
      return cache.addAll(PRECACHE_URLS).catch(err => console.warn(err));
    }).then(() => self.skipWaiting())
  );
});

self.addEventListener('activate', event => {
  event.waitUntil(
    caches.keys().then(keys => {
      return Promise.all(
        keys.filter(k => k !== CACHE_NAME && k !== RUNTIME_CACHE).map(k => caches.delete(k))
      );
    }).then(() => self.clients.claim())
  );
});

self.addEventListener('fetch', event => {
  const req = event.request;
  const url = new URL(req.url);
  if (req.method !== 'GET') return;
  if (url.hostname.includes('googleapis.com') || url.hostname.includes('gstatic.com') || url.hostname.includes('firebase')) return;
  if (url.protocol === 'chrome-extension:') return;

  if (url.hostname.includes('tile.openstreetmap.org') || url.hostname.includes('unpkg.com')) {
    event.respondWith(
      caches.open(RUNTIME_CACHE).then(cache => {
        return cache.match(req).then(cached => {
          const fetchPromise = fetch(req).then(res => {
            if (res && res.status === 200) cache.put(req, res.clone());
            return res;
          }).catch(() => cached);
          return cached || fetchPromise;
        });
      })
    );
    return;
  }

  if (req.mode === 'navigate' || (req.headers.get('accept') || '').includes('text/html')) {
    event.respondWith(
      fetch(req).then(res => {
        if (res && res.status === 200) {
          const copy = res.clone();
          caches.open(CACHE_NAME).then(c => c.put(req, copy));
        }
        return res;
      }).catch(() => caches.match(req).then(cached => cached || caches.match('./Mifu.A.%20C.%20L%20(1).html')))
    );
    return;
  }

  event.respondWith(
    caches.match(req).then(cached => {
      return cached || fetch(req).then(res => {
        if (res && res.status === 200 && req.method === 'GET') {
          const copy = res.clone();
          caches.open(RUNTIME_CACHE).then(c => c.put(req, copy));
        }
        return res;
      }).catch(() => cached);
    })
  );
});

self.addEventListener('push', event => {
  let data = { title: 'MifugoLink EA', body: 'Kuna taarifa mpya' };
  try { if (event.data) data = event.data.json(); } catch(e){}
  event.waitUntil(
    self.registration.showNotification(data.title, { body: data.body, vibrate: [200, 100, 200] })
  );
});

self.addEventListener('notificationclick', event => {
  event.notification.close();
  event.waitUntil(
    clients.matchAll({ type: 'window' }).then(clientList => {
      for (const c of clientList) { if ('focus' in c) return c.focus(); }
      if (clients.openWindow) return clients.openWindow('./');
    })
  );
});
