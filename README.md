# Tailwind Benchmark No. 2

## What this is about

This benchmark evaluates the marketing claim that Tailwind produces smaller builds.

I already did [another benchmark](https://github.com/ScriptRaccoon/tailwind-benchmark) before which deals with a basic landing page. This time, it is just an HTML page with the same card, copied 100 times. This does not happen in practice, but when the same card is used over multiple pages, 100 times in total, the results will be similar.

The CSS version is found in the subfolder `CSS`. The Tailwind version is found in the subfolder `Tailwind`. For better comparison, the (quite big) Tailwind CSS reset was replaced with the same, more simple one, used in the CSS version.

## Results

In both cases, the CSS was minified. Here are the results:

### Vanilla CSS (Winner)

-   `index.html`: 19.969 bytes
-   `style.css`: 249 bytes
-   total: 20.218 Bytes

### Tailwind

-   `index.html`: 24.109 bytes
-   `style.css`: 494 bytes
-   total: 24.603 bytes

## Conclusion

Tailwind's total bundle size **21%** larger than the Vanilla CSS version.

In response to my previous benchmark, on Twitter, it was claimed that Tailwind's bundle size wins with larger projects since we reuse the same utility classes over and over again. At first, this seems to be plausible. However, this disregards the HTML file, which grows a lot when the same utilities are repeated over and over again.

This can be seen very clearly in this repository. In Tailwind's HTML file, the class string for the card

`bg-white max-w-xs mx-auto p-4 my-4 rounded-lg`

is repeated 100 times, which is of course more data than

`card`

100 times. This explains why the HTML is larger.

The CSS file is also larger. This is partly because of the internal opacity variables which are not necessary here. But even when they are removed manually, the CSS file is 416 bytes, so **67%** larger than the Vanilla CSS file.

Of course, these little bytes do not make any difference. But when an application grows and the relation stays the same (this needs to be tested\*), the difference could be quite remarkable. See [this benchmark](https://github.com/TGlide/tailwind-benchmark) by Thomas G. Lopes with more data, where Tailwind's bundle size is indeed smaller.

## Next benchmark

https://github.com/ScriptRaccoon/tailwind-benchmark-3

\*See [this benchmark](https://github.com/TGlide/tailwind-benchmark) by Thomas G. Lopes with more data, where Tailwind's bundle size is indeed smaller.
