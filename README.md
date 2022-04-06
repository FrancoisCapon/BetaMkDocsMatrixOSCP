# BetaMkDocsMatrixOSCP

L'impression PDF [`print.pdf`](https://github.com/FrancoisCapon/BetaMkDocsMatrixOSCP/raw/main/matrix/print/print.pdf) est obtenue à l'aide des éléments suivants  :

1. un [plugin MkDocs](https://github.com/FrancoisCapon/BetaMD2WPMR) dont le rôle est d'exporter dans la colonne `50` de la matrice :
    * la table des matières
    * le contenu du rapport
1. cette matrice (celle de ce dépôt) avec :
    * en colonnes `05` à `15` une mise en forme générale et neutre du rapport
    * en colonne `20` la mise en forme OSCP
    * en colonne `30` la personnalisation du rapport
    * ⚠️ seule la colonne `30` doit être utilisée pour la personnalisation
      * exemple le fichier `meta.html`
1. les [Robots WeasyPrint](https://github.com/FrancoisCapon/TheWeasyPrintMatrixRobotsProject) qui vont produire le PDF à partir de la matrice

## 1️⃣ Le plugin [MD2WPMR](https://github.com/FrancoisCapon/BetaMD2WPMR)
Après chargement du dépôt, il doit être installé avec Beautiful Soup dans votre "environnement Python MkDocs"  :
```
pip install -e .
pip install beautifulsoup4
```
## :two: La matrice
La matrice du dépôt est une matrice d'exemple qui utilise la documentation de MkDocs avec quelques légères modifications pour différents tests de mise en forme.
Le plugin et sa configuration est à ajouter au fichier `mkdocs.yml`.
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
* Après validation du processus sur ce projet d'exemple, la matrice doit être recopier dans le "projet OSCP MkDocs".

## :three: Les Robots WeasyPrint
La documentation du dépôt **[TheWeasyPrintMatrixRobotsProject](https://github.com/FrancoisCapon/TheWeasyPrintMatrixRobotsProject#readme)** traite de tous les aspects relatifs aux Robots :robot:.

Le lancement de la génération du PDF s'effectue depuis un "environnement Robots WeasyPrint" (container recommandé) en lançant le script Python `print.py` situé à la racine de la matrice :
```python
mkdocs-project/matrix/print.py

#!/usr/bin/env python3
from weasyprintmatrixrobots.robot_manager import Manager
Manager('.').do_job()
```

