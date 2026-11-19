# Générateur de cartes de visite — CCG Groupe

Page unique, servie par GitHub Pages : **https://siradio.github.io/cartes-ccg/**

Saisir ses coordonnées, obtenir une carte de visite au format **85 × 55 mm**
avec un QR code vCard, et l'imprimer ou l'enregistrer en PDF.

## Fonctionnement

- Aperçu de la carte mis à jour à la frappe.
- Le QR encode une fiche **vCard 3.0** : un scan enregistre le contact
  directement dans le téléphone.
- Photo optionnelle, affichée en rond à côté du QR.
- Impression A4 à l'échelle 100 % — la carte sort à sa taille réelle.
- Export du QR seul en PNG.

## Ce qui sort de la machine : rien

La page est **autonome**. Aucune bibliothèque externe, aucune police distante,
aucun appel réseau : le générateur de QR et le logo sont embarqués dans le
fichier.

Les informations saisies ne sont ni transmises, ni enregistrées ailleurs que
dans le navigateur :

- les coordonnées personnelles (nom, téléphone, e-mail, photo) restent en
  mémoire de page et disparaissent à la fermeture ;
- seuls les champs d'entreprise — société, site, adresse, slogan — sont
  conservés dans le `localStorage` du navigateur, sous la clé
  `ccg_carte_entreprise_v1`, pour éviter de les resaisir.

La page fonctionne donc aussi bien hors ligne : enregistrer `index.html` et
l'ouvrir depuis le disque.

## Utilisation hors ligne

Clic droit sur la page → *Enregistrer sous*, puis ouvrir le fichier.
Tout continue de fonctionner, QR compris.
