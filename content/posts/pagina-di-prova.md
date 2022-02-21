+++
title = "Pagina di prova"
description = "In modalità org l'introduzione al post è inserita all'interno del blocco `description` ed esportata nel front matter del file markdown processato da Hugo."
date = 2022-02-20T20:37:00+01:00
tags = ["test", "katex", "inkscape", "code"]
draft = false
+++

## Formule {#formule}

In tutte le pagine [\\(\KaTeX\\)](https://katex.org) si occupa del rendering delle formule matematiche, sia _inline_ come ad esempio l'identità di Eulero \\(e^{i\pi} = -1\\), sia a centro pagina come nella definizione della funzione zeta di Riemann

\\[\zeta(s) = \sum\_{i = 1}^{\infty} \frac{1}{n^s}\\]


## Immagini SVG {#immagini-svg}

Quasi tutte le immagini sono create con [Inkscape](https://inkscape.org/it/) e salvate nel formato svg nativo: per inserire le formule in \\(\LaTeX\\) c'è l'ottima estensione TexText.[^fn:1]

{{< figure src="/images/gauss.svg" >}}

Il preambolo a cui TexText fa riferimento è semplicemente

```tex
\documentclass[12pt]{article}
\usepackage{amsmath,amsthm,amssymb,amsfonts}
\usepackage{color}
```

L'opzione della classe `article` emula i 16 pixel del testo nella pagina. Inoltre in TexText è impostato un fattore di scala di `1.21em`, per cui l'effetto dovrebbe essere quello di avere formule della stessa dimensione in html che in svg.[^fn:2]

La prima è un'immagine svg, mentre la seconda è generata con KaTeX.

{{< figure src="/images/zeta.svg" >}}

\\[\zeta(s) = \prod\_p \frac{1}{1 - p^{-s}}\\]


## Spell checker {#spell-checker}

Doom Emacs non offre una configurazione dedicata per Ispell in modalità org. Almeno per saltare il controllo dei blocchi con formule si può usare il codice seguente nella propria configurazione:

```elisp
(add-hook 'org-mode-hook
          (lambda ()
            (make-local-variable 'ispell-skip-region-alist)
            (add-to-list 'ispell-skip-region-alist '("\\[" . "\\\\]"))
            (add-to-list 'ispell-skip-region-alist '("\\$" . "\\$"))
            ))
```

[^fn:1]: Reperibile al link <https://textext.github.io/textext/>
[^fn:2]: Il fattore di scala `1.21em` è il default di KaTeX ([docs](https://katex.org/docs/font.html#font-size-and-lengths))
