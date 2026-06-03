# NetScheM — Architecture Diagram Designer

Éditeur de diagrammes d'architecture Mermaid.js en *single-page HTML*.  
Aucune installation, aucune dépendance locale : ouvrez le fichier dans un navigateur et commencez.

## Fonctionnalités

### Éditeur de code
- **CodeMirror 5** avec coloration syntaxique Mermaid, numérotation de lignes, auto-complétion
- Mode sombre / clair avec persistance dans `localStorage`
- Rendu automatique du diagramme (debounce 400 ms) avec thème adapté au mode
- Raccourci `Ctrl+S` / `Cmd+S` pour forcer le rendu

### Zoom du diagramme
- Boutons `+` / `−` / `⟲` (reset) dans l'en-tête de l'aperçu
- Molette de souris sur l'aperçu (Ctrl non nécessaire)
- Raccourcis clavier : `Ctrl+=`, `Ctrl+-`, `Ctrl+0`
- Incréments de 0.25, de 25 % à 300 %
- Persistance du niveau de zoom dans `localStorage`
- Barres de défilement horizontale et verticale actives quand le zoom dépasse 100 %

### Templates d'architecture (lecture seule)
6 modèles préchargés, consultables en lecture seule :

| Template | Description |
|---|---|
| **3-Tiers** | Isolation Présentation / Métier / Données |
| **Microservices Sécurisés** | API Gateway, JWT, Rate Limiter |
| **Flux TLS Chiffré** | Chiffrement de bout en bout |
| **Zero Trust** | Never trust, always verify |
| **Pipeline CI/CD** | Intégration et déploiement sécurisés |
| **Architecture Hexagonale** | Ports / Adapters |

- Un badge violet `[template]` s'affiche à côté du nom du template
- L'éditeur devient grisé (read-only) avec opacité réduite
- Un bouton **Dupliquer** apparaît pour copier le template en mode édition

### Schéma personnalisé
- Option `✦ Schéma personnalisé` en tête de la liste des templates
- Éditeur libre avec auto-sauvegarde dans `localStorage`
- Badge vert `[Personnalisé]`

### Assistant syntaxe Mermaid
Panneau latéral coulissant (`?` dans la barre d'outils) avec 6 sections et boutons « Insérer » :

1. **Orientation du graphe** — `graph TB`, `graph LR`, etc.
2. **Types de nœuds** — Rectangle, arrondi, cercle, diamant, losange
3. **Types de liens** — Flèche, trait, pointillé, avec étiquette
4. **Subgraph** — Groupes de nœuds
5. **Styles et couleurs** — `style`, `classDef`, `class`
6. **Commentaires** — `%%`

Chaque bouton insère le code au curseur et ferme le panneau.

### Import / Export
| Format | Action |
|---|---|
| **Import .mmd** (`.mmd`, `.txt`, `.mermaid`) | Charge le fichier en mode personnalisé |
| **Export Code** | Télécharge le code source en `.mmd` |
| **Export SVG** | Télécharge le diagramme au format vectoriel |
| **Export PNG** | Télécharge le diagramme en haute résolution (2×) |

### Réinitialisation
- Bouton **Réinitialiser** : vide l'éditeur, réinitialise le zoom, efface le localStorage
- Confirmé par une modale pour éviter les pertes accidentelles
- Rétablit le schéma par défaut (`graph TB %% Saisissez votre code ici`)

### Protection contre la perte de données
- **Modale de confirmation** avant de charger un template si du code personnalisé non exporté existe dans `localStorage`
- **Modale de choix** (Dupliquer / Vierge) en passant d'un template au mode personnalisé
- **Modale de confirmation** avant réinitialisation

### Interface adaptative
- Panneaux redimensionnables par glisser-déposer (25 % – 75 %)
- Passage en colonnes sous 1024 px
- Icônes responsives (étiquettes visibles dès 700 px)
- Préférence `prefers-reduced-motion` respectée
- Accessibilité : rôles ARIA, `aria-label`, focus visible, modal focus trap

## Utilisation

1. Ouvrez `netschem.html` dans un navigateur moderne (Chrome, Firefox, Edge, Safari)
2. Choisissez un template dans la liste ou commencez à écrire du code Mermaid
3. Le diagramme se met à jour automatiquement dans le panneau d'aperçu
4. Utilisez le zoom, l'assistant syntaxe, et exportez votre travail

## Structure du projet

```
netschem.html        Application complète (HTML/CSS/JS embarqué, ~1500 lignes)
README.md            Documentation
```

## Dépendances (CDN)

- [CodeMirror 5.65.16](https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.16/) — Éditeur de code
- [Mermaid 10](https://cdn.jsdelivr.net/npm/mermaid@10/) — Rendu de diagrammes
- [Google Fonts](https://fonts.googleapis.com) — Inter & JetBrains Mono

Aucune autre dépendance. L'application fonctionne hors-ligne une fois les CDN chargés.

## Licence

Usage interne — Projet RSSI.
