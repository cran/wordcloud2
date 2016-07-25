---
title: "Wordcloud2 introduction"
date: "`r Sys.Date()`"
output: 
  html_document:
    highlight: kate
    toc: true
    toc_depth: 4
    mathjax: null
---

This is an introduction to `wordcloud2`  [package](http://github.com/lchiffon/wordcloud2). This package provides an HTML5 interface to wordcloud for data visualization. [Timdream's wordcloud2.js](https://github.com/timdream/wordcloud2.js) is used in this package.
![png](http://7xr5em.com1.z0.glb.clouddn.com/wordcloud2.png)

This document show two main function in `Wordcloud2`:

1. `wordcloud2`: provide traditional wordcloud with HTML5
2. `letterCloud`: provide wordcloud with selected word(letters).

### install wordcloud2

You may have installed this package. Well, I still want to leave these codes here for installing.
```{r eval = F}
devtools::install_github("lchiffon/wordcloud2")
```

### `wordlcoud2` function

You can use wordcloud directly:
```{r eval= F}
library(wordcloud2)
wordcloud2(data = demoFreq)
```
![ex0](http://7xr5em.com1.z0.glb.clouddn.com/ex0.png)

`demoFreq` is a data.frame including word and freq in each column.

```{r eval = F}
head(demoFreq)
```
```{r eval = F}
         word freq
oil       oil   85
said     said   73
prices prices   48
opec     opec   42
mln       mln   31
the       the   26
```



### Parameters
- `data`
  - A data frame including word and freq in each column
- `size`
  - Font size, default is 1. The larger size means the bigger word.
- `fontFamily`	
  - Font to use.
- `fontWeight`	
  - Font weight to use, e.g. normal, bold or 600
- `color`	
  - color of the text, keyword 'random-dark' and 'random-light' can be used. color vector is also supported in this param
- `minSize`	
 - A character string of the subtitle
- `backgroundColor`	
  - Color of the background.
- `gridSize`	
  - Size of the grid in pixels for marking the availability of the canvas the larger the grid size, the bigger the gap between words.
- `minRotation`	
  - If the word should rotate, the minimum rotation (in rad) the text should rotate.
- `maxRotation`	
  - If the word should rotate, the maximum rotation (in rad) the text should rotate. Set the two value equal to keep all text in one angle.
- `rotateRatio`	
  - Probability for the word to rotate. Set the number to 1 to always rotate.
- `shape`	
  - The shape of the "cloud" to draw. Can be a keyword present. Available presents are 'circle' (default), 'cardioid' (apple or heart shape curve, the most known polar equation), 'diamond' (alias of square), 'triangle-forward', 'triangle', 'pentagon', and 'star'.
- `ellipticity`
  - degree of "flatness" of the shape wordcloud2.js should draw.
- `figPath`
  - A fig used for the wordcloud.
- `widgetsize`	
  - size of the widgets

#### Example1: use color and backgroundcolor
```{r eval = F}
wordcloud2(demoFreq, color = "random-light", backgroundColor = "grey")
```
![png](http://7xr5em.com1.z0.glb.clouddn.com/ex1.png)

#### Example2: use rotations

```{r}
wordcloud2(demoFreq, minRotation = -pi/6, maxRotation = -pi/6, minSize = 10,
  rotateRatio = 1)
```
![png](http://7xr5em.com1.z0.glb.clouddn.com/ex3.png)

#### Example3: use figure file as a mask.

For example, `t.png` is A BIRD with black and white:
![png](http://7xr5em.com1.z0.glb.clouddn.com/t.png)

```{r eval = F}
figPath = system.file("examples/t.png",package = "wordcloud2")
wordcloud2(demoFreq, figPath = figPath, size = 1.5,color = "skyblue")
```
![png](http://7xr5em.com1.z0.glb.clouddn.com/tcloud.png)

### `letterCloud` function 

`letterCloud` provide the function to create a wordcloud with a word, like this:
```{r eval = F}
letterCloud(demoFreq, word = "R", size = 2)
```
![png](http://7xr5em.com1.z0.glb.clouddn.com/R.png)

Or:
```{r eval = F}
letterCloud(demoFreq, word = "WORDCLOUD2", wordSize = 1)
```
![png](http://7xr5em.com1.z0.glb.clouddn.com/wordcloud2.png)
**wordcloud with fig and letterCloud may disappeared in Rstudio Viewer, open into browser when you meet this bug**

#### Parameters

- `data`	
  - A data frame including word and freq in each column
- `word`	
  - A word to create shape for wordcloud.
- `wordSize`
  - Parameter of the size of the word, default is 2.
- `letterFont`	
  - Letter font
- `...`
  - Other parameters for wordcloud2
Go to [wordcloud2](http://github.com/lchiffon/wordcloud2) in the github to leave a comment or give this package a star.


