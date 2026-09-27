# NEO

*[Read in English](README.md)*

> **Édition multilingue.** Ce fork ajoute la traduction de l'interface de NEO (anglais et français). [Présentation du fork](FORK.md#version-française). Le texte ci-dessous est la traduction du README de Hugh Howey, l'auteur de NEO : c'est lui qui parle.

**Un traitement de texte sans distraction pour les auteurs, par un auteur en herbe.**

Dès son installation, NEO sait que vous écrivez des *livres*, et rien d'autre. Pas de superflu, pas de distractions, et des manuscrits qui ressemblent à des livres pendant que vous les écrivez.

NEO fonctionne en local. Vos textes en cours sont enregistrés sous forme de fichiers simples sur votre disque. Pas de compte, pas d'abonnement. Et c'est gratuit !

## Télécharger

Récupérez le dernier installateur sur la **[page des versions](../../releases)** :

- **macOS** : téléchargez le `.dmg` pour les anciens Mac Intel ou le fichier arm64 pour les Mac Apple Silicon. Ouvrez-le et glissez NEO dans Applications.
- **Windows** : téléchargez le `.exe` et lancez-le. Ou récupérez l'installateur (setup) et lancez-le.
- **Linux** : téléchargez le `.AppImage`, rendez-le exécutable et lancez-le :

  ```
  chmod +x NEO-*.AppImage
  ./NEO-*.AppImage
  ```

  S'il se plaint d'une sandbox (fréquent sous Ubuntu 24.04 et versions suivantes), lancez-le avec `./NEO-*.AppImage --no-sandbox`. Votre bibliothèque se trouve dans `~/Documents/NEO Library` ; Fichier → Dossier de la bibliothèque… permet de la déplacer où vous voulez.

## Pourquoi NEO ?

**La bibliothèque**

Votre bibliothèque ressemble à des étagères, pas à une liste de fichiers. Des étagères étiquetées, organisées comme bon vous semble : par série, par état d'avancement, par nom de plume. Des barres de progression sur les couvertures montrent où vous en êtes de vos objectifs de mots. Vous pouvez glisser-déposer les livres n'importe où, déplacer les étagères et habiller vos titres d'une couverture.

**Juste une page blanche**

Une page blanche par défaut, ou un mode sombre (que je préfère désormais !). Les commandes s'estompent tant que la souris ne les survole pas. Les chapitres se numérotent et se renumérotent tout seuls. Des lettrines marquent le début des chapitres, parce que j'adore les lettrines. Tirets, vrais points de suspension et guillemets typographiques se mettent en place pendant la frappe (à la française quand NEO est en français). La correction orthographique n'apparaît que lorsque vous la demandez : fini les soulignés rouges en pleine phrase qui réveillent votre syndrome de l'imposteur.

**Entrée, Entrée, Entrée**

Une fois Entrée : nouveau paragraphe. Deux fois : un saut de section `***`. Trois fois : un nouveau chapitre. Le but, c'est de CONTINUER À ÉCRIRE.

Un clic droit sur le titre du premier chapitre en fait un prologue, sur celui du dernier un épilogue : ils sortent de la numérotation, et tout se renumérote.

**Le Chutier**

Le conseil d'écriture dit « tuez vos darlings », ces passages auxquels on tient trop. Moi je dis : *gardez les corps*. Glissez n'importe quel passage beau mais encombrant sur l'onglet Chutier. Il quitte votre manuscrit sans être perdu, et se restaure exactement à l'endroit d'où il vient. Des zombies plus que des darlings.

**Les repères**

En plein élan et il vous manque un nom, un fait, une date ? ⌘⇧X pose une marque et une note. Le panneau de gauche affiche un point rouge sur chaque chapitre où vous devez revenir. Le panneau de droite liste toutes ces choses à faire.

**Le plan, pour les architectes**

Faites le plan de vos chapitres et sections dans l'onglet Plan ; les notes de section apparaissent dans le manuscrit sous forme de paragraphes fantômes grisés, prêts à être remplacés par le texte. Les jardiniers peuvent tout ignorer, ou apprendre à dessiner une fichue carte pour la première fois. Essayez. Vous pourriez aimer ça !

**Les couvertures**

