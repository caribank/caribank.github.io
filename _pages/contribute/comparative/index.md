---
title: "Comparative annotations"
permalink: /contribute/comparative
---

Currently, the main goal is identification of correspondence sets, annotation of cognate material and reconstruction of proto-forms.
For all three endeavours, a dedicated `Annotator` column contains one or more comma-separated (`,`) identifier(s) for [contributors](https://github.com/caribank/caribank/blob/main/etc/contributors.csv), to help keep track of who did what.
If you edit (rather than delete) somebody else's annotation, add your handle to the list, instead of overwriting theirs.

## Cognate sets
Cognate sets (= identified correspondences) are stored in [a separate spreadsheet](https://github.com/caribank/caribank/blob/main/reconstruction/cognatesets.csv).
A cognate set minimally has values for `ID`, `Concept`, and `Annotator`.
* The `ID` field does double duty as an identifier within the database, as well as a human-friendly handle. This means that instead of using an identifier for computers (like `3033`) and a name for humans (like `TREE-2`), a single shorthand (like `yeye-tree`) is used.
* The `Concept` field contains a gloss for the concept(s) the ancestral form likely expressed. If possible, this should be a [Concepticon](concepticon.clld.org/) gloss; in our tree example, this would be [TREE OR WOOD](https://concepticon.clld.org/parameters/2141).
* See the [bibliography](/contribute/bib) page for instructions for cognate sets sourced from the literature.

## Cognacy
The entities available for annotation are sourced from the database and loaded into annotation spreadsheets.
These spreadsheets contain a combination of 1) columns containing information about the entity and 2) annotation columns.
Changes to the annotation columns will be fed back into the database; *changes to other columns will not have any effect*.

Cognacy annotations are on the level of the **morph** from a **historical** perspective.
That is, the atomic unit of annotation are invariable and non-segmentable segment sequences reconstructible to a proto-language.
Units in the language-specific datasets are not necessarily at the level of the morph.
Specifically, morphologically complex stems may occur as the smallest unit of analysis, both in dictionary datasets, as well as glossed corpora.
Such cases requires a more elaborate annotation scheme, explained below.

Entities from the database receive an annotation minimally consisting of:
* `Cognateset_ID`, referencing the cognate set
* `Annotator`, referencing the [table of contributors](https://github.com/caribank/caribank/blob/main/etc/contributors.csv)

An example of a simple case is Werikyana *kahu* 'sky', which (to the best of our knowledge) is monomorphemic both synchronically and historically, being a descendant of Proto-Cariban \**kapu*.
The `Cognateset_ID` corresponding to this set of correspondences is `kapu-sky`; the `Annotator` value is the identifier of whoever's annotating.
Thus, the row in the annotation spreadsheet looks as follows (some columns omitted for readability):

| ID              | Language_ID | Form | Translation | Cognateset_ID | Segmentation | Hist_Comment | Annotator |
|-----------------|-------------|------|-------------|---------------|--------------|--------------|-----------|
| kax-sm-kahu-sky | kax         | kahu | sky         | kapu-sky      |              |              | fm        |

For (historically) morphologically complex database entities, `Segmentation` is used to store information about etymological morph breaks.
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

## Morphologically complex stems
There are datasets that contain roots and derivational morphs in their morph table, and information about morphologically complex stems in a separate stem table.
These stems (which are **not** the smallest unit of analysis in their respective dataset) cannot and need not be annotated for cognacy.
Instead, the cognacy annotations of their constituent morphs is used to automatically build "morphologically complex cognates" ([example]({{site.APP_URL_BASE}}complexcognatesets/ete-detrz-apeti-grab-1)).

## Proto-forms
Reconstructed forms can be entered in [a separate spreadsheet](https://github.com/caribank/caribank/blob/main/reconstruction/proto_forms.csv).
`Concept` only needs to contain a value if the form's meaning is not identical to the concept annotated for the corresponding cognate set (i.e., if semantic shift has taken place).
A reconstructed form may come from the literature; in that case, the source is made explicit in the `Source` field.
Proto-forms are transcribed using the following special characters:

| Grapheme | IPA |
|---|---|
| ⟨ë⟩ | ə |
| ⟨ï⟩ | ɨ |
| ⟨y⟩ | j |

Unspecified non-nasal consonants, vowels, and nasals can be indicated with the symbols ⟨C⟩, ⟨V⟩ and ⟨N⟩.

## Editing data
There are two ways to edit the spreadsheets:

* [Google sheets](gsheets) (basic, but very accessible)
* [Github](github) (more power + control, bit of a learning curve)
