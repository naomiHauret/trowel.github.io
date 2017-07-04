---
title: Set your global configuration
permalink: /documentation/trowel-core/use-a-component/config/
---

*Trowel* allows you to control the selector that will be generated into css, and through the variable `$trowel-config` you can set selector syntax options or the responsive breakpoints used.

## syntax
### Separators
*Trowel* is based on the BEM (Block - Element - Modifier) principle. Blocks and Elements are static and set by the developer that created the *Trowel component*.
You will set the Modfiers (and the Element-modifiers) through the *Trowel variables*.
But you can also set the syntax that will separate each element of the selector. By default, Trowel set the separator syntax as BEM preconise it :

```
// The default configuration for syntax separator
$trowel-config: (
  'syntax': (
    'separator': (
      'element': '__',
      'modifier': '--',
    ),
  )
);

// The config above will generate selectors on this model
.btn--primary { ... }
.btn__icon { ... }
```

But you can totally change it into a bootstrap-like syntax :

```
$trowel-config: (
  'syntax': (
    'separator': (
      'element': '-',
      'modifier': '-',
    ),
  )
);

// The config above will generate selectors on this model
.btn-primary { ... }
.btn-icon { ... }
```

### Prefixes
You can also set a prefix for every selector generated with trowel, as well as its own separator :

```scss
$trowel-config: (
  'syntax': (
    'prefix': 'c',
    'separator': (
      'prefix': '-',
      'element': '__',
      'modifier': '--',
    ),
  )
);

// The config above will generate selectors on this model
.c-btn--primary { ... }
.c-btn__icon { ... }
```

If the `prefix` key into the `$trowel-config` is set as `null`, no prefixes will be added to selectors :

```scss
$trowel-config: (
  'syntax': (
    'prefix': null,
    'separator': (
      'prefix': '-',
      'element': '__',
      'modifier': '--',
    ),
  )
);

// The config above will generate selectors on this model
.btn--primary { ... }
.btn__icon { ... }
```

## Responsive breakpoints
As we will see later, we can set a specific value to a property depending of the size of the viewport into a *Trowel variable*. But first, through the `$trowel-config` variable, we need  to set responsive breakpoints that will be targeted into the *Trowel variables*.

```scss
// this is how we set the responsive breakpoints into the config variable
$trowel-config: (
  'breakpoints': (
    'xs': (
      'max': 10rem,
    ),
    'sm': (
      'min': 10rem,
      'max': 20rem,
    ),
    'md': (
      'min': 20rem,
    )
  ),
);
```

## Set the `$trowel-config`
Set the configuration to Trowel by setting the variable `$trowel-config` before the `@import` of `trowel-core`. Each key that is not defined will be set by the default value listed below :

```scss
// Trowel config with all the default values
$trowel-config: (
  'breakpoints': (
    'xs': (
      'max': 10rem,
    ),
    'sm': (
      'min': 10rem,
      'max': 20rem,
    ),
    'md': (
      'min': 20rem,
    )
  ),
  'syntax': (
    'prefix': null,
    'separator': (
      'prefix': '-',
      'element': '__',
      'modifier': '--',
    ),
  )
);
```

{% include page-control.html href="/documentation/trowel-core/use-a-component/customize/" label="Customize a trowel component" %}
