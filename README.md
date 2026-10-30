# 🔐 Nom-du-projet

Application mobile **personnelle**, **sans pub** et **sans tracker**, pour gérer ses authentifications :

- générer ses codes 2FA (TOTP), comme une app d'authenticator ;
- stocker ses mots de passe dans un coffre chiffré.

> ⚠️ **Statut : en planification.** Rien n'est encore implémenté. Ce dépôt contient pour l'instant la feuille de route et les choix de conception.

## Pourquoi ce projet ?

Je ne veux pas confier mes codes d'authentification et mes mots de passe à une app remplie de publicités et de trackers. Ce projet est un outil à usage personnel, dont je contrôle le code et les données. C'est aussi un projet d'apprentissage.

> Ce projet n'est pas audité. Si tu cherches une solution éprouvée, regarde plutôt [Aegis](https://github.com/beemdevelopment/Aegis), [Ente Auth](https://github.com/ente-io/ente), [Bitwarden](https://github.com/bitwarden) ou [KeePassXC](https://github.com/keepassxreboot/keepassxc).

## Fonctionnalités prévues

### Authenticator (TOTP)
- [ ] Ajout par scan de QR code (`otpauth://`) ou saisie manuelle de la clé
- [ ] Génération des codes TOTP (RFC 6238) avec compte à rebours
- [ ] Stockage chiffré des secrets
- [ ] Déverrouillage par biométrie ou code PIN
- [ ] Export / import chiffrés (sauvegarde)

### Gestionnaire de mots de passe
- [ ] Coffre chiffré protégé par un mot de passe maître (dérivation de clé Argon2)
- [ ] Création, modification, suppression et recherche d'entrées
- [ ] Générateur de mots de passe
- [ ] Verrouillage automatique et effacement du presse-papiers

### Confort et sécurité
- [ ] Autofill (Android / iOS)
- [ ] Blocage des captures d'écran
- [ ] Synchronisation optionnelle chiffrée de bout en bout, ou sauvegarde manuelle d'un fichier

## Principes de sécurité

- **Aucune crypto maison** : uniquement des bibliothèques éprouvées (libsodium, Android Keystore, iOS Keychain).
- **Local d'abord** : les données restent sur l'appareil, sauf sauvegarde ou synchronisation choisie explicitement.
- **Zéro pub, zéro télémétrie, zéro tracker.**
- **Sauvegarde obligatoire** : perdre le téléphone ne doit pas signifier perdre l'accès à ses comptes.

## Feuille de route

| Phase | Contenu |
|-------|---------|
| 0 | Cadrage : plateforme, technologie, modèle de menace |
| 1 | MVP authenticator (TOTP) |
| 2 | Gestionnaire de mots de passe |
| 3 | Autofill, synchronisation, protections supplémentaires |
| 4 | Durcissement : relecture de la crypto, tests, procédure de récupération |

Les passkeys (WebAuthn / FIDO2) sont hors périmètre au départ et seront évaluées plus tard.

## Stack technique

À définir : natif (Kotlin / Swift), Flutter ou React Native.

## Installation

Pas encore disponible.

## Contribuer

Projet personnel : les issues et les remarques sur la sécurité sont les bienvenues, les pull requests le seront une fois le socle posé.

## Licence

À choisir (par exemple MIT ou GPL-3.0).
