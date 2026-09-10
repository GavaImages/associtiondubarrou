# Site — Association du Quartier du Barrou

Site web de l'association du quartier du Barrou à Sète, avec espace administrateur pour publier des annonces et gérer les activités.

## Contenu du dépôt

| Fichier         | Rôle                                                                 |
|-----------------|----------------------------------------------------------------------|
| `index.html`    | Le site complet (accueil, activités, actualités, association, contacts, espace admin) |
| `sitemap.xml`   | Plan du site pour les moteurs de recherche                           |
| `robots.txt`    | Instructions d'indexation pour les robots (Google, Bing, etc.)       |
| `404.html`      | Page personnalisée affichée si un visiteur tape une URL inexistante  |
| `README.md`     | Ce fichier — documentation                                           |

## Déployer sur GitHub Pages

1. Créer un dépôt GitHub **public** (ex : `lebarrou`)
2. Cliquer sur **Add file → Upload files**, glisser-déposer les 5 fichiers
3. **Commit changes**
4. Aller dans **Settings → Pages**
5. Sous **Source**, sélectionner : *Deploy from a branch* → `main` → `/ (root)` → **Save**
6. Attendre 1-2 minutes. L'URL apparaît en haut : `https://TON_PSEUDO.github.io/lebarrou/`

## Espace administrateur

Accessible via le lien **« Espace admin »** dans le pied de page.

**Comptes de démonstration** (mot de passe commun : `barrou2026`) :

| Identifiant | Nom affiché | Rôle             |
|-------------|-------------|------------------|
| `francoise` | Françoise   | Présidente       |
| `aline`     | Aline       | Vice-présidente  |
| `jo`        | Jo          | Secrétaire       |

**Fonctionnalités du tableau de bord** :
- Onglet **Événements** : créer, modifier, supprimer des annonces (avec photo optionnelle)
- Onglet **Activités** : gérer les activités régulières du quartier
- L'**auteur** est automatiquement rempli avec le nom du compte connecté

## Limite importante à connaître

Les annonces publiées via l'espace admin sont **stockées dans le navigateur de chaque visiteur** (technologie `localStorage`).

**Conséquence pratique** : chaque visiteur voit ses propres annonces. Si Françoise publie une news depuis son ordinateur, Aline ne la verra pas depuis le sien.

C'est parfait pour une **démonstration individuelle** (montrer aux membres du bureau comment ça marchera), mais **inadapté à un vrai site partagé**.

Pour un vrai site où toutes les annonces sont partagées, il faudra ajouter un backend. Solutions gratuites recommandées :
- **Supabase** (base de données PostgreSQL, 500 Mo gratuits) — le plus simple techniquement
- **Decap CMS** + Netlify — plus adapté aux non-techniciens qui publieront ensuite

## Référencement Google

Le site inclut déjà un référencement optimisé :
- Balises `<title>`, `<meta description>`, mots-clés
- **Open Graph** (Facebook, LinkedIn, WhatsApp) et **Twitter Card** pour un partage social soigné
- **Données structurées Schema.org** (type `NGO`) pour aider Google à comprendre qu'il s'agit d'une association locale
- **Balises géographiques** (`geo.region`, coordonnées GPS) pour le référencement local
- **Sitemap** et **robots.txt**
- Favicon personnalisé

### À faire pour activer le référencement

- [ ] Créer une image **`og-image.jpg`** de **1200 × 630 pixels** (visuel affiché lors du partage sur Facebook, WhatsApp, etc.) et la placer à la racine du dépôt. Idéalement une belle photo du quartier ou de l'étang.
- [ ] Inscrire le site sur [Google Search Console](https://search.google.com/search-console) pour lancer l'indexation et suivre les statistiques.
- [ ] Soumettre le sitemap dans Search Console (URL : `https://votre-domaine/sitemap.xml`).

## Utiliser un nom de domaine personnalisé (ex : lebarrou34.com)

Si tu veux que le site soit à `lebarrou34.com` plutôt qu'à l'URL github.io :

1. Dans le dépôt, créer un fichier nommé **`CNAME`** (sans extension) contenant simplement : `lebarrou34.com`
2. Chez ton hébergeur DNS (celui où tu as acheté lebarrou34.com), ajouter les enregistrements A/CNAME que GitHub demande (voir la doc officielle : https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site)
3. Dans **Settings → Pages**, saisir `lebarrou34.com` dans **Custom domain** et cocher **Enforce HTTPS**

**⚠️ Si tu utilises un domaine différent de lebarrou34.com**, il faudra mettre à jour ces trois fichiers :
- `sitemap.xml` — remplacer `https://lebarrou34.com/` par ton URL
- `robots.txt` — remplacer l'URL du sitemap
- `index.html` — dans les balises `<meta property="og:url">`, `<link rel="canonical">`, et le bloc JSON-LD (chercher `lebarrou34.com`)

## Points à finaliser avant mise en production

- [ ] Vérifier / compléter les coordonnées de l'association sur la page **Contacts** (le téléphone est en placeholder)
- [ ] Remplacer le bouton « Télécharger le bulletin d'adhésion » par un vrai lien vers un PDF
- [ ] Ajouter les vrais membres du bureau sur la page **Association**
- [ ] Compléter les pages Mentions légales, Politique de confidentialité, Accessibilité (placeholder dans le footer)
- [ ] Créer l'image `og-image.jpg` (voir référencement ci-dessus)
- [ ] Choisir un vrai mot de passe pour l'admin (⚠️ le mot de passe actuel `barrou2026` est visible dans le code source — ce n'est pas une vraie sécurité, seulement une barrière pour la démo)

## Mettre à jour le site

Pour modifier une page ou remplacer un fichier après la mise en ligne :
- Aller sur GitHub → dépôt → cliquer sur le fichier
- Cliquer l'**icône crayon** en haut à droite pour éditer en ligne
- Ou **Add file → Upload files** pour remplacer un fichier
- **Commit changes** → le site est à jour sous 1-2 minutes
