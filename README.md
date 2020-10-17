## LaTeX-α<sup>2</sup>

[![CTAN](https://img.shields.io/ctan/v/latexalpha2.svg)](https://ctan.org/pkg/latexalpha2)
[![Travis](https://img.shields.io/travis/stevenliuyi/latex-alpha2.svg)](https://travis-ci.org/stevenliuyi/latex-alpha2)

LaTeX-α<sup>2</sup> (`latexalpha2`) is a LaTeX package that can execute Wolfram Language codes and show the corresponding results inside LaTeX documents.

The package is heavily inspired by [LaTeX-Alpha](https://github.com/Akollek/LaTeX-Alpha). Unfortunately, LaTeX-Alpha has been down for a while. The aim of this package is to replace LaTeX-Alpha, as well as to provide various new features.

The codes can be executed either locally (via locally installed Mathematica) or on the cloud (via [Wolfram Cloud](https://www.wolframcloud.com/)) using the [WolframScript](https://www.wolfram.com/wolframscript/) interpreter. In addition, you can also use [Mathics](http://mathics.github.io) (a free, open-source alternative to Mathematica) for computations.

The package only supports Unix-like system for now. Pull requests are welcome.

### Usage

- First install [WolframScript](https://www.wolfram.com/wolframscript/) (or [Mathics](http://mathics.github.io)) if you haven't already done so. You can use `type wolframscript` or `type mathics` to check if it's properly installed.

- Download `latexalpha2.sty` to the same folder as your `.tex` file:

```
curl -O https://raw.githubusercontent.com/stevenliuyi/latex-alpha2/master/latexalpha2.sty
```

To avoid copying the file every time, please see the [installation guide](#installation) below.

- Add `\usepackage{latexalpha2}` to the preamble of your document. All the codes will be run locally by default. If you'd like to run on the cloud, use `\usepackage[cloud]{latexalpha2}` instead. For the Mathics mode, use `\usepackage[mathics]{latexalpha2}`.

- LaTeX must be invoked with the `-shell-escape` flag in order to run WolframScript (or Mathics). For example: ```pdflatex -shell-escape example.tex```.

Please refer to the [documentation](https://raw.githubusercontent.com/stevenliuyi/latex-alpha2/master/latexalpha2.pdf) for more information.

### Examples
#### `\wolfram{}`

Input:
```tex
$\wolfram{Series[Exp[x],{x,0,5}]}$
```

Output:

![](http://latex.codecogs.com/gif.latex?1+x+\frac{x^2}{2}+\frac{x^3}{6}+\frac{x^4}{24}+\frac{x^5}{120}+O(x^6))

#### `\wolframgraphics{}`

Input:

```tex
\begin{figure} 
    \wolframgraphics[pdf]{Plot3D[Sin[x]Cos[y], {x, -2Pi, 2Pi}, {y, -2Pi, 2Pi}]}{example}
    \includegraphics{example.pdf}
    \caption{Plot of $f(x,y)=\sin(x)\cos(y)$}
    \centering
\end{figure}
```

Output:

![Example Plot](images/example.png?raw=true)

Input:

```tex
\begin{figure} 
    \wolframgraphics[pdf]{GeoGraphics[{Red,Thick,GeoPath["DateLine"]},GeoRange->{All, {90, 270}},GeoGridLines->Quantity[15, "AngularDegrees"]]}{example2}
    \includegraphics{example2.pdf}
    \caption{International Date Line}
    \centering
\end{figure}
```

Output:

![Example Plot 2](images/example2.png?raw=true)

#### `\wolframalpha{}`

Input:
```tex
The population of Shanghai is $\wolframalpha{population of Shanghai}$, which is $\wolframalpha{ratio of Shanghai populatioin and NYC population}$ times the population of New York City.
```

Output:

The population of Shanghai is 2.415×10<sup>7</sup> people, which is 2.814 times the population of New York City.

Input:
```tex
$\wolframalpha{Compton scattering for electron}$
```

Output:

![](http://latex.codecogs.com/gif.latex?\Delta\lambda=(1-\cos(\theta))\left(0.0019569512\text{h}\\,\text{c}/\text{keV}\right))

#### `\wolframdsolve{}`

Input:
```tex
\wolframdsolve{y'[x]+y[x]==a*Sin[x]}{y[x]}{x}
```

Output:

![](http://latex.codecogs.com/gif.latex?y(x)=\frac{1}{2}a(\sin(x)-\cos(x))+c_1e^{-x})


#### `\wolframtable{}`

Input:
```tex
\begin{tabular}{ccc}
    \hline
    \wolframtable{Join[{{x,x^2,x^3}}, Table[{i,i^2,i^3},{i,5}]]}
    \hline
\end{tabular}
```

Output:

![Example Plot 3](images/example3.png?raw=true)


### Installation

To avoid copying the `latexalpha2.sty` file for every new project, you could install the package instead. Just put the `.sty` file in the `texmf/tex/latex` folder (for TeX Live, it would be `/usr/local/texlive/texmf-local/tex/latex` by default), and then run `sudo texhash` to update the package database. For more information, please refer to [LaTeX/Installing Extra Packages](https://en.wikibooks.org/wiki/LaTeX/Installing_Extra_Packages).

### License

This work is distributed under the LaTeX Project Public License (LLPL), version 1.3c.
