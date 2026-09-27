# NEO, multilingual edition

*[Version française plus bas](#version-française)*

This fork of [NEO](https://github.com/hughhowey/neo), Hugh Howey's distraction-free word processor for authors, adds one thing: **NEO can speak your language.** It ships in eight languages: English, French (reviewed by a native speaker), and Spanish, Portuguese, German, Italian, Dutch and Polish (machine-assisted, native-speaker review welcome). Any other language can be added with a single file, without programming.

Everything else is NEO, unchanged. English users see exactly the same app.

## Why this fork

NEO is a wonderful tool for writing books, but its interface was English-only, which kept it out of reach of many writers. The goal of this fork is to open it to authors who write in other languages, starting with French, while respecting NEO's philosophy: no bloat, nothing that interrupts the writer, plain files.

This work is offered to the original project. Hugh Howey is free to take all of it, part of it, or just the idea. The changes live on the [`i18n` branch](../../tree/i18n), kept clean so it can become a pull request at any time.

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
- **macOS**: no more duplicate "Enter Full Screen" in the View menu.

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

Ce fork de [NEO](https://github.com/hughhowey/neo), le traitement de texte épuré pour auteurs créé par Hugh Howey, ajoute une seule chose : **NEO parle votre langue.** Il est livré en huit langues : anglais, français (relu par un locuteur natif), ainsi qu'espagnol, portugais, allemand, italien, néerlandais et polonais (traductions assistées par IA, relecture par des natifs bienvenue). Toute autre langue s'ajoute avec un simple fichier, sans programmer.

Tout le reste, c'est NEO, inchangé. Les utilisateurs anglophones voient exactement la même application.

## Pourquoi ce fork

NEO est un formidable outil d'écriture, mais son interface n'existait qu'en anglais. L'objectif est de l'ouvrir aux auteurs d'autres langues, à commencer par le français, en respectant sa philosophie : pas de superflu, rien qui interrompe l'écriture, des fichiers simples.

Ce travail est proposé au projet d'origine : Hugh Howey est libre d'en reprendre tout, une partie, ou seulement l'idée. Les modifications se trouvent sur la [branche `i18n`](../../tree/i18n), gardée propre pour pouvoir devenir une pull request à tout moment.

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
- **macOS** : plus de doublon « Activer le mode plein écran » dans le menu Présentation.

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
