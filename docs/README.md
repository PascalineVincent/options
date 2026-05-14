# Portail Options Pédagogiques 2026-2027

## Structure des fichiers

```
├── _interface.html          ← Interface web (NE PAS MODIFIER)
├── generer_portail.R        ← Script principal : génère docs/index.html
├── plateforme_options.qmd   ← Fonctions R d'affectation (pour RStudio)
├── _quarto.yml              ← Config projet
├── custom.scss              ← Thème (inchangé)
├── demo_google_form_2026.xlsx    ← Données démo étudiants
├── demo_redoublants_2026.xlsx    ← Données démo redoublants
└── docs/
    └── index.html           ← Portail généré ← GitHub Pages lit ici
```

## Générer le portail (docs/index.html)

**Depuis R/RStudio :**
```r
source("generer_portail.R")
```

**Depuis le terminal :**
```bash
Rscript generer_portail.R
```

> ⚠️ Ne pas utiliser `quarto render` pour générer le portail —  
> Quarto affiche son propre HTML vide autour du rendu.  
> `plateforme_options.qmd` contient uniquement les fonctions R d'affectation.

## Déployer sur GitHub Pages

```bash
git add docs/index.html
git commit -m "deploy portail 2026-27"
git push
```

Activer GitHub Pages : Settings → Pages → Branch: main → Folder: /docs

## Mots de passe

| Espace | Mot de passe |
|--------|-------------|
| Administration | `options2026!` |
| Enseignant | `enseignant2026!` |

## Workflow affectation (R)

```r
source("generer_portail.R")  # charge aussi les fonctions

# Démo (60 étudiants fictifs)
run_affectation()

# Workflow réel
run_affectation(
  fichier_google = "voeux_2026.xlsx",
  fichier_retour = "retour_enseignants.xlsx"
)
```
