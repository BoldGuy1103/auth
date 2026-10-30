# Plan de développement : app mobile d'authentification perso

*Authenticator 2FA + gestionnaire de mots de passe, à usage personnel et sans pub*

## Mise en garde : le risque est dans la crypto, pas dans la pub

Une app maison sans pub est plus saine qu'une app bourrée de trackers. Mais un gestionnaire de mots de passe fait maison, c'est un coffre-fort : si le chiffrement est mal implémenté, on perd en sécurité par rapport à une app auditée. Deux règles :

- **Ne jamais écrire sa propre crypto.** Utiliser des bibliothèques éprouvées (libsodium, ou les API natives Android Keystore / iOS Keychain).
- **Prévoir des sauvegardes.** Si le téléphone meurt et que le coffre n'existe qu'à un endroit, on perd l'accès à tous ses comptes.

Il existe aussi des alternatives open source sans pub (Aegis ou Ente Auth pour le TOTP, Bitwarden ou KeePassXC pour les mots de passe). Si le but est d'apprendre ou d'avoir un contrôle total, construire reste pertinent. Sinon, ça vaut la peine de les essayer d'abord.

## Phase 0 : cadrage

- Choisir la plateforme (Android seul, iOS seul, ou les deux) et la techno : natif (Kotlin / Swift), Flutter ou React Native.
- Définir le modèle de menace : que veut-on protéger, et contre qui (vol du téléphone, malware, perte) ?

## Phase 1 : MVP authenticator (TOTP)

- Scan de QR code (`otpauth://`) et saisie manuelle de la clé secrète.
- Génération des codes TOTP (RFC 6238) avec compte à rebours. Des bibliothèques existent, c'est un algorithme simple.
- Stockage chiffré des secrets, déverrouillage par biométrie ou code PIN.
- Export et import chiffrés (sauvegarde).

## Phase 2 : gestionnaire de mots de passe

- Coffre chiffré (mot de passe maître + dérivation de clé Argon2).
- CRUD des entrées (site, identifiant, mot de passe, notes), recherche, générateur de mots de passe.
- Verrouillage automatique, effacement du presse-papiers après quelques secondes.

## Phase 3 : confort et sécurité

- Autofill (service d'autofill Android / extension de mots de passe iOS), la partie la plus technique.
- Blocage des captures d'écran, détection de root / jailbreak.
- Synchronisation optionnelle entre appareils, chiffrée de bout en bout, ou sauvegarde manuelle d'un fichier.

## Phase 4 : durcissement

- Relecture du code de chiffrement, tests, scénarios de perte du téléphone.
- Procédure de récupération documentée.

## Un point sur les passkeys

Les codes à 6 chiffres sont du TOTP, et les passkeys (WebAuthn/FIDO2) sont un mécanisme différent, plus complexe à gérer dans une app tierce. Il vaut mieux commencer par TOTP et mots de passe, puis évaluer les passkeys plus tard.

## Questions ouvertes

- Plateforme visée : Android, iOS, ou les deux ?
- Expérience préalable en développement mobile ?
