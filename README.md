# PyMoX - GC7

Trousse à outils utiles pour devs en PyMoX

---

## Rapide mémo

```bash
py -m venv .venv
.\.venv\Scripts\activate
pip install -r requirements.txt

py -m build
twine check dist/*  --verbose
twine upload dist/* --verbose

git log --oneline

semantic-release version
semantic-release version --print

semantic-release publish

semantic-release --noop version
Cela te dira si une version serait générée.

semantic-release version --commit --tag --no-push

Cela va :
Lire les commits
Calculer la prochaine version (ex: 0.2.0)
Modifier __version__ dans gc7/__init__.py
Créer un commit et un tag localement

Remove-Item -Recurse -Force dist, src/gc7/gc7.egg-info

git commit --allow-empty -m "feat: add dummy feature for version bump"
git commit --allow-empty -m "fix: déclenchement de la release 1.0.1" 
git push origin main

voir conventional commits: https://www.conventionalcommits.org/en/v1.0.0/

En cas de volonté de revenir sur une version précédente (Problème avec PyPI: Interdit de reculer):
git revert <hash du commit> (pour ramener la main du dépôt GH)
dans le __ini__.py, mettre : __version__='x.y.z' (> au dernier de PyPI)
refaire le build + renvoi:
py -m build    
twine upload dist/*

Désinstaller tous les packages de l'env global :
pip freeze | ForEach-Object { pip uninstall -y $_ }

# 1. Crée une branche temporaire pour garder les fichiers
git checkout --orphan temp_branch

# 2. Ajoute tous les fichiers à cette nouvelle branche
git add .

# 3. Fais un commit initial
git commit -m "Initial commit"

# 4. Supprime l'ancienne branche main
git branch -D main

# 5. Renomme la branche temporaire en main
git branch -m main

# 6. Force le push vers GitHub (⚠️ cela écrase l’historique distant)
git push -f origin main


```