Chaque livre a sa couverture ! Les nouveaux livres reçoivent une composition abstraite générée (six styles graphiques, six modèles typographiques, polices fournies avec NEO), si bien que deux histoires ne se ressemblent jamais sur l'étagère. Dès qu'une histoire dépasse 1 000 mots, NEO peut la lire et peindre une couverture abstraite à partir du texte. Cela demande un peu plus de travail mais en vaut vraiment la peine. Obtenez une clé d'API sur le site d'OpenAI et collez-la dans **Fichier → Couverture…**. L'image est générée en arrière-plan pour environ un centime. (Ces images ne sont pas destinées à la publication, seulement à inspirer l'écriture !) La clé d'API est stockée chiffrée dans les réglages de NEO, jamais dans le dossier de votre bibliothèque. Le titre et l'auteur sont toujours composés en vraie typographie par-dessus, le lettrage n'est donc jamais confié à une IA générative. Le ↻ sur chaque livre change sa typographie et ses couleurs, ou le repeint. Et vous pouvez toujours passer du style abstrait moderne à la version peinte, et inversement.

**Objectifs et élan**

Objectifs de mots quotidiens, sprints d'écriture et courbe de progression à la façon du NaNoWriMo. Ça mérite encore des tests, mais je crois que ça marche plutôt bien !

**Les exports**

EPUB 3 avec une vraie table des matières conforme aux recommandations de KDP, Word .docx, PDF, HTML, Markdown et texte brut. Envoyez-vous par e-mail un instantané PDF horodaté, avec une empreinte SHA-256 du texte dans le corps du message. Ça pourrait servir un jour.

**L'import**

Importez vos manuscrits .docx, .txt et .md existants ; chapitres et sauts de section sont détectés automatiquement. C'est encore un peu brut et vous devrez peut-être retoucher certaines choses. NEO essaie de récupérer votre titre et de le retirer du corps du texte, et cela semble plutôt bien fonctionner.

**Les sauvegardes**

Enregistrement continu, sauvegardes zip quotidiennes conservées deux semaines, tout est stocké en fichiers simples. Placez le dossier de votre bibliothèque NEO sur iCloud si vous voulez plus de sécurité. Vous pouvez aussi vous envoyer une copie de votre texte en cours par e-mail d'une seule touche : ⌘E.

## Vos fichiers

Tout se trouve dans `~/Documents/NEO Library` : un dossier par livre, les chapitres en HTML lisible, les métadonnées en JSON. Ouvrez-les dans votre éditeur de texte préféré.

## Langues

NEO parle anglais, français, espagnol, portugais, allemand, italien, néerlandais et polonais. Choisissez dans **Présentation → Langue** ; au premier lancement, NEO suit la langue de votre système quand il la connaît. Ajouter une langue tient en un seul fichier, sans programmation : voir [TRANSLATING.md](TRANSLATING.md) (en anglais).

## Compiler depuis les sources (pour les curieux)

Nécessite [Node.js](https://nodejs.org).

```
git clone -b i18n https://github.com/sebastienpiconnier/neo.git
cd neo
npm install
npm start
```

Pour fabriquer les installateurs : `npm install electron-builder --save-dev`, puis `npm run package` (macOS), `npm run package:win` (Windows) ou `npm run package:all`. Le résultat arrive dans `dist/`.

L'application est très simple : une coque Electron (`main.js`), un pont de préchargement (`preload.js`) et l'interface (`app.js` + `styles.css` + `index.html`). Si vous connaissez JavaScript, vous pouvez modifier NEO. Allez-y.

## Feuille de route (des idées dont je rêve mais que je ne réaliserai peut-être jamais)

Historique des versions de chapitre · format de manuscrit pour les soumissions aux agents (Times New Roman, double interligne, bloc d'adresse, juste pour faire plaisir à Kristin Nelson) · pages de fin communes mises à jour dans tous les livres d'un coup (idem pour les pages de copyright, les biographies, etc.).

## Contribuer

Les issues et les pull requests sont les bienvenues : voir [CONTRIBUTING.md](CONTRIBUTING.md) (en anglais). Je préviens : NEO a des partis pris assumés, et le superflu a tué toutes les applications d'écriture que j'ai essayées. Si vous voulez quelque chose de complexe, essayez Scrivener. C'est vraiment une excellente application, adorée par beaucoup ! Il existe tant de merveilleuses applications d'écriture ! Personne n'a besoin d'utiliser celle-ci, à part moi.

## Licence

[MIT](LICENSE) : libre d'utilisation, de modification et de partage.

## Philosophie

Au cas où vous ne le sauriez pas, j'ai ouvert l'univers de Silo à la fan fiction il y a des années. Et pas seulement pour la publier sur des sites de fan fiction : vous pouvez vendre ce que vous écrivez et garder chaque centime ! Il existe beaucoup d'incroyables histoires de Silo. Mais les lecteurs en redemandent toujours.
