# Politique de sécurité

PrivaLayer est un outil de confidentialité ; les failles de sécurité y sont prises au sérieux.

## Signaler une vulnérabilité

Merci de **ne pas** ouvrir d'issue publique pour une faille de sécurité potentielle. Contactez plutôt le mainteneur en privé (via l'adresse de contact du dépôt GitHub, ou une Security Advisory GitHub privée si le dépôt le permet) en décrivant :

- le problème et son impact potentiel,
- les étapes pour le reproduire,
- si possible, un correctif suggéré.

Vous recevrez un accusé de réception sous quelques jours. PrivaLayer n'ayant pas de serveur ni de service en ligne, la plupart des correctifs consistent simplement à publier une nouvelle version du fichier `index.html`.

## Périmètre

Sont particulièrement bienvenus les signalements concernant :

- une implémentation incorrecte des primitives cryptographiques (dérivation de clé, ratchet, AES-GCM),
- une fuite de données vers le réseau (PrivaLayer ne doit **jamais** faire de requête réseau),
- une faille permettant de déchiffrer des messages sans la clé privée du destinataire,
- une réutilisation de nonce/IV ou de clé de message.

Hors périmètre : l'absence d'authentification hors-bande de l'échange de clé publique (limitation connue et documentée dans le README), ou la sécurité de l'appareil de l'utilisateur lui-même.
