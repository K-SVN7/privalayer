# PrivaLayer

Application web (fichier HTML unique) qui chiffre du texte et des fichiers localement dans le navigateur avant de les partager par n'importe quel canal (WhatsApp, SMS, Telegram, e-mail, etc.). Aucun serveur, aucune dépendance externe, aucune installation requise.

## Fonctionnement

- Chiffrement de bout en bout basé sur la Web Crypto API du navigateur (ECDH P-256 pour l'échange de clés, AES-256-GCM pour le chiffrement).
- Chaque contact jumelé dispose d'un secret partagé dérivé localement (Diffie-Hellman), à partir duquel une clé unique est générée pour chaque message (ratchet symétrique à chaînes HKDF).
- Le trousseau (clé privée, clé publique, contacts) est stocké chiffré dans `localStorage`, protégé par un mot de passe (PBKDF2, 100 000 itérations, SHA-256).
- Aucune requête réseau n'est émise par l'application, à aucun moment.
- Fonctionne hors ligne après le premier chargement (PWA installable via `manifest.json` + `sw.js`).

## Fichiers du projet

```
index.html       Application complète (HTML + CSS + JS inline)
manifest.json    Manifeste PWA
sw.js            Service worker (cache hors ligne)
icon-192.png     Icône PWA 192×192
icon-512.png     Icône PWA 512×512
```

## Installation

Trois options, sans build ni dépendance :

1. Ouvrir `index.html` directement dans un navigateur.
2. Héberger l'ensemble des fichiers sur un hébergement statique quelconque (GitHub Pages, etc.).
3. Après un premier chargement, installer l'app depuis le menu du navigateur (« Ajouter à l'écran d'accueil ») pour un usage 100 % hors ligne.

## Utilisation

1. **Créer un mot de passe** au premier lancement — il protège le trousseau local et n'est jamais transmis.
2. **Partager sa clé publique** (onglet *Ma clé*) avec un contact, par n'importe quel moyen.
3. **Jumeler ce contact** (onglet *Contacts*) en collant sa clé publique reçue.
4. **Chiffrer** un message ou un fichier pour ce contact (onglet *Chiffrer*), puis copier ou partager le résultat.
5. Le destinataire colle le bloc reçu, ou ouvre le fichier `.privalayer`, dans son propre PrivaLayer pour le déchiffrer (onglet *Déchiffrer*).

L'onglet *Réglages* permet de changer le mot de passe, exporter/importer le trousseau, ou régénérer les clés.

## Compatibilité

Chrome 60+, Firefox 57+, Safari 11+, Edge 79+.

## Licence

GPL-3.0 — voir [LICENSE](LICENSE).

## Signaler une faille

Voir [SECURITY.md](SECURITY.md).
