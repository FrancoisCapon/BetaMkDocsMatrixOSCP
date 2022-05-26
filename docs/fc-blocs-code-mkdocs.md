# Les blocs de Code MkDocs

Il y a deux types de blocs de code disponible dans MkDocs Material :

* bloc de code `SuperFences` (extension du parser Markdown de Python)
* bloc de code `HTML`

Références :

* [Material for MkDocs > Code blocks](https://squidfunk.github.io/mkdocs-material/reference/code-blocks/)
* [Python-Markdown](https://python-markdown.github.io/)
* [SuperFences](https://facelessuser.github.io/pymdown-extensions/extensions/superfences/)

## Bloc de Code `SuperFences` MkDocs

Ce type de bloc de code permet de :

* coloriser syntaxiquement le code si un langage est indiqué : ` ```python `
* mettre en évidence des lignes ` ```hl_lines="2 3 10-15"  ` (lignes 2, 3 et de 10 à 15)
* numéroter les lignes ` ```linenums="5" ` (numérotation des lignes commençant à 5)

Ces différentes options peuvent être combinées :

```
```python hl_lines="2 5-6" linenums="1"
#!/usr/bin/python
# Note: see how to craft FEALIST in eternalblue_poc.
from impacket import smb
from struct import pack
import sys
import socket
```
<figcaption>Syntaxe de code combinant les différentes options</figcaption>

```python hl_lines="2 5-6" linenums="1"
#!/usr/bin/python
# Note: see how to craft FEALIST in eternalblue_poc.
from impacket import smb
from struct import pack
import sys
import socket
```
<figcaption>Résultat de code combinant les différentes options</figcaption>
!!! note
    Les lignes mises évidences sont en **rouge OSCP** dans le rendu PDF.

```hl_lines="2 5-6" linenums="1"
#!/usr/bin/python
# Note: see how to craft FEALIST in eternalblue_poc.
from impacket import smb
from struct import pack
import sys
import socket
```

## Bloc de Code `HTML` MkDocs

Ce sont des blocs de code standard `HTML`, des éléments peuvent être mis en évidence en utilisant la balise `<mark>`.

!!! note
    Il est nécessaire de traduire les chevrons ouvrants en entité HTML `&lt;` s'il peuvent être interprété comme l'ouverture d'un balise HTML.

```html
<pre><code>
<mark>$ mkdocs serve</mark>
INFO    -  Building documentation...
INFO    -  Cleaning site directory
[I 160402 15:50:43 server:271] <mark>Serving on http://127.0.0.1:8000</mark>
[I 160402 15:50:43 handlers:58] Start watching changes
[I 160402 15:50:43 handlers:60] Start detecting changes &lt;halt>
[I 160402 15:50:43 handlers:58] Start watching changes < halt>
[I 160402 15:50:43 handlers:60] Start detecting changes <halt>
</code></pre>
```
<figcaption>Exemple de bloc de code HTML</figcaption>

<pre><code>
<mark>$ mkdocs serve</mark>
INFO    -  Building documentation...
INFO    -  Cleaning site directory</mark>
[I 160402 15:50:43 server:271] <mark> Serving on http://127.0.0.1:8000</mark>
[I 160402 15:50:43 handlers:58] Start watching changes
[I 160402 15:50:43 handlers:60] Start detecting changes &lt;halt>
[I 160402 15:50:43 handlers:58] Start watching changes < halt>
[I 160402 15:50:43 handlers:60] Start detecting changes <halt>
</code></pre>


