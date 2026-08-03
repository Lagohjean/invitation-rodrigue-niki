# Invitation au mariage de Rodrigue & Grâce

Faire-part web pour le mariage de **Rodrigue & Grâce**, le **samedi 12 septembre 2026**
à Yopougon (Abidjan, Côte d'Ivoire).

Voir en ligne : https://lagohjean.github.io/invitation-rodrigue-niki/

## Le déroulé de la page

1. **La porte** — porte sculptée dorée qui s'ouvre sur « Touchez pour entrer »
2. **Héros** — monogramme R&G, prénoms, date et lieu, sur photo plein écran
3. **Carte d'invitation** — les familles LAGOH & KEMONDE, verset, accès à la carte imprimée
4. **Notre histoire** — frise des quatre étapes de l'union
5. **Le programme de la journée** — cérémonie civile, bénédiction, réception, fête
6. **Compte à rebours** — jusqu'au 12 septembre 2026 à 12h00
7. **Les lieux** — mairie de Yopougon et EERCI Temple Jérusalem, avec itinéraires
8. **Notre album** — 9 photos, agrandissables
9. **RSVP** — formulaire qui envoie la réponse par WhatsApp

## Le programme (source : la carte imprimée)

| Heure | Moment | Lieu |
|-------|--------|------|
| 12:00 | Cérémonie civile | Mairie de Yopougon |
| 13:30 | Bénédiction nuptiale | EERCI Temple Jérusalem, Yopougon Siporex, derrière l'Agence Emploi Jeunes |
| À la suite | Réception | Sur place, au Temple Jérusalem |

## Modifier le contenu

Tout ce qui change souvent est regroupé dans l'objet `CONFIG`, en haut de
[`assets/js/main.js`](assets/js/main.js) :

| Clé | Rôle |
|-----|------|
| `dateMariage` | Cible du compte à rebours (heure d'Abidjan, UTC+0) |
| `whatsapp` | Numéro qui reçoit les confirmations, format international sans `+` |
| `musique` | Chemin du fichier audio d'ambiance |
| `photos` | Les photos de l'album, dans l'ordre d'affichage |

Les textes (prénoms, familles, verset, horaires, adresses) sont directement dans
[`index.html`](index.html). Les couleurs et les tailles sont des variables CSS en tête de
[`assets/css/style.css`](assets/css/style.css).

### Ajouter la musique d'ambiance

Déposer un fichier `assets/audio/ambiance.mp3`. Le bouton son apparaît tout seul dès que
le fichier est disponible, et reste masqué sinon. Aucune autre modification n'est requise.

### Compléter les horaires de la réception

La carte imprimée ne précise pas l'heure de la réception : sa carte affiche donc
« À la suite ». Pour mettre un horaire, remplacer dans `index.html` :

```html
<span class="a-preciser">À la suite</span>
<!-- devient -->
<span class="moment-heure">16:00</span>
```

## Organisation des fichiers

```
index.html              le faire-part du 12 septembre 2026
assets/css/style.css    styles et animations
assets/js/main.js       porte, compte à rebours, galerie, RSVP
assets/img/             photos optimisées pour le web + ornements SVG
traditionnel/           l'ancien faire-part du mariage traditionnel (23 mai 2026)
```

## Notes techniques

- Aucune dépendance ni étape de compilation : c'est du HTML, CSS et JavaScript simples.
  Les seules ressources externes sont les polices Google Fonts.
- Les animations respectent `prefers-reduced-motion` : elles se désactivent pour les
  personnes qui ont demandé à limiter les effets de mouvement.
- Le RSVP ne stocke rien et n'utilise aucun serveur : il prépare un message WhatsApp que
  l'invité envoie lui-même.
- Testé de 390 px (mobile) à 1440 px (ordinateur), sans débordement horizontal.
