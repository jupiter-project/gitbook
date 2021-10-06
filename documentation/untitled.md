# Developer's Guide

### How can you contribute? <a id="how-can-you-contribute"></a>

* create pull requests
* review pull requests
* help users on issues
* ask us, info@jup.io

### Tools and Tips <a id="tools-and-tips"></a>

#### Usable URLs <a id="usable-urls"></a>

* **API** - [http://localhost:7876/test](http://localhost:7876/test)​
* **DB Interface** - [http://localhost:7876/dbshell](http://localhost:7876/dbshell)​
* **Java Class Browser** - [http://localhost:7876/doc](http://localhost:7876/doc)​

#### Database <a id="database"></a>

* H2 embedded database
* main database: `nxt_db/`
* test database: `nxt_test_db/`
* the database directories do not contain user specific data and can be safely deleted
* but no need to delete them on upgrade, the DbVersion code takes care of schema updates
* use the nxt.db framework when accessing the database from your code

### Coding Process <a id="coding-process"></a>

#### Branching Model <a id="branching-model"></a>

* ​[Vincent Driessen's Branching Model](http://nvie.com/posts/a-successful-git-branching-model/)​
* **tl;dr:**
  * master is release branch
  * dev is maintained by sigwo
  * releases/abc is maintained by Jupiter developers
  * feature/abc is yours

#### Design  <a id="design"></a>

* better think twice than code twice
* communicate with community and us

#### Implementation  <a id="implementation"></a>

* Coding Style
  * use the existing code as example for whitespace and indentation
  * the default settings of IntelliJ IDEA are good enough
  * make sure your code fits in
  * use \[IDE-Code-Style-Config\]
* Code should be self-documenting and readable, only special cases need comments
* The "Effective Java" book is a must read
* Some of the advice in "Clean Code" is good

#### Testing <a id="testing"></a>

* all API calls can be tested manually from the auto-generated [http://localhost:7876/test](http://localhost:7876/test) page
* many tests need blocks to be generated, see the examples how to fake the forging process
* write your tests against the http API or the public java API, which are relatively stable

#### Documentation <a id="documentation"></a>

* API calls should be documented first \(because if you don't, you never will\)

### UI Developers <a id="ui-developers"></a>

#### Where to Look <a id="where-to-look"></a>

* index.html: all of the html markup for pages and modals
* js/nrs.\*.js: corresponding js files for each task the file name displays, one roughly for each page
* js/nrs.modals.\*.js: The modal js \(popups\) for each set of popups, one for each set of modals
* any CSS: Bootstrap is used for the design, so changes to CSS rules should be generally avoided

#### Programming Style <a id="programming-style"></a>

* HTML style
  * Make sure to use the i18n for any text data, internationalization
  * Follow everything else as already set up by Wesley
* JS style
  * Same as above, just make the code fit into every other part
* Adding a page
  * Create a new html page markup in index.html, refer to other pages, starts with
  * Reference the page with a new link in the menu fixed to the left side of the page, from line 245 to 290 at time of writing
  * Create a corresponding js file in /js directory that handles all page specific scripting.
* Adding a modal
  * Create a new html modal also in index.html, the modals start around line 1750 at time of writing
  * It is fairly easy to make a modal based upon the information from other modals already created.

#### Translation  <a id="translation"></a>

**Language Translations**

Translation of the client UI to other languages is done by the community within a crowdsourced process on the platform **Crowdin**:

* ​[https://crowdin.com/project/nxt-ui-translation](https://crowdin.com/project/nxt-ui-translation)​

If you feel comfortable translating you are very welcome to join and help with translations.

**Coding**

On the development side, the `i18next` Javascript translation library is used for translation. Translations and associated translation keys can be added to the code in the following way:

* With `data-i18n` data attribute in HTML code, e.g. `<span data-i18n="send_message">Send Message</span>`
* Via `$.t()` function in JS, e.g. `$.t("send_message")`

Translation files can be found in the `locales` folder, base language is the english translation in `locales/en/translation.json`.

When adding new text/labeling visible in the UI do the following:

* Use one of the methods outlined above, choose an appropriate translation key
* Add both the key and the english text to the top of the english translation file
* Please don't use namespaces in your keys \(e.g. not `namespace.mynewkey`\) since this is complicating the filestructure of translation files when created automatically and cause problems when importing files to translation service
* If possible, don't use the `$.t()` function in a dynamic way \(e.g. `$.t(type + "_currency")`\), otherwise translation keys can't be extracted from the code
* If you later change the english text in the HTML please also change the text within the english translation file, otherwise the new english text is overwritten with the old english text from translation file
* DON'T USE TRANSLATION TEXTS CONTAINING HTML \(TAGGED WITH `[html]`\) FOR SECURITY REASONS!

**Updating base translation file**

The basis for other translations is the **English translation** file in `ui/locales/en/translation.json`. From time to time it might be necessary to collect translation keys forgotten to be added by developers systematically by using the i18next parser. To update the file with the latest keys and English base translations do the following:

1. Make a permanent backup of your `locales` folder outside of your Git repository
2. Count the rows of the English translation file, e.g. `wc -l ui/locales/en/translation.json`
3. To avoid intervening with 3rd party files create a temporary folder for files to be parsed `mkdir ui/trans-tmp/` \(`cp ui/js/*.* ui/trans-tmp/`, `cp -R ui/html ui/trans-tmp/`, `cp ui/*.html ui/trans-tmp/`\)
4. Parse translation strings not yet included in the English translation file with the i18next parser \(extra install\) with `i18next ui/trans-tmp -r -l en -o ui/locales/` \(if there is a strange "reuseSuffix" entry at the top of the file: this is a bug, delete!\)
5. There are dynamic uses of the `$.t()` function in the code base causing `i18next` to not detect all keys. If there is a generated `translation_old.json` file, don't throw these away. Instead add these strings manually to the `translation.json` file \(keep an eye on commas at the end of the lines!\)
6. Search for empty translation strings in English translation file forgotten by developers \(by searching for empty string ""\), full-text search in client folders for associated key and manually fill-in english string to translation file.

**Publish new base translations**

For providing new translation strings on the platform for the community to translate do the following:

1. Update the English base translation file \(see above guide\)
2. Build the Crowdin project \(permissions needed\) and make a backup download of the latest translations
3. Compare the number of translation keys in your generated file with the number of keys in the file on the Crowdin website and make sure, these fit together and there weren't any misses in the creation process \(don't be confused by Crowdin actually displaying "Words" count, you have to look at the "Settings -&gt; Reports" tab for comparison\)
4. Update the `translation.json` file on Crowdin
5. Inform the community about new translation tasks

**Integrating new translations into the client**

1. Build/download the latest translation files from Crowdin \(permissions needed\) and replace the language folders like `fa`, `pt-BR`,... with the folders downloaded. Please make sure to NOT touch the English folder `en`.
2. Rename all folder names to lowercase, e.g. `es-ES` to `es-es`.
3. Make some consistency checks \(lengths of old/new files, "git diff" on language files\)
4. New languages can be added to `NRS.languages` in `ui/js/nrs.settings.js` file. Review the status of the languages \(40-50%+ Experimental, 70-80%+ Beta, 90-95%+ Stable\), eventually add new languages

