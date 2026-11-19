# Générateur de cartes de visite — CCG Groupe

Page unique, servie par GitHub Pages : **https://siradio.github.io/cartes-ccg/**

Saisir ses coordonnées, obtenir une carte de visite au format **85 × 55 mm**
avec un QR code vCard, et l'imprimer ou l'enregistrer en PDF.

## Accès protégé

La page s'ouvre sur un écran de connexion. Le contenu est **chiffré** :

- AES-256-GCM ;
- clé dérivée de l'identifiant et du mot de passe par PBKDF2-HMAC-SHA256,
  310 000 itérations ;
- déchiffrement réalisé dans le navigateur via WebCrypto.

Le fichier publié ne contient donc aucun texte lisible : sans le mot de passe,
il n'y a rien à extraire du code source de la page.

**Les identifiants ne figurent pas dans ce dépôt.** Ils sont transmis séparément.

### Limites à connaître

- Ce dépôt est public : le fichier chiffré est téléchargeable par tous. La
  confidentialité repose entièrement sur la robustesse du mot de passe, une
  attaque hors ligne restant toujours possible.
- Toute personne disposant du mot de passe accède à la page et peut la
  rediffuser.
- Le mécanisme protège le contenu au repos ; ce n'est pas un contrôle d'accès
  par utilisateur : ni comptes distincts, ni révocation individuelle, ni
  journal d'accès.

### Prérequis navigateur

WebCrypto exige un contexte sécurisé. La page fonctionne servie en **https**
(GitHub Pages) ou depuis `localhost`. Ouverte directement en `file://`, le
déchiffrement est indisponible et la page l'indique explicitement.

## Fonctionnement

- Aperçu de la carte mis à jour à la frappe.
- Le QR encode une fiche **vCard 3.0** : un scan enregistre le contact
  directement dans le téléphone.
- Photo optionnelle, affichée en rond à côté du QR.
- Impression A4 à l'échelle 100 % — la carte sort à sa taille réelle.
- Export du QR seul en PNG.

## Ce qui sort de la machine : rien

Une fois déverrouillée, la page est **autonome**. Aucune bibliothèque externe,
aucune police distante, aucun appel réseau : le générateur de QR et le logo
sont embarqués.

Les informations saisies ne sont ni transmises, ni enregistrées ailleurs que
dans le navigateur :

- les coordonnées personnelles (nom, téléphone, e-mail, photo) restent en
  mémoire de page et disparaissent à la fermeture ;
- seuls les champs d'entreprise — société, site, adresse, slogan — sont
  conservés dans le `localStorage` du navigateur, sous la clé
  `ccg_carte_entreprise_v1`, pour éviter de les resaisir.

## Régénérer la page

Le générateur et la source non chiffrée sont conservés hors de ce dépôt.
Changer le mot de passe consiste à relancer la génération puis à remplacer
`index.html` :

```bash
node mkgate.js Generateur-cartes-CCG.html index.html <identifiant> <motdepasse>
```

Un numéro de version daté s'affiche sous le formulaire : il permet de vérifier
d'un coup d'œil qu'on regarde bien la dernière version publiée, et non une copie
en cache.
