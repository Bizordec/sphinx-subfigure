# sphinx-subfigure (IN-DEVELOPMENT)

A [sphinx](https://www.sphinx-doc.org) extension to create figures with multiple images:

- Provides a simple format for complex image layouts.
- Supports HTML fully, with responsive layouts, for different screen sizes
  - LaTeX is supported, except for images that span multiple rows.
  - degrades gracefully for other formats.
- Supports figure numbering and referencing.
- Supports image sub-captions, via `alt` text.

## Usage

Install `sphinx-subfigure` with `pip install sphinx-subfigure`,
then add `sphinx_subfigure` to your `conf.py` file's `extensions` variable:

```python
extensions = ["sphinx_subfigure"]

numfig = True  # optional
```

Now add a `subfigure` directive to your document:

```restructuredtext
.. subfigure:: AA|BC
   :layout-sm: A|B|C
   :subcaptions: above
   :name: myfigure
   :class-grid: outline

   .. image:: imageA.png
      :alt: Image A

   .. image:: imageB.png
      :alt: Image B

   .. image:: imageC.png
      :alt: Image C

    Figure Caption
```

1. Each image is automatically assigned an *area identifier* (A, B, C, etc.).
2. Layouts are formed by composing the areas into a grid, with rows delimited by `|`.
3. Each area must be used exactly once in the layout, and form a single rectangle.
4. "Empty" areas can be designated with `.`
5. Additional layouts can be defined with `:layout-sm:`, `:layout-lg:`, `:layout-xl:`, and `:layout-xxl:`, for different screen sizes (HTML only).

:::{subfigure} AA|BC
:layout-sm: A|B|C
:subcaptions: above
:name: myfigure
:class-grid: outline

```{image} _static/A.png
:height: 100px
:alt: Image A
```

```{image} _static/B.png
:height: 100px
:alt: Image B
```

```{image} _static/C.png
:height: 100px
:alt: Image C
```

Figure Caption

:::

The figure can now be referenced in the document:

```restructuredtext
:ref:`myfigure`, :numref:`myfigure`
```

{ref}`myfigure`, {numref}`myfigure`

## More Examples

:::{subfigure} AA|BC
:subcaptions: above
:class-grid: outline

```{image} _static/A.png
:height: 100px
:alt: Image A
```

```{image} _static/B.png
:height: 100px
:alt: Image B
```

```{image} _static/C.png
:height: 100px
:alt: Image C
```

Image spanning multiple columns: `AA|BC`

:::

---

:::{subfigure} AB|AC
:subcaptions: above
:class-grid: outline

```{image} _static/A.png
:height: 100px
:alt: Image A
```

```{image} _static/B.png
:height: 100px
:alt: Image B
```

```{image} _static/C.png
:height: 100px
:alt: Image C
```

Image spanning multiple rows: `AB|AC`

:::

---

:::{subfigure} A.B|CDE
:subcaptions: above
:class-grid: outline

```{image} _static/A.png
:height: 100px
:alt: Figure A
```

```{image} _static/B.png
:height: 100px
:alt: Figure B
```

```{image} _static/C.png
:height: 100px
:alt: Figure C
```

```{image} _static/D.png
:height: 100px
:alt: Figure D
```

```{image} _static/E.png
:height: 100px
:alt: Figure E
```

Sub-figure with empty area: `A.B|CDE`

:::

---

:::{subfigure} 3
:subcaptions: below
:class-grid: outline

```{image} _static/A.png
:height: 100px
:alt: Figure A
```

```{image} _static/B.png
:height: 100px
:alt: Figure B
```

```{image} _static/C.png
:height: 100px
:alt: Figure C
```

Sub-figure with captions below

:::

---

:::{subfigure} 3
:class-grid: outline

```{image} _static/A.png
:height: 100px
:alt: Figure A
```

```{image} _static/B.png
:height: 100px
:alt: Figure B
```

```{image} _static/C.png
:height: 100px
:alt: Figure C
```

Sub-figure with no captions

:::

---

:::{subfigure} 2
:layout-sm: 1
:layout-lg: 3
:layout-xl: 4
:layout-xxl: 5
:subcaptions: above
:class-grid: outline

```{image} _static/A.png
:height: 100px
:alt: Figure A
```

```{image} _static/B.png
:height: 100px
:alt: Figure B
```

```{image} _static/C.png
:height: 100px
:alt: Figure C
```

```{image} _static/D.png
:height: 100px
:alt: Figure D
```

```{image} _static/E.png
:height: 100px
:alt: Figure E
```

Sub-figure with adaptive layouts

:::