# Guide de compilation du mémoire

## Démarrage rapide (3 minutes)

**Sur Overleaf (recommandé) :**
1. Télécharger le dépôt en ZIP puis *New Project → Upload Project*.
2. Dans *Menu → Compiler*, choisir **XeLaTeX**.
3. Cliquer sur Recompile (deux fois si besoin pour références et glossaire).
4. Télécharger le PDF ; vérifier qu'aucun marqueur rouge n'y apparaît.

**Sur son ordinateur (une fois TeX Live complet ou MiKTeX installé) :**

```bash
latexmk -xelatex -interaction=nonstopmode main.tex
```

Pour valider le PDF, trois contrôles sont obligatoires : zéro marqueur rouge
(`grep -rn 'acompleter\|amesurer' --include='*.tex' .` ne doit renvoyer que la
définition des commandes dans `main.tex`), aucune erreur `Undefined` dans le
journal de compilation, et contrôle visuel de la page de garde, du sommaire, de
la bibliographie et des annexes.

---

## Pourquoi ce guide

Le bac à sable de rédaction ne dispose d'aucune distribution LaTeX ni d'un accès
aux miroirs TeX Live : le PDF ne peut pas y être généré. La compilation doit
être effectuée sur votre poste ou sur Overleaf.

## Moteur recommandé : XeLaTeX

La classe `ifri.cls` charge les paquets `pstricks`, `pst-node` et `pst-tree`.
PSTricks repose sur des primitives PostScript : avec pdfLaTeX, le chargement
échoue ou nécessite une chaîne `latex → dvips → ps2pdf`. **XeLaTeX gère
PSTricks nativement** et accepte tous les paquets utilisés (`babel`,
`glossaries`, `algorithm2e`, `tikz`, `natbib`, `nomencl`, `minitoc`).

Aucune commande PSTricks n'est utilisée dans le corps du document : si votre
jurys/examinateur exige pdfLaTeX, la seule alternative propre est de commenter
la ligne PSTricks de `ifri.cls` après accord, puis de recompiler — à ne faire
qu'en dernier recours, car `ifri.cls` est le modèle officiel.

## Option 1 — Overleaf (la plus simple)

1. Importer tout le dépôt en ZIP (Menu → New Project → Upload Project).
2. Menu → **Compiler : XeLaTeX**.
3. La compilation déclenche automatiquement BibTeX et `makeglossaries`.
4. Si les références ou le glossaire n'apparaissent pas, lancer deux
   recompilations complètes (Menu → Recompile).

## Option 2 — TeX Live local (Linux / macOS / Windows)

Installer une distribution complète (TeX Live « full » ou MiKTeX avec
installation automatique des paquets), puis, depuis la racine du dépôt :

```bash
latexmk -xelatex -interaction=nonstopmode main.tex
```

`latexmk` enchaîne automatiquement XeLaTeX, BibTeX et `makeglossaries`
autant de fois que nécessaire.

### Chaîne manuelle équivalente

```bash
xelatex -interaction=nonstopmode main.tex
makeglossaries main
bibtex main
xelatex -interaction=nonstopmode main.tex
xelatex -interaction=nonstopmode main.tex
```

## Vérifications obligatoires avant le dépôt

1. Aucun marqueur rouge ne doit subsister :

   ```bash
   grep -rn 'acompleter\|amesurer' --include='*.tex' .
   ```

   (La définition des commandes dans `main.tex` est normale ; toute autre
   occurrence correspond à une information encore manquante.)

2. Le journal de compilation ne doit contenir ni `Undefined control sequence`,
   ni `Citation ... undefined`, ni `Reference ... undefined`, ni
   `LaTeX Error`. Les avertissements (`Warning`) de débordement de ligne sont à
   corriger dans la mesure du possible.
3. Contrôler visuellement : page de garde remplie, sommaire à jour, liste des
   acronymes complète, tableaux et figures numérotés, bibliographie sans
   entrée orpheline, annexes A à H présentes.
4. Vérifier que les annexes reposant sur des documents externes (autorisation
   signée, schémas du service, résultats bruts) contiennent bien les pièces
   réelles avant de verrouiller le PDF.

## Artefacts

Les fichiers générés (`.aux`, `.log`, `.toc`, `.gls`, `.bbl`, `.pdf`
temporaires, etc.) sont exclus du suivi Git par `.gitignore`. Le PDF final
peut être ajouté volontairement au moment du dépôt, il n'est pas ignoré.
