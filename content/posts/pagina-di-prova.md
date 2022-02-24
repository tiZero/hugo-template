+++
title = "Pagina di prova"
description = "In modalità org l'introduzione al post è inserita all'interno del blocco `description` ed esportata nel front matter del file markdown processato da Hugo."
date = 2022-02-20T20:38:00+01:00
tags = ["test", "katex", "inkscape"]
draft = false
+++

## Formule {#formule}

In tutte le pagine [\\(\KaTeX\\)](https://katex.org) si occupa del rendering delle formule matematiche, sia _inline_ come ad esempio l'identità di Eulero \\(e^{i\pi} = -1\\), sia a centro pagina come nella definizione della funzione zeta di Riemann
\\[
\zeta(s) = \sum\_{i = 1}^{\infty} \frac{1}{n^s}
\\]


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
            (add-to-list 'ispell-skip-region-alist '("\\\\\\[" . "\\\\]"))
            (add-to-list 'ispell-skip-region-alist '("\\$" . "\\$"))
            ))
```


## Tabelle {#tabelle}

Org permette molto agevolmente di costruire tabelle in testo semplice: lo stile delle tabella seguente è adattato dal [blog di Gregory Gundersen](https://github.com/gwgundersen/blog-theme/blob/master/css/blog.css). Il numero di soluzioni reali dell'equazione \\(ax^2 + bx + c = 0\\) dipende dal segno del **discriminante** \\[\Delta = b^2 - 4ac\\] definito a partire dai coefficienti \\(a\\), \\(b\\) e \\(c\\) come riepilogato nella tabella seguente:

| Segno di \\(\Delta\\) | Soluzioni reali | Soluzioni puramente immaginarie |
|-----------------------|-----------------|---------------------------------|
| \\(\Delta > 0\\)      | Due             | Nessuna                         |
| \\(\Delta = 0\\)      | Una soltanto    | Nessuna                         |
| \\(\Delta < 0\\)      | Nessuna         | Due (opposte)                   |

Nel caso in cui \\(\Delta \geq 0\\) vale la formula risolutiva per le equazioni di secondo grado
\\[
x = \frac{-b \pm \sqrt{\Delta}}{2a}
\\]
Come per le figure, è possibile aggiungere una didascalia alle tabelle utilizzando il tag `#+caption` in org-mode.


## Liste <span class="tag"><span class="list">list</span></span> {#liste}

In Org-mode è possibile attribuire un tag (o anche più di uno) a ciascuna sezione del post. Tuttavia, questi non sono cliccabili. Ad esempio, al titolo di questo paragrafo è stato aggiunto il tag `list`.

I corpi considerati in fisica possono essere di diversa natura.

-   Corpi _puntiformi_: dotati di massa ma aventi volume zero (considerati cioè come un punto che non occupa una regione estesa di spazio)
-   Corpi _estesi_: aventi sia massa che volume positivi

Finora abbiamo trattato

<div class="task-list">

-   [X] Corpi puntiformi
-   [ ] Corpi estesi

</div>

La sintassi di Org per creare le cosiddette _TODO list_ è la stessa di Markdown. Attenzione al fatto che la classe `task-list` non è automaticamente esportata[^fn:3] in Black Friday, ed è pertanto necessario indicarla esplicitamente all'inizio della lista, ad esempio con

```org
#+ attr_html: :class task-list
- [X] Corpi puntiformi
- [ ] Corpi estesi
```

In questo modo è possibile ad esempio rimuovere i pallini prima di ciascun elemento impostando lo stile nel file css.

[^fn:1]: Reperibile al link <https://textext.github.io/textext/>
[^fn:2]: Il fattore di scala `1.21em` è il default di KaTeX ([docs](https://katex.org/docs/font.html#font-size-and-lengths))
[^fn:3]: Vedi [hugo issue 6837](https://github.com/gohugoio/hugo/issues/6837)
