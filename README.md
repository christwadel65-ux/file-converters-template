# 🔄 file-converters-template

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Version](https://img.shields.io/badge/python-3.8+-blue.svg)
![License](https://img.shields.io/github/license/christwadel65-ux/file-converters-template)
![Stars](https://img.shields.io/github/stars/christwadel65-ux/file-converters-template?style=social)

> 🔧 **Tagline** : Convertisseur rapide et fiable pour [FORMAT_A] → [FORMAT_B]

---

## 📸 Aperçu

![Demo](docs/demo.gif)

```bash
$ python converter.py input.dxf
✓ Chargement du fichier...
✓ Conversion en cours...
✓ Fichier converti avec succès: output.dwg
```

---

## ✨ Fonctionnalités

- ✅ **Conversion rapide** : Traitement optimisé pour les gros fichiers
- ✅ **Batch processing** : Convertir plusieurs fichiers en une seule commande
- ✅ **Formats multiples** : Support de [FORMAT_A], [FORMAT_B], [FORMAT_C]
- ✅ **Préservation des données** : Conservation de toutes les métadonnées
- ✅ **Interface CLI** : Facile à automatiser et scripter
- ✅ **Cross-platform** : Windows, macOS, Linux

---

## 🚀 Installation

### Prérequis

- Python 3.8+
- pip

### Installation rapide

```bash
# Cloner le repo
git clone https://github.com/christwadel65-ux/file-converters-template.git
cd file-converters-template

# Installer les dépendances
pip install -r requirements.txt
```

### Via pip (si publié)

```bash
pip install file-converters-template
```

### Installation en environnement virtuel (recommandé)

```bash
# Créer l'environnement
python -m venv venv

# Activer (Windows)
venv\Scripts\activate

# Activer (Linux/Mac)
source venv/bin/activate

# Installer
pip install -r requirements.txt
```

---

## 💻 Utilisation

### Usage basique

```bash
# Convertir un seul fichier
python converter.py input.dxf

# Spécifier le fichier de sortie
python converter.py input.dxf -o output.dwg

# Convertir tous les fichiers d'un dossier
python converter.py --batch ./input_folder/
```

### Options avancées

```bash
# Avec options de qualité
python converter.py input.dxf --quality high

# Mode verbose
python converter.py input.dxf -v

# Ignorer les erreurs
python converter.py --batch ./folder/ --ignore-errors

# Dry run (simulation)
python converter.py input.dxf --dry-run
```

### Options CLI

| Option | Alias | Description | Défaut |
|--------|-------|-------------|--------|
| `--output` | `-o` | Fichier de sortie | `[input]_converted.[ext]` |
| `--batch` | `-b` | Conversion par lot | - |
| `--quality` | `-q` | Qualité (low/medium/high) | `medium` |
| `--verbose` | `-v` | Mode verbeux | `false` |
| `--ignore-errors` | | Ignorer les erreurs | `false` |
| `--dry-run` | | Simulation sans conversion | `false` |
| `--help` | `-h` | Afficher l'aide | - |

---

## 📚 API Python

### Utilisation programmatique

```python
from converter import FileConverter

# Initialiser le convertisseur
converter = FileConverter()

# Convertir un fichier
result = converter.convert(
    input_path='input.dxf',
    output_path='output.dwg',
    quality='high'
)

if result.success:
    print(f"✓ Converti : {result.output_path}")
    print(f"  Taille : {result.size_kb} KB")
    print(f"  Temps : {result.duration_ms} ms")
```

### Conversion par lot

```python
from converter import BatchConverter

# Convertir un dossier
batch = BatchConverter()
results = batch.convert_folder(
    input_folder='./input',
    output_folder='./output',
    pattern='*.dxf'
)

print(f"Réussis : {results.success_count}/{results.total_count}")
```

### Avec callbacks

```python
def on_progress(filename, percent):
    print(f"{filename}: {percent}%")

def on_complete(filename, success):
    if success:
        print(f"✓ {filename}")
    else:
        print(f"✗ {filename}")

converter = FileConverter()
converter.on_progress = on_progress
converter.on_complete = on_complete

converter.convert('input.dxf')
```

---

## 🎯 Formats supportés

### Formats d'entrée

- ✅ `.dxf` - AutoCAD Drawing Exchange Format
- ✅ `.dwg` - AutoCAD Drawing (lecture)
- ⏳ `.dwf` - Design Web Format (à venir)

### Formats de sortie

- ✅ `.dwg` - AutoCAD Drawing
- ✅ `.pdf` - Portable Document Format
- ✅ `.svg` - Scalable Vector Graphics
- ⏳ `.png` - Raster image (à venir)

---

## ⚙️ Configuration

### Fichier de configuration

Créez un fichier `config.json` :

```json
{
  "default_quality": "high",
  "output_format": "dwg",
  "preserve_metadata": true,
  "compression": true,
  "auto_backup": false,
  "max_file_size_mb": 100
}
```

### Variables d'environnement

```bash
# Définir le dossier de sortie par défaut
export CONVERTER_OUTPUT_DIR=/path/to/output

# Niveau de log
export CONVERTER_LOG_LEVEL=INFO
```

---

## 🏗️ Architecture

```
file-converters-template/
├── src/
│   ├── converter/      # Module principal
│   ├── parsers/        # Parseurs de formats
│   ├── writers/        # Writers de formats
│   └── utils/          # Utilitaires
├── tests/              # Tests unitaires
├── examples/           # Exemples d'utilisation
├── docs/               # Documentation
└── requirements.txt    # Dépendances
```

---

## 🛠️ Technologies

- **Langage** : Python 3.8+
- **Parsing** : ezdxf, pyautocad
- **CLI** : argparse / click
- **Tests** : pytest
- **Linting** : pylint, black

---

## 🧪 Tests

```bash
# Lancer tous les tests
pytest

# Avec couverture
pytest --cov=src

# Tests spécifiques
pytest tests/test_converter.py

# Mode verbeux
pytest -v
```

---

## 📈 Performances

| Format | Taille fichier | Temps conversion |
|--------|----------------|------------------|
| DXF → DWG | 1 MB | ~0.5s |
| DXF → DWG | 10 MB | ~3.2s |
| DXF → DWG | 100 MB | ~28.5s |

*Tests effectués sur : Intel i7, 16GB RAM, SSD*

---

## 🐛 Dépannage

### Erreur : "Module not found"

```bash
pip install -r requirements.txt
```

### Erreur : "Invalid file format"

Vérifiez que le fichier n'est pas corrompu :
```bash
python converter.py --validate input.dxf
```

### Erreur : "Out of memory"

Réduisez la qualité ou utilisez l'option `--low-memory` :
```bash
python converter.py input.dxf --low-memory
```

---

## 🤝 Contribution

Les contributions sont les bienvenues !

1. Fork le projet
2. Créez votre branche (`git checkout -b feature/NewFormat`)
3. Committez vos changements (`git commit -m 'feat: add new format support'`)
4. Poussez vers la branche (`git push origin feature/NewFormat`)
5. Ouvrez une Pull Request

### Ajouter un nouveau format

```python
# src/parsers/new_format.py
from .base import BaseParser

class NewFormatParser(BaseParser):
    def parse(self, filepath):
        # Votre code ici
        pass
```

---

## 📝 Changelog

### v1.0.0 (2025-12-24)
- ✨ Première version stable
- ✅ Support DXF → DWG
- ✅ Mode batch
- 📚 Documentation complète

Voir [CHANGELOG.md](CHANGELOG.md) pour l'historique complet.

---

## ⚠️ Limitations

- Taille maximale de fichier : 500 MB (configurable)
- Certaines entités CAD complexes peuvent être simplifiées
- Nécessite les droits d'écriture dans le dossier de sortie

---

## 📄 Licence

Ce projet est sous licence MIT - voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## 👤 Auteur

**Christ Wadel**

- 🌐 Portfolio : [christwadel65-ux.github.io/Site_git](https://christwadel65-ux.github.io/Site_git/)
- 💼 GitHub : [@christwadel65-ux](https://github.com/christwadel65-ux)
- 📧 Email : [votre-email@example.com]

---

## 🙏 Remerciements

- [ezdxf](https://github.com/mozman/ezdxf) pour le parsing DXF
- Communauté Python CAD
- Tous les contributeurs

---

## 🔗 Liens Utiles

- [Documentation complète](docs/)
- [Exemples](examples/)
- [FAQ](docs/FAQ.md)
- [Signaler un bug](https://github.com/christwadel65-ux/file-converters-template/issues)

---

<div align="center">

**⭐ Utile ? Donnez une étoile !**

</div>

