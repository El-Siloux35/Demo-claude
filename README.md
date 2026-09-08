# Démos d'interfaces : voix, geste, regard, objet 3D, animations

Sept démos d'interfaces à ouvrir dans un navigateur, sans installation ni
compilation. Chaque page est un fichier HTML autonome, et porte un encart noir
« Voir le prompt » qui donne le prompt permettant de la reconstruire.

`index.html` est la page d'accueil qui mène aux sept démos.

## Mettre en ligne

Ces pages sont du HTML statique : n'importe quel hébergement fait l'affaire.

Avec Vercel, depuis un dépôt GitHub :

1. Créer un dépôt et y pousser ce dossier.
2. Sur vercel.com, « Add New » puis « Project », et importer le dépôt.
3. Laisser le préréglage sur « Other » : il n'y a rien à construire, les
   fichiers sont servis tels quels.
4. Déployer. L'adresse fournie est en HTTPS, ce qui est nécessaire au point
   suivant.

Sans dépôt, l'interface de Vercel accepte aussi le dossier par glisser-déposer.

## Pourquoi l'hébergement compte pour la caméra et le micro

Quatre démos demandent la caméra ou le micro : Voix, Geste, Regard et Carte.
Un navigateur n'accorde ces autorisations qu'à une page servie en HTTPS, ou
ouverte depuis la machine elle-même. Une page mise en ligne en HTTPS fonctionne
donc normalement.

Une page affichée à l'intérieur d'un cadre (iframe) est un cas à part : elle
n'obtient la caméra que si la page qui l'intègre la lui délègue explicitement.
Sans cette délégation, le navigateur refuse sans même proposer d'autorisation.
Les démos concernées détectent cette situation et l'expliquent à l'écran.

## Ce que chaque démo utilise

| Démo | Capteur | Technologie |
| --- | --- | --- |
| Voix | Micro | Web Audio API (analyse du son dans le navigateur) |
| Geste | Caméra | MediaPipe Tasks Vision, suivi de main |
| Regard | Caméra | MediaPipe Tasks Vision, suivi de visage |
| Carte | Caméra | MediaPipe Tasks Vision, orientation de la tête |
| Carrousel | Aucun | Three.js et un shader de déformation |
| Objet 3D | Aucun | Three.js et GSAP ScrollTrigger |
| Animations | Aucun | anime.js |

Le calcul se fait entièrement dans le navigateur : aucune image ni aucun son
n'est envoyé sur un serveur. Les bibliothèques et les modèles de détection sont
chargés depuis un CDN au premier affichage, une connexion est donc nécessaire.

## Ouvrir en local

Ouvrir `index.html` directement fonctionne dans la plupart des cas. Pour se
rapprocher des conditions d'un vrai hébergement, servir le dossier :

```
python3 -m http.server 8000
```

puis ouvrir http://localhost:8000
