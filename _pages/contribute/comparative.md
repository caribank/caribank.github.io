---
title: "Contribute comparative annotations"
permalink: /contribute/comparative
layout: single
---

Currently, the main goal is annotation of cognate material and reconstruction of proto-forms.

## Cognate sets
There is a [table of cognate sets](https://github.com/caribank/caribank/blob/main/reconstruction/cognatesets.csv)

## Cognacy
The entities available for annotation are sourced from the database and loaded into annotation spreadsheets.
These spreadsheets contain a combination of columns containing information about the entity and annotation columns.
Changes to the annotation columns will be fed back into the database; *changes to other columns will not have any effect*.

Cognacy annotations are on the **historical** morph level, i.e., invariable and non-segmentable segment sequences reconstructible to some proto-language, ideally Proto-Cariban.
Entities from the database receive an annotation minimally consisting of:
* `Cognateset_ID`, referencing the cognate set
* `Annotator`, referencing the [table of contributors](https://github.com/caribank/caribank/blob/main/etc/contributors.csv)

An example of such a simple case is Werikyana *kahu* 'sky', which (to the best of our knowledge) is monomorphemic both synchronically and historically, being a descendant of Proto-Cariban \**kapu*.
The `Cognateset_ID` corresponding to this set of correspondences is `kapu-sky`; the `Annotator` value is the identifier of whoever's annotating.
Thus, the row in the annotation table looks as follows (some columns omitted for readability):

| ID              | Language_ID | Form | Translation | Cognateset_ID | Segmentation | Hist_Comment | Annotator |
|-----------------|-------------|------|-------------|---------------|--------------|--------------|-----------|
| kax-sm-kahu-sky | kax         | kahu | sky         | kapu-sky      |              |              | fm        |

For less straightforward cases, `Segmentation` is used to store information about etymological morph breaks.
`Hist_Comment` is always optional, but is useful for keeping track of ideas and problems.
For instance, Macushi *tîrî* 'put, give' is synchronically monomorphemic, but the *t* used to be a (lexically conditioned) third person prefix that has now become part of an invariable root.
This means that an etymological morph break needs to be inserted, which is done by

1. separating the relevant cognate sets with `+`
2. copying the `Form` to the `Segmentation` column
3. inserting a `+` at the appropriate position

This results in the following annotation:

| ID              | Language_ID | Form | Translation | Cognateset_ID | Segmentation | Hist_Comment | Annotator |
|-----------------|-------------|------|-------------|---------------|--------------|--------------|-----------|
| mac-sm-tiri-put | mac         | tɨrɨ | put; give         | t-add+iri-put      |   t+ɨrɨ         |  Lexicalized \*t-\*            | fm        |

Material not assignable to a cognate set can be left empty or made explicit with `?`.
For instance, if the source of the *t* above was unkown, the `Cognateset_ID` annotation could be `+iri-put` or `?+iri-put`; the `Segmentation` remains the same.
It is crucial to use `+`-delimited `Segmentation` values for these cases, otherwise sound correspondences will be incorrect.



There are two ways to edit the annotation spreadsheets:

* [Google sheets](/contribute/gsheets) (basic, but very accessible)
* [Github](/contribute/github) (more power + control, bit of a learning curve)
