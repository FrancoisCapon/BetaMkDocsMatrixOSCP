# BetaMkDocsMatrixOSCP

Le final [`print.pdf`](https://github.com/FrancoisCapon/BetaMkDocsMatrixOSCP/raw/main/matrix/print/print.pdf) est obtenu à l'aide des éléments suivants  :

1. un [plugin MkDocs](https://github.com/FrancoisCapon/BetaMD2WPMR) dont le rôle est d'exporter dans la matrice dans la colonne `50` :
    * la table des matières
    * le contenu du rapport
1. cette matrice avec :
    * en colonnes `05` à `15` une mise en forme générale et neutre du rapport
    * en colonne `20` la mise en forme OSCP
    * en colonne `30` la personnalisation du rapport
    * ⚠️ seule la colonne `30`doit être utilisée pour la personnalisation
1. les [Robots WeasyPrint](https://github.com/FrancoisCapon/TheWeasyPrintMatrixRobotsProject) qui vont produire le PDF à partir de la matrice

## 1️⃣ Le plugin [MD2WPMR](https://github.com/FrancoisCapon/BetaMD2WPMR)
Après chargement du dépôt, il doit être installé avec Beautiful Soup ans votre "environnement python" MkDocs  :
```
pip install -e .
pip install beautifulsoup4
```
## :two: La matrice
La matrice du dépôt est une matrice d'exemple qui utilise la documentation de MkDocs avec quelques légères modifications pour différents tests de mise en forme.
Le plugin et sa configuration est ajouter au fichier `mkdocs.yml`.
```yaml
...
plugins:
    - search
    # fc export plugin
    - md2wpmr:
        number_column : 50
        number_row_toc : 5200
        number_row_pages : 5400
```
* Le plugin n'est appelé que lors du build `mkdocs build`.
* Attention le plugin stop le build après l'export, donc il est nécessaire de le désactiver (en commentant ses lignes) pour obtenir un build site "normal".
* Après validation du processus sur ce projet d'exemple, la matrice doit être recopier dans votre "projet OSCP".

## :three: Les Robots WeasyPrint
La documentation du dépôt **[TheWeasyPrintMatrixRobotsProject](https://github.com/FrancoisCapon/TheWeasyPrintMatrixRobotsProject#readme)** traite de tous les aspects relatifs aux Robots.

Le lancement de la génération du PDF s'effectue depuis un "environnement Robots WeasyPrint" (container recommandé) en lançant le script Python `print.py` situé à la racine de la matrice :
```python
#!/usr/bin/env python3
from weasyprintmatrixrobots.robot_manager import Manager
Manager('.').do_job()
```

