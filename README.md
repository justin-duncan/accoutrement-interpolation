# Sass Accoutrement

**Robust design systems** require
_meaningful_, _readable_, _reusable_ code.
These Sass utilities are designed to
help define and manage your design tokens
(colors, fonts, sizes, etc.)
in a format that can be understood
by both humans and parsers --
opening the door for automation,
while improving consistency and readability.
These tools also integrate with [Herman][herman],
our automated living pattern-library generator
built on [SassDoc][sassdoc].

[herman]: https://www.oddbird.net/herman/
[sassdoc]: http://sassdoc.com/

- [Official Site](https://www.oddbird.net/accoutrement/)
- [Documentation](https://www.oddbird.net/accoutrement/docs/)
- [Source Code](https://github.com/oddbird/accoutrement/)
- [Issues](https://github.com/oddbird/accoutrement/issues)

_Brought to you by [OddBird][oddbird] --
the creators of [Susy][susy],
[True][true],
and [Herman][herman]._

[oddbird]: https://www.oddbird.net/
[susy]: https://www.oddbird.net/susy/
[true]: https://www.oddbird.net/true
[herman]: https://www.oddbird.net/herman
[fonts]: https://www.oddbird.net/accoutrement/docs/type.html

## Installation

Install the package with npm or yarn

```bash
npm install accoutrement [--save-dev]
yarn add accoutrement [--dev]
```

Import what you need:

```scss
// core and all plugins (also available with `/index`)
@import "<path-to>/accoutrement/sass/tools";

// init normalization
@import "<path-to>/accoutrement/sass/init";

// individual plugins (core is required)
@import "<path-to>/accoutrement/sass/core";
@import "<path-to>/accoutrement/sass/plugin/<name>";
```

If you're using [Eyeglass](https://github.com/linkedin/eyeglass),
you can import the default "tools" (core + plugins) using only:

```scss
@import "accoutrement";
```

## Usage

The accoutrement tools are built around
a shared data-storage syntax
using Sass "map" objects:

```scss
$map: (
  "root": 16px,
  "gutter": 1em,
);
```

Using a custom syntax,
we can extend maps to handle internal reference,
and functional adjustments --
capturing meaningful relationships
between design tokens:

```scss
$map: (
  "root": 16px,
  // internal reference & adjustments
  "gutter": "#root"
    (
      "_major-third": 1,
      "convert-units": "rem",
    ),
);
```

Map storage serves a larger purpose:

- Related data is grouped explicitly,
  making the code more readable and maintainable
- The "single source of truth"
  encourages reusable design patterns
- Meaningful structure allows automation,
  from [automated style guides][herman]
  to automated functionality
  (provided in the plugins)

[herman]: https://www.oddbird.net/herman/
[type]: https://www.oddbird.net/accoutrement/docs/type.html

## [Core](https://www.oddbird.net/accoutrement/docs/core.html)

The **Core** module provides the generic
(non data-specific)
setup and syntax parsing:

- Retrieve & parse map values
  with the generic [`get-token()`][get] function
- Use our built-in [math][math], [modular-scale][ratio],
  [list][list], and [string][string] utilities
- Register your own first class [functions][functions],
  for reference inside data maps

[get]: https://www.oddbird.net/accoutrement/docs/core-get.html
[math]: https://www.oddbird.net/accoutrement/docs/core-math.html
[ratio]: https://www.oddbird.net/accoutrement/docs/core-ratio.html
[list]: https://www.oddbird.net/accoutrement/docs/core-lists.html
[string]: https://www.oddbird.net/accoutrement/docs/core-strings.html
[functions]: https://www.oddbird.net/accoutrement/docs/core-register.html

## [Init](https://www.oddbird.net/accoutrement/docs/init.html)

We provide light-weight browser-normalization,
as a distinct include.
This is not part of the `accoutrement/sass/tools` package
because it is the only module to produce
direct CSS output.

## Plugins…

While the core module handles generic data-management,
we also provide plugins for a few common data types:

- **[Animate](https://www.oddbird.net/accoutrement/docs/animate.html)** --
  Tools for managing CSS transitions and animations
- **[Color](https://www.oddbird.net/accoutrement/docs/color.html)** --
  Tools for managing CSS colors and contrast-ratios
- **[Scale](https://www.oddbird.net/accoutrement/docs/scale.html)** --
  Tools for managing CSS sizes: typographic scales, spacing, etc.
- **[Type](https://www.oddbird.net/accoutrement/docs/type.html)** --
  Tools for managing webfonts, generated content, and other text needs
