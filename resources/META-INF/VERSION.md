## Markdown Navigator

[TOC levels=3,6]: # "Version History"

### Version History
- [2.2.0.8 - Compatibility & Enhancement Release](#2208---compatibility--enhancement-release)
- [2.2.0 - Compatibility & Enhancement Release](#220---compatibility--enhancement-release)
- [2.1.1 - Bug Fix & Enhancement Release](#211---bug-fix--enhancement-release)
- [2.1.0 - Bug Fix Release](#210---bug-fix-release)
- [2.0.0 - New Parser Release](#200---new-parser-release)


<!--![TOC Demo](https://github.com/vsch/idea-multimarkdown/raw/master/assets/images/noload/TOCDemo.gif) -->

&nbsp;<details id="todo"><summary>**To Do List**</summary>

##### This Release To Do

* [ ] Add: Copy Rendered Markdown to HTML mime format to allow composing e-mails in plugin and
      pasting to apple mail.
* [ ] Fix: `[flexmark icon logo]: raw/master/assets/images/flexmark-icon-logo.png` shows as
      unresolved by annotator but completes fine and inline link with same URL does not show as
      unresolved.
* [ ] Add: when typing in the text field for change link to reference, automatically enable the
      add reference text if reference id is different from original
* [ ] Fix: on ENTER when removing item prefix should not insert a blank line
* [ ] Fix: Header marker equalization
* [ ] Add: paste image into document, use content preview and replace whatever is selected or
      under caret not just full links. Default to reuse the name at caret. Directory to be
      configurable by scope of the destination file.
* [ ] Add: transpose table, best to copy to clipboard transposed table
* [ ] Add: update parser configuration to new flexmark-java options.
* [ ] Add: wrap on typing to respect the `@formatter:off`/`@formatter:on` tagging by searching
      for HTML Comment Block in the `PsiFile` at file level (not embedded in other elements)
      located before caret line. First one with `@formatter:on` or `@formatter:off` setting
      wins.
* [ ] Add: all inline toggling actions to take punctuation characters that they will not wrap by
      default if caret is on them or the current word to wrap ends on one of them: `.,;:!?`. If
      the caret is right after one of them then default behavior should be to wrap the word
      immediately before the punctuation char.
* [ ] Change: change inline code action to work just like bold, italic and strike through,
      instead of continuously adding back ticks.
* [ ] Fix: Swing preview HTML table has body row count reset or reversed so first row is like
      heading.
* [ ] Add: TOC option to wrap generated TOC in `&nbsp;<details id="todo"><summary>Toc
      Title</summary>` and `&nbsp;<details>` so it is collapsible. Add this parsing option to
      flexmark-java to parse this format.
* [ ] Add: format option to sort task lists with completed ones last, leaving the order
      otherwise unchanged.
* [ ] Add: parser emulation family to parser configuration
* [ ] Add: parser profile needs to be passed to functions handling formatting and prefix
      generation. Now this can vary significantly from one parser family to another.
* [ ] Fix: when ENTER deletes a list item prefix inserts extra blank line
* [ ] Add: option to disable all smart typing and handlers with an action or toolbar button
* [ ] Add: Copy to YouTrack button similar to copy to Jira
* [ ] Fix: for parsing purposes make all bullets interrupt all paragraphs. This will eliminate
      the possibility of wrap on typing will merge a block of list items when one of them is
      edited to non-list item, as it does now.
* [ ] Add: option for escaping special cases for `*`, `-`, `+`, `#` _`N.`_ where _N_ is numeric
      with a `\` so that it is not mis-interpreted as a special char at first non-blank of a
      wrapped line. If one is found in such a position then it should be annotated with a
      warning and a quick fix to escape it, unless it is the first non-blank of the list item's
      text. The `#` affects current implementation but should only be escaped if it lands
      exactly on the items child indent position, if parser rules don't allow leading spaces
      before ATX headings.
* [ ] Add: join processor to remove bullet list marker when joining next line item
* [ ] Fix: CommonMark and Commonmark to CommonMark
* [ ] Add: CommonMark 0.27 compliant flexmark-java
* [ ] Add: other parser profiles and appropriate options to allow using these:
      * [ ] CommonMark: GitHub Comments
      * [ ] Kramdown: GitHub Docs, GitHub Wiki Pages, Jekyll
      * [ ] FixedIndent: MultiMarkdown, PanDocs, Pegdown
* [ ] Add: `PARSE_JEKYLL_MACROS_IN_URLS` option for parser and to Parser settings to enable
      parsing of jekyll macros in urls with spaces between macro and braces.
* [ ] Fix: cursor navigation very slow in table with few rows but very long text in columns: see
      `Extensions.md` in `flexmark-java` wiki. Suspect is figuring out table context for toolbar
      button state update.
* [ ] Fix: inserting list item above in a loose list should not insert blank line below current
      item since we are inserting above and not affecting the current item.
* [ ] Add: List syntax dependent list item action behavior.
      - [x] Add: flexmark option to recognize empty list sub-items option to PARSER purpose.
      - [x] Fix: psi list item prefix reporting to match fixed4, github and CommonMark list
            processing settings.
      * [x] Fix: list indent for nested items should not indent to more than (listLevel)*4 + 3
            in fixed 4 mode, and check if also in GitHub compatible mode
      - [ ] Fix: indent/un-indent for other than fixed 4 has to re-indent child items to the
            parent's new indent level. Otherwise parsing of the children will be off. Right now
            works only for fixed4
* [ ] Add: List syntax dependent list format behavior.
      * [ ] GitHub enforces styleSettings.LIST_ALIGN_CHILD_BLOCKS and has a maximum for prefix
            marker start
      * [ ] CommonMark enforces styleSettings.LIST_ALIGN_CHILD_BLOCKS and have no maximum for
            prefix as long as it matches the parent item's content indent
- [ ] Fix: Un-indent item action leaves leading indent if it was aligned to parent's left text
      edge.

##### Next Release To Do

* [ ] Add: state persistence for JavaFX script parameters and modify the `details` opener and
      Collapse Markdown scripts to use these for initializing the open/close state.
* [ ] Add: save the persistence for JavaFX with the document state so that it is restored when
      the document opens.
* [ ] Fix: When pasting text that contains ref links over a selection that already has these
      references, after the paste the references are deleted but new ones are not added. Put a
      check if possible to ignore any existing references in a selection since they will be
      deleted by the paste.
* [ ] Fix: can't modify PSI inside on save listener.

----

* [ ] Add: GitHub links should offer the same change relative/http: intention as the rest of the
      links.
* [ ] Fix: HRule colors the whole line even when it is in a list item
* [ ] Fix: SimToc requires default settings so that rendering will reflect project settings not
      defaults of flexmark-java SimToc extension. For now renders what is in the document.
* [ ] Fix: Link Map
      * [ ] implement `ExpandedItemRendererComponentWrapper` for table cells so that the
            extended tooltip does not hide an error tooltip.
* [ ] Add: option to escape special chars when they migrate to the beginning of a line and away
      from the beginning of a line after wrapping. Simpler to un-escape them if they are escaped
      before wrap and re-escape any at the beginning of a line.
* [ ] Add: ability to move a lookup-up to the start of an element's location so that completions
      for emoji shortcuts and links located in heading elements can be properly aligned.
* [ ] Fix: take a look at the toolbar implementation to see if it can be made to put in a drop
      down for buttons that don't fit.
* [ ] Add: source synchronization for Swing preview window
* [ ] Add: source synchronization for HTML plain text previews
- [ ] Add: a CommonMark profile and compatible options in settings
* [ ] Add: detection for **GitHub** issue completions when no task servers are defined.

&nbsp;</details>

### 2.2.0.8 - Compatibility & Enhancement Release

* Add: `Copy markdown document or selection as HTML mime formatted text` action that will copy
  document or selection to the clipboard in HTML format that will paste as formatted text into
  applications that handle HTML formatted text. Useful for pasting rendered markdown in e-mails.
  To override the default styles and parser options for rendered HTML create a profile named
  `COPY_HTML_MIME` and override CSS Text. Use
  `/com/vladsch/idea/multimarkdown/html_mime_default.css` as a starting template. All style
  settings must be contained in a single matching entry since they are set in each element and
  there is no stylesheet and the "css" text is parsed and its style added to the element's style
  attribute. The "parent" selector is based on Markdown AST hierarchy and not actual HTML which
  at the time attributes are applied does not exist, so any HTML tags surrounding Markdonw
  elements will have no effect. Also the classes are hardcoded into the attribute provider such
  as: `tr.odd`, `tr.even` and `li.loose` based again on Markdown AST.
* Add: option to not load GIF images, later if possible to not animate them just display the
  first frame. Really messes up preview and scrolling. Even crashed PhpStorm needing a power
  down because it would not be killed. Same with IDEA but force quit worked.
* Fix: In profiles Stylesheet and HTML override project settings options were reversed in the
  code. Html controlled Stylesheet and Stylesheet controlled HTML.
* Fix: Copy Jira and YouTrack heading would not have text if `Anchor Links` parser option was
  selected.
* Add: option to not load GIF images, later if possible to not animate them just display the
  first frame. Really messes up preview and scrolling. Even crashed PhpStorm needing a power
  down because it would not be killed.
* Add: formatter control tags support
* Add: Copy YouTrack formatted text, like Jira but with differences
* Fix: Copy Jira formatted text adding extra blank line in block quote
* Add: fenced/indented code trailing space trimming options.
* Add: flexmark-java flexmark example trailing space trimming options.
* Add: fenced code style option `Space before language info` to put a space between opening
  marker and language info string
* Fix: disable backspace, enter and typed character handlers in multi-caret mode.
* Add: multi-invoke for inline code completion to select fully qualified names or just simple
  names. Make simple name the default. Very annoying to get full names in docs.

### 2.2.0 - Compatibility & Enhancement Release

#### Basic & Enhanced Editions

- Add: markdown live template for collapsible details mnemonic `.collapsed`
- Add: option in settings to hide disabled buttons
- Change: move disable annotations from debug to document settings.
- Fix #335, Markdown Navigator breaks the line end whitespace trimming feature of EditorConfig
- Change: remove all **pegdown** dependencies
- Change: remove tab previews and enable split editor for basic edition, with fixed position
  restoring.
- Add: basic version now has split editor
- Fix: Slow scrolling with JavaFX WebView, was also causing unacceptable typing response for
  files of 500+ lines. Caused by WebView handling of CSS parameters not code.
- Fix: reimplemented JavaFX WebView integration with interruptible rendering to favour typing
  response.
- Add: #225, code highlight line number via Prism.js highlighter option
- Fix: #313, Changing fonts causes WebStorm to freeze
- Add: #316, Make shared settings Project specific
- Fix: #315, NullPointerException with v2016.3 EAP (163.6110.12)
- Fix: Implement multi-line URL image links in flexmark-java
- Fix: #327, IntelliJ IDEA 2016.3 EAP API change incompatibility.
- Fix: #328, wiki link can use ` `, `-`, `+`, `<` or `>` to match a `-` in the file name. Added
  stub index for links to make file reference search efficient.
- Change: document icons to match 2016.3 style

#### Enhanced Edition

* Fix: Rename refactoring of referencing elements broken by stub index work
* Add: JavaFX WebView script provider `Details tag opener` to open all `<details>` tags in
  preview so the content can be seen while editing
* Add: collapsible headers and markdown scripts
* Fix: setting change export now forces to re-export files in case some settings changed that
  affect the content of exported files.
* Change list toolbar icons to be simpler and more distinguishable. they all look alike.
* Add: link map move up/down groups within tree node
* Add: link map add quick fix to move errant mapping group to `unused` link type so config can
  be saved.
* Add: jekyll templates by adding an option to create a initial content when creating a mapping
  text group: empty, sample1,... each sample is based on element type
* Fix: splitting a line right after list item marker would be inconsistent and not result in a
  new list item above the current one.
* Fix: bump up the index file version numbers
* Change: disabled swing synchronization until it works properly
* Add: warning that prism syntax highlighter slows typing response also added for Fire Bug Lite
* Fix: document format would sometimes wrap early.
* Fix: swing css files not to have embedded `<` in comments to eliminate `Unterminated Comment`
  exception when using `Embed stylesheet URL content` option in HTML Generation with Swing
  browser
* Fix: swing browser pane to process HTML header for stylesheet links and load them. Now Swing
  browser can be used with exported HTML documents and a fast way to play with Swing stylesheet
  by embedding it in the HTML to get live update in the preview.
* Add: warning to Prism.js and Fire Bug Lite that they can affect preview display and typing
  response.
* Add: preview update delay tweak, default of 500ms makes typing a breeze and preview updates
  half second later.
* Fix: export on smart mode exit broke exporting all together
* Fix: style sheets need url prefix when displaying HTML
* Add: Re-Export action that will ignore modification time and force re-exporting of all
  required files.
* Fix: added a short time delay to running export after settings change or project open.
* Add: option to not wrap on typing when soft wrap is enabled for the editor
* Fix: #340, 2.1.1.40 Fail to re-gen HTML files when HTML already exists
* Add: option for format document with soft wraps: disabled, enabled and infinite margins. Will
  remove all soft breaks when formatting the document.
* Fix: balloon on html project export
* Add: link text completion for GitHub issue titles. Completes same as in text. Fast way to link
  to issues and have the title in the link.
* Add: #314, Export .html files (as part of build?)
    * exported files are limited to being under the project base directory to prevent erroneous
      target directory from writing to the file system in unexpected location.
    * copy custom font file if stylesheet has reference to it
    * optionally use relative links to:
        * exported html files
        * stylesheets and scripts
        * custom font
        * image files
    * optionally copy image files
* Fix : Jira copy to add blank lines for loosely spaced lists and after the last list item of
  the outer-most list and the next element
* Add: scope based rendering profiles allowing fine grained control on markdown rendering
  options.
* Add: #319, Synchronize source caret to preview element on click.
* Add: #283, print html preview for now only for JavaFx
* Add: #174, Suggestion: URL-to-filename transformation rules for image previews
    * Options to map from markdown link text to GitHub based link reference. ie. `{{ static_root
      }}` --> `/`
    * Options to map from GitHub based link reference to markdown link text. ie. `/` --> `{{
      static_root }}`
    * With scope based rendering profiles this mapping can be customized for specific files
      and/or directories
* Add: #331, Add markdown context aware trailing space removal
* Add: #329, Now can delete all previously generated file through HTML export or just the files
  that were previously generated and will no longer be generated in the current configuration.
* Add: Update HTML Export on project settings change option.
* Fix: #330, unexpected HTML export files on save.
* Fix: exported HTML was missing custom CSS text from Stylesheet options.
* Add: HTML Export will export any HTML files that were exported with different settings
* Add: Export Markdown to HTML action will export all changed files and delete any invalid ones
  from previous exports.
* Add: HTML Export to display error on export of different sources to same target
* Add: progress indicator to HTML Export and make it backgroundable and cancellable.
* Add: Soft wrap at right margin option to application settings for markdown documents.
* Add: configurable file reference recognition in jekyll front matter element
* Fix: linked map settings adding empty group on settings load in migration code
* Add: #332, refactor file name reference in jekyll front matter when renaming file
* Fix: when Prism.js is used as highlighter, scrolling to source with caret in the code part of
  the fenced code would always scroll to top of document.
* Fix: #320, ArrayIndexOutOfBoundsException at BlockQuoteAddAction
* Fix: JavaFX preview synchronize to caret would mess up for heading and fenced code in list
  items.
* Fix: Edit TOC dialog did not add a space between `levels=...` and the next option
* Fix: Jira copy failed to include `:lang=` for fenced code and did not add an extra blank line
  after the fenced code
* Fix: flexmark-java options refactoring exception and make dialog reflect position and
  selection of element being renamed.

### 2.1.1 - Bug Fix & Enhancement Release

#### Basic & Enhanced Editions

- Fix: #299, Tables not syntax highlighted in basic version.
- Add: List syntax options: CommonMark, Fixed, GitHub.
- Add: #301, License activation not working for some network security configurations, Option to
  use non-secure connection for license activation.
- Fix: #302, IndexOutOfBoundsException: Index out of range: 190
- Fix: #307, NegativeArraySizeException when opening .md.erb file, IDE bug
- Change: update Kotlin to 1.0.4

#### Enhanced Edition

- Fix: #305, Document Format indents Footmarks converting them to code blocks
- Add: #306, Copy/Cut of reference links, images or footnote references to include the
  references and footnotes on paste.
- Add: #300, Breadcrumbs support for Markdown documents
- Fix: breadcrumbs to show heading hierarchy as parents, including headings nested within other
  elements like list items, block quotes, etc.
- Add: breadcrumb option to show element text and maximum number of characters of text to use
  (10-60, 30 default).
- Fix: breadcrumb setext heading to use atx equivalent text
- Fix: breadcrumbs to show paragraph text instead of `Text Block`
- Add: Copy as JIRA formatted text action. Copy selection or whole document to clipboard as JIRA
  formatted text.
- Fix: #308, Wiki vcs repo not recognized in 2016.3 due to API changes. Affects to http:...
  absolute link conversion from non wiki markdown files to wiki target files.
- Add: on paste reference link format resolution for new destination file
- Add: on paste link format resolution for new destination file

### 2.1.0 - Bug Fix Release

#### Basic & Enhanced Editions

- Change: update source for flexmark-java refactored file layout.
- Fix: #287, tables stopped rendering
- Fix: #286, PyCharm 2016.2.1, unterminated fenced code causing too many exceptions
- Fix: #285, Not able to parse .md.erbfile
- Fix: #287, tables stopped rendering part 2, tables not rendering at all
- Fix: #291, on open idea load multimarkdown failure some time!, tentative fix.
- Change: remove Lobo Evolution library and other unused dependencies.
- Fix: #293, Cannot adjust settings for "Explicit Link"

#### Enhanced Edition

* Fix: remove e-mail validation from fetch license dialog.
* Fix: typing at the start of text of a numbered list item with wrap on typing enabled would
  delete the character as soon as it was typed.
* Fix: wrap on typing would stop wrapping text when space was typed. Caused by the IDE no longer
  generating pre-char typed handler calls for some yet unknown reasons.
* Fix: remove wrap on typing disabling when typing back ticks or back slashes because it was
  only needed due to pegdown parser quirks.
* Fix: #288, IndexOutOfBoundsException
* Fix: #294, Structure view text not compatible with text search.
    1. Headings: searchable text is the heading text, greyed out text is the heading id with `#`
       prefixed showing the ref anchor for the heading
    2. Images: searchable text is the image link, greyed out text is the alt text
    3. List Items: searchable text is the first line of the item text
    4. Links: searchable text is the link url, greyed out text is the link text
    5. Footnotes: searchable text is footnote reference `:` first line of footnote text
    6. References: searchable text is the reference id `:` reference link url
* Fix: #296, License expiration not handled properly by plugin for versions released before
  license expired
* Fix: #297, Code Fence only minimizes leading spaces of the first code line during formatting
* Fix: #298, Formatting list items with empty text and first item a Atx heading, moves the
  heading before the list item

### 2.0.0 - New Parser Release

#### Basic & Enhanced Editions

- Fix: #282, Child paragraphs of tight list items are merged into the item text in preview
  instead of being a separate paragraph.
- Change: Component name for Markdown Navigator application shared settings changed to `Markdown
  Navigator` from a confusing `ApplicationShared`. Did't realize that the component name was
  used for display in import/export settings dialog.
- Fix: JavaFX and Swing stylesheets to better match GFM rendering.
- Add: Flexmark parser used for Swing preview rendering and plain HTML text previews.
- Add: allow task list items from ordered list items like GitHub, rendering is the same as
  bullet items.
- Fix: emoji renderer was not setting image height, width nor align attributes
- Fix: emoji parser flags were not being passed to HTML Renderer
- Add: Flexmark parser used for JavaFX Html preview rendering.
- Add: Debug setting to allow switching to pegdown for HTML rendering for debug and comparison
  purposes.
- Change: update flexmark-java parser to spec 0.26 with more intuitive emphasis parsing
- Add: skeleton error reporter to make reporting plugin errors more convenient and also more
  complete. No server code yet. For now disabled.
- Fix: With lexer as syntax highlighter deleting the last space after `[ ]` would cause an
  exception that was trapped but it would mess up syntax highlighting
- Fix: parser would accept ordered lists using `)` delimiter, as per CommonMark spec.
- Add: flexmark parser as the default option for lexer, parser and external annotator. Typing
  response is amazing. Some elements still missing:
    - Definitions
    - Typographic: Quotes, Smarts
    - Multi-Line Image URLs

#### Enhanced Edition

* Change: Move pegdown timeout from parser settings to debug settings. :grinning:
* Add: use actual char width to fix for wrap on typing fix when typing right before start of
  line elements.
* Add: GFM table rendering option to render tables text that GFM would render as text.
* Fix: wrap on typing right before an element set to always be at the beginning of line would
  always put the caret right before the element after wrapping, typing the next word and space
  would wrap the word to the previous line, leaving the caret at the start of line. Now the
  caret is kept at the end of the previous line making caret behaviour more natural.
* Fix: split editor layout change actions and preview content change actions now restore focus
  back to the text editor. Now they can be used in keyboard shortcuts without interrupting
  typing by needing a mouse click to restore focus.
* Add: source position information to list items.
* Fix: link text suggestion provider to remove any `..` directory references
* Fix: Refine JavaFX scroll preview to source position and highlighting to work more intuitively
  for block elements, images and address JavaFX WebView DOM element offset quirks.
* Add: JavaFX scroll preview to source position and various highlight options to show which
  element in the source has focus.
* Add: flexmark spec example rendering options: fenced code, sections, definition list
* Change: simulated TOC to allow `''` for titles to match what is allowed in references
* Add: list annotation and quick fixes when list items are inconsistent. i.e. bullet and
  numbered items mixed in one list.
* Add: table annotations and reformat quick fix
* Add: parser option for generated TOC to include a blank line spacer after the `[TOC]:#` marker
  to increase compatibility with existing markdown parsers.
