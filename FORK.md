# NEO, multilingual edition

*[Version française plus bas](#version-française)*

> **Now part of NEO.** The translations were merged by Hugh Howey and shipped in **NEO 0.9.0** ([#94](https://github.com/hughhowey/neo/pull/94)), along with the macOS menu fix ([#95](https://github.com/hughhowey/neo/pull/95)). Download NEO from [its own releases page](https://github.com/hughhowey/neo/releases). The translated shortcuts window followed ([#108](https://github.com/hughhowey/neo/pull/108)). Accessibility ([#111](https://github.com/hughhowey/neo/pull/111)) and the translated update messages were merged too. This fork now carries what is offered next: prologue and epilogue ([#110](https://github.com/hughhowey/neo/pull/110)).

This fork of [NEO](https://github.com/hughhowey/neo), Hugh Howey's distraction-free word processor for authors, adds one thing: **NEO can speak your language.** It ships in eight languages: English, French (reviewed by a native speaker), and Spanish, Portuguese, German, Italian, Dutch and Polish (machine-assisted, native-speaker review welcome). Any other language can be added with a single file, without programming.

Everything else is NEO, unchanged. English users see exactly the same app.

## Why this fork

NEO is a wonderful tool for writing books, but its interface was English-only, which kept it out of reach of many writers. The goal of this fork is to open it to authors who write in other languages, starting with French, while respecting NEO's philosophy: no bloat, nothing that interrupts the writer, plain files.

This work is offered to the original project. Hugh Howey is free to take all of it, part of it, or just the idea. The translations lived on the [`i18n` branch](../../tree/i18n) and were merged as [pull request #94](https://github.com/hughhowey/neo/pull/94). Each later addition has its own branch, offered one at a time.

It was built with the help of Claude (Anthropic's AI assistant), then tested and reviewed by a French novelist who uses NEO.

## What changes for writers

- **View → Language** menu. On first launch, NEO follows the system language when a translation exists. Switching language saves the open book and reopens it in the new language.
- **The whole interface is translated**: menus, dialogs, messages, tooltips, the shortcuts sheet, the empty-field hints, the first-run welcome.
- **Each language's typography while typing**: « » in French, Spanish, Italian and European Portuguese, „ “ in German, „ ” in Polish, “ ” in English, Dutch and Brazilian Portuguese.
- **Regional variants**: a region only lists what differs from its language (`fr-CA` → `fr` → English). Canadian French and European Portuguese are included; Belgian and Swiss French use the base French.
- **Numbers and plurals follow the language** ("1 mot", "1 234 mots" in French).
- **Exports follow the language**: chapter headings ("Chapitre 1"), EPUB table of contents and landmarks, "by / par" on title pages, the EPUB language tag.
- **French typography while typing** (when NEO is in French, or the spellcheck language is French): « guillemets » with no-break spaces, the ’ apostrophe, and a narrow no-break space before ; : ! ? It works in the manuscript, titles, outline and notes.
- **Import understands French manuscripts**: "Chapitre", "Partie", "Épilogue" headings and "par Auteur" bylines are recognized.
- **French cover titles set better**: French small words (de, la, les, du…) are treated like "of" and "the" when the cover title is laid out.
- **Small fixes that help every language**: word counts ignore lone punctuation (« », a spaced dash); the shortcuts sheet aligns its columns for longer labels; standard menu items (Undo, Copy, Quit…) are labelled in the chosen language.

## Also in this fork

- **Prologue and epilogue**: right-click the first chapter's heading to make it a prologue, or the last one's to make it an epilogue. They step out of the numbering (the next chapter becomes Chapter 1) everywhere, including exports; imported manuscripts keep their Prologue / Epilogue headings. On its own branch, [`prologue-epilogue`](../../tree/prologue-epilogue), to be offered separately.
- **macOS**: no more duplicate "Enter Full Screen" in the View menu ([pull request #95](https://github.com/hughhowey/neo/pull/95)).
- **Accessibility** (on its own branch, [`accessibility`](../../tree/accessibility)):
  - **View → Brighter Interface** is now a checkbox, and turns on by itself when the system asks for more contrast (macOS "Increase contrast", Windows contrast themes). In it, every text, hint and placeholder reaches the 4.5:1 contrast that WCAG and France's RGAA ask for, on paper and at night. In the other languages it is named for what it does (Contraste renforcé, Erhöhter Kontrast…).
  - **View → Interface Size**: Normal, 125%, 150% or 200%. The shelf, panes, bottom bar and dialogs grow together; the page keeps its own size. No interface text is smaller than 12px any more.
  - At rest, the interface text that carries information (note labels, word counts, outline numbers, empty-tab messages) reads at 4.5:1 too. NEO's quiet look stays: the bottom bar still fades until you reach for it.
  - **Keyboard**: F6 or ⌃Tab moves between the page, the chapters, the notes and the bottom bar (add ⇧ to go backwards, Esc back to the page); on the shelf, between the books and the header. On a Mac, F6 needs fn; ⌃Tab works as is. Books, chapters, tabs and counters answer to Tab, Enter and Space. A gold ring shows where the keyboard is.
  - **Screen readers**: named buttons and regions, tabs with their state, named chapters, dialogs announced as dialogs, the progress chart described.
  - The system's "Reduce motion" stills fades and slides; Windows high-contrast mode is supported.

## How it works

- **No dependencies, no framework.** A small helper, `i18n.js` (about 80 lines), is shared by the window and the main process.
- **The English text is the key**: `t('Cancel')`. The code stays readable, and a missing translation simply shows the English original.
- **One language = one file** in `locales/`: `fr.json` maps each English string to its translation. `en.json` holds English plural forms. The Language menu lists whatever files are present.
- **Plurals** use the standard Unicode rules (`Intl.PluralRules`), so languages with several plural forms are supported.
- **Tooling**: `node scripts/i18n.js template` regenerates `locales/_template.json` (every string, ready to translate); `node scripts/i18n.js check fr` lists missing strings and broken `{placeholders}`.
- **Books stay portable**: default names (the "Notes" and "Outline" tabs) are stored in English and shown translated, so a book opens correctly whatever the language.

## Files changed

| File | Change |
|---|---|
| `i18n.js` | New: the translation helper |
| `locales/*.json` | New: English plurals; French, Spanish, Portuguese, German, Italian, Dutch, Polish (about 420 strings each); Canadian French and European Portuguese differences |
| `locales/_template.json` | New: blank template for translators |
| `scripts/i18n.js` | New: template generator and coverage check |
| `TRANSLATING.md` | New: how to add a language |
| `app.js` | Every visible string wrapped in `t()`; French typography; language switch |
| `main.js` | Menus and dialogs translated; Language menu; language setting in `settings.json`; French import headings |
| `preload.js` | Passes the translations to the window before it starts |
| `index.html` | Static texts marked with `data-i18n` attributes |
| `styles.css` | Empty-field hints read from translatable variables; help sheet column |
| `covers.js` | French small words on covers; translated "Untitled" |
| `README.md`, `package.json` | Languages section; translation tools kept out of builds |

The mobile companion (`pocket/`) is not translated yet.

## Try it

```
git clone -b i18n https://github.com/sebastienpiconnier/neo.git
cd neo
npm install
npm start
```

Then choose **View → Language → Français**.

## Add a language

Copy `locales/_template.json` to `locales/<code>.json` (for example `es.json`), set the language's own name in `_meta.name`, translate the values, and run `node scripts/i18n.js check <code>`. Full guide: [TRANSLATING.md](TRANSLATING.md).

---

# Version française

> **Désormais intégré à NEO.** Hugh Howey a fusionné les traductions, publiées dans **NEO 0.9.0** ([n° 94](https://github.com/hughhowey/neo/pull/94)), avec le correctif du menu macOS ([n° 95](https://github.com/hughhowey/neo/pull/95)). Téléchargez NEO sur [sa propre page de versions](https://github.com/hughhowey/neo/releases). La fenêtre des raccourcis traduite a suivi ([n° 108](https://github.com/hughhowey/neo/pull/108)). L'accessibilité ([n° 111](https://github.com/hughhowey/neo/pull/111)) et la traduction des messages de mise à jour ont aussi été fusionnées. Ce fork porte maintenant la proposition suivante : le prologue et l'épilogue ([n° 110](https://github.com/hughhowey/neo/pull/110)).

Ce fork de [NEO](https://github.com/hughhowey/neo), le traitement de texte épuré pour auteurs créé par Hugh Howey, ajoute une seule chose : **NEO parle votre langue.** Il est livré en huit langues : anglais, français (relu par un locuteur natif), ainsi qu'espagnol, portugais, allemand, italien, néerlandais et polonais (traductions assistées par IA, relecture par des natifs bienvenue). Toute autre langue s'ajoute avec un simple fichier, sans programmer.

Tout le reste, c'est NEO, inchangé. Les utilisateurs anglophones voient exactement la même application.

## Pourquoi ce fork

NEO est un formidable outil d'écriture, mais son interface n'existait qu'en anglais. L'objectif est de l'ouvrir aux auteurs d'autres langues, à commencer par le français, en respectant sa philosophie : pas de superflu, rien qui interrompe l'écriture, des fichiers simples.

Ce travail est proposé au projet d'origine : Hugh Howey est libre d'en reprendre tout, une partie, ou seulement l'idée. Les traductions se trouvaient sur la [branche `i18n`](../../tree/i18n), fusionnée sous forme de [demande de fusion n° 94](https://github.com/hughhowey/neo/pull/94). Chaque ajout suivant a sa propre branche, proposée une à la fois.

Il a été réalisé avec l'aide de Claude (l'assistant IA d'Anthropic), puis testé et relu par un romancier français qui utilise NEO.

## Ce qui change pour l'auteur

- **Menu Présentation → Langue.** Au premier lancement, NEO suit la langue du système. Changer de langue enregistre le livre ouvert et le rouvre dans la nouvelle langue.
- **Toute l'interface est traduite** : menus, fenêtres, messages, infobulles, aide des raccourcis, indications des champs vides, accueil.
- **La typographie de chaque langue à la frappe** : « » en français, espagnol, italien et portugais européen, „ “ en allemand, „ ” en polonais, “ ” en anglais, néerlandais et portugais du Brésil.
- **Variantes régionales** : une région ne contient que ses différences (`fr-CA` → `fr` → anglais). Le français canadien et le portugais européen sont inclus ; le français de Belgique et de Suisse utilise le français de base.
- **Nombres et pluriels à la française** : « 1 mot », « 1 234 mots ».
- **Les exports suivent la langue** : « Chapitre 1 », table des matières EPUB, « par » sur la page de titre, langue déclarée dans l'EPUB.
- **Typographie française à la frappe** : « guillemets » avec espaces insécables, apostrophe ’, espace fine insécable avant ; : ! ? Dans le manuscrit comme dans les titres, le plan et les notes.
- **L'import comprend les manuscrits français** : titres « Chapitre », « Partie », « Épilogue » et mention « par Auteur ».
- **Couvertures** : les petits mots français (de, la, les, du…) sont mis en page comme « of » et « the ».
- **Vocabulaire** : Darlings devient **Chutier**, Pantser / Plotter deviennent **Jardinier / Architecte**.

## Aussi dans ce fork

- **Prologue et épilogue** : un clic droit sur le titre du premier chapitre en fait un prologue, sur celui du dernier un épilogue. Ils sortent de la numérotation (le chapitre suivant devient le chapitre 1) partout, exports compris ; les manuscrits importés gardent leurs titres Prologue / Épilogue. Sur sa propre branche, [`prologue-epilogue`](../../tree/prologue-epilogue), pour être proposé séparément.
- **macOS** : plus de doublon « Activer le mode plein écran » dans le menu Présentation ([demande de fusion n° 95](https://github.com/hughhowey/neo/pull/95)).
- **Accessibilité** (sur sa propre branche, [`accessibility`](../../tree/accessibility)) :
  - **Présentation → Contraste renforcé** (anciennement « Interface plus lumineuse ») devient une case à cocher, et s'active d'elle-même quand le système demande plus de contraste (« Augmenter le contraste » sur macOS, thèmes de contraste sur Windows). Tous les textes, indications et zones vides y atteignent le contraste de 4,5:1 demandé par le WCAG et le RGAA, sur papier comme de nuit.
  - **Présentation → Taille de l'interface** : normale, 125 %, 150 % ou 200 %. Bibliothèque, panneaux, barre du bas et fenêtres grandissent ensemble ; la page garde sa propre taille. Plus aucun texte d'interface sous 12 px.
  - Au repos, les textes d'interface qui portent une information (étiquettes des notes, nombres de mots, numéros du plan, messages des onglets vides) atteignent aussi 4,5:1. L'esprit discret de NEO demeure : la barre du bas reste estompée tant qu'on ne va pas la chercher.
  - **Clavier** : F6 ou ⌃Tab passe de la page aux chapitres, aux notes et à la barre du bas (avec Maj en arrière, Échap revient à la page) ; dans la bibliothèque, des livres à l'en-tête. Sur Mac, F6 demande la touche fn ; ⌃Tab marche tel quel. Livres, chapitres, onglets et compteurs répondent à Tab, Entrée et Espace. Un anneau doré montre où se trouve le clavier.
  - **Lecteurs d'écran** : boutons et zones nommés, onglets avec leur état, chapitres nommés, fenêtres annoncées comme telles, graphique de progression décrit.
  - « Réduire les animations » du système fige fondus et glissements ; le mode contraste élevé de Windows est pris en charge.

## Essayer

```
git clone -b i18n https://github.com/sebastienpiconnier/neo.git
cd neo
npm install
npm start
```

Puis **Présentation → Langue → Français**.

## Ajouter une langue

Copiez `locales/_template.json` en `locales/<code>.json`, indiquez le nom de la langue dans `_meta.name`, traduisez les valeurs, puis lancez `node scripts/i18n.js check <code>`. Guide complet (en anglais) : [TRANSLATING.md](TRANSLATING.md).
