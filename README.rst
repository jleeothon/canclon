# canclón

Template name resolution for Django class-based views.

## Introduction

*canclón* is a local name for the horned screamer, [*Anhima cornuta*](https://en.wikipedia.org/wiki/Horned_screamer). This is a group of [class-based views](https://docs.djangoproject.com/en/dev/topics/class-based-views/) for [Django](http://djangoproject.com/). The simple flexibility and [DRYness](http://en.wikipedia.org/wiki/Don't_repeat_yourself) of this group of classes is comparable to that of horned screamer's [horn](https://www.youtube.com/watch?v=1esf6WNdvso).

Django's default method for template name resolution has a couple of not-so-niceties for more advanced developers, such as default template suffixes appended with an underscore (yay for dashes) and an assumption of HTML files (you might want to include other extension, such as `.jade`). This project gives you the flexibility of having everybody need to stick to a set of standards, or as well phase slowly into a standard by permitting more template names to be selected.

This project is released under an MIT License.

Warning:

> Including this functionality in your project makes template name resolution "DRYier" and more flexible but a bit slower.

## Getting started

Copy and paste whatever you want.

## Options

`template_flags` are variable names that are set to `True` for your template. **More insight into the usefulness of this, later**.

`template_suffixes` are usually actions associated with the model for which the template will serve, e.g. `list`, `edit`, `confirm-delete`.

`template_suffix_joints` is the separators between a model and a suffix. The default is a singleton (a 1-tuple) with a dash (`tuple('-')`).

`template_extensions` is the list of file extensions to look for, the default is a singleton of `'html'`. You can include other formats such as `.jade`.

Based on suffixes, suffix joints and extensions, a list of all posible combinations is returned. They take the form: `1/234.5`, where:
- 1 is the app label
- 2 is the model name
- 3 is separator (joint)
- 4 is the suffix
- 5 is the file extension

When a suffix is a null string, the separator and suffix are omitted.

## Proposals

If Django could receive a lazy object for `get_template_names` instead of a pre-evaluated iterable, this implementation would be both more time-efficient and space-efficient.
