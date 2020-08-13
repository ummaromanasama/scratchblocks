# 3D_Print_Coding_Blocks


Overview: Tangible coding blocks curates a more hands-on learning experience, encourage peer programming through unplugged computer science activities to understand the fundamental concepts of computer science. Students will develop their critical, analytical, and problem-solving skills through the use of physical coding blocks.

To reproduce your own coding blocks for the classroom you will need:
- 3D printer
- Filament
- [TinkerCAD account](https://www.tinkercad.com/)
- [scratchblocks](http://scratchblocks.github.io/)

How to 3D print your own coding blocks:
1. With the [scratchblocks](http://scratchblocks.github.io/) generator, type in your desired coding block and then download the SVG file. The SVG will provide the shape of the coding block.
2. Log into [TinkerCAD account](https://www.tinkercad.com/), start a new project, and upload the SVG file to the building plate.
3. If there are missing components to your coding block create the indentations by duplicating and erasing components as needed.
4. Add the corresponding text that you used in the [scratchblocks](http://scratchblocks.github.io/) generator to your blocks.
5. Space out and size all the components of your coding blocks accordingly and you are done designing your coding block.
6. Export the coding block as an STL file, throw it into your slicer of choice, and 3D print your coding block!
7. To differentiate the text and block color; you pause the print, unload the filament, load the new filament, and resume your print.
---

Make pictures of Scratch blocks from text.

[![Screenshot](http://scratchblocks.github.io/screenshot.png)](https://scratchblocks.github.io/#when%20flag%20clicked%0Aclear%0Aforever%0Apen%20down%0Aif%20%3C%3Cmouse%20down%3F%3E%20and%20%3Ctouching%20%5Bmouse-pointer%20v%5D%3F%3E%3E%20then%0Aswitch%20costume%20to%20%5Bbutton%20v%5D%0Aelse%0Aadd%20(x%20position)%20to%20%5Blist%20v%5D%0Aend%0Amove%20(foo)%20steps%0Aturn%20ccw%20(9)%20degrees)

**[Try it out!](http://scratchblocks.github.io/)**

---

**scratchblocks** is used to write Scratch scripts:

- in [Scratch Forum](http://scratch.mit.edu/discuss/topic/14772/) posts
- in [Scratch Wiki](http://wiki.scratch.mit.edu/wiki/Block_Plugin) articles
- in the [Code Club](https://www.codeclub.org.uk) project guides

It's MIT licensed, so you can use it in your projects. (But do send me a link [on Twitter](http://twitter.com/blob8108)!)

For the full guide to the syntax, see [the wiki](http://wiki.scratch.mit.edu/wiki/Block_Plugin/Syntax).

# Usage

## MediaWiki

Use [the MediaWiki plugin](https://github.com/tjvr/wiki-scratchblocks). (This is what the [Scratch Wiki](http://wiki.scratch.mit.edu/wiki/Block_Plugin) uses.)

## WordPress

I found [a WordPress plugin](https://github.com/tkc49/scratchblocks-for-wp). It might work for you; I haven't tried it.

## Pandoc

Code Club use their own [lesson_format](https://github.com/CodeClub/lesson_format) tool to generate the PDF versions of their project guides. It uses the [pandoc_scratchblocks](https://github.com/CodeClub/pandoc_scratchblocks) plugin they wrote to make pictures of Scratch scripts.

This would probably be a good way to write a Scratch book.

## HTML

Include a copy of [the scratchblocks JS file](https://scratchblocks.github.io/js/scratchblocks-v3.4-min.js) on your webpage.

```html
<script src="scratchblocks-v3.4-min.js"></script>
```

You can also include [the translations JS file](https://scratchblocks.github.io/js/translations-all-v3.4.js) if you want to include non-English blocks, but since that's quite large (nearly 600K?) it's recommended you build your own file with just the locales you need. For example, a translation file that just loads the German language (ISO code `de`) would look something like this:

```js
window.scratchblocks.loadLanguages({
    de: <contents of locales/de.json>
})
```

You then need to call `scratchblocks.renderMatching` after the page has loaded. It takes a CSS-style selector for the elements that contain scratchblocks code. The `style` option controls how the blocks appear, either the Scratch 2 or Scratch 3 style is supported.

```js
scratchblocks.renderMatching('pre.blocks', {
  style:     'scratch3',   // Optional, defaults to 'scratch2'.
  languages: ['en', 'de'], // Optional, defaults to ['en'].
});
```

### Inline blocks

To use blocks inside a paragraph...

```html
I'm rather fond of the <code class="b">stamp</code> block in Scratch.
```

...make a separate call to `renderMatching` using the `inline` argument.

```js
scratchblocks.renderMatching("code.b", {
  inline: true,
  // Repeat `style` and `languages` options here.
});
```

## Browserify

You can even use `scratchblocks` with browserify, if you're into that sort of
thing.

Once you've got browserify set up to build a client-side bundle from your app
code, you can just add `scratchblocks` to your dependencies, and everything
should Just Work™.

```js
var scratchblocks = require('scratchblocks');
scratchblocks.renderMatching('pre.blocks');
```

# Languages

To update the translations:
```sh
npm upgrade scratch-l10n
npm run locales
```

## Adding a language

Each language **requires** some [additional words](https://github.com/tjvr/scratchblocks/blob/master/locales-src/extra_aliases.js) which aren't in Scratch itself (mainly the words used for the flag and arrow images). I'd be happy to accept pull requests for those! You'll need to rebuild the translations with `npm run locales` after editing the aliases.

# Development

This should set you up and start a http-server for development:

```
npm install
npm start
```

Then open <http://localhost:8000/> :-)

For more details, see [`CONTRIBUTING.md`](https://github.com/tjvr/scratchblocks/blob/master/.github/CONTRIBUTING.md).


# Credits

Many, many thanks to the [contributors](https://github.com/tjvr/scratchblocks/graphs/contributors)!

* Authored by [tjvr](https://github.com/tjvr)
* Icons derived from [Scratch Blocks](https://github.com/LLK/scratch-blocks) (Apache License 2.0)
* Scratch 2 SVG proof-of-concept, shapes & filters by [as-com](https://github.com/as-com)
* Anna helped with a formula, and pointed out that I can't read graphs
* JSO designed the syntax and wrote the original [Block Plugin](http://wiki.scratch.mit.edu/wiki/Block_Plugin_\(1.4\))
* Help with translation code from [joooni](http://scratch.mit.edu/users/joooni/)
* Block translations from the [Scratch translation server](http://translate.scratch.mit.edu/)
* Ported to node by [arve0](https://github.com/arve0)
