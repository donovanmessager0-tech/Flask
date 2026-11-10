# Flask

Application Flask simple qui vérifie l'état d'une base de données MySQL.

La route `/` renvoie :
- `Database Connection Status: Connected` si la connexion à MySQL fonctionne
- `Database Connection Status: Disconnected` sinon

## Prérequis

- Python 3.13 ou compatible
- MySQL disponible localement ou sur un serveur distant
- Un terminal pour lancer le projet

## 1) Cloner le projet

```bash
git clone https://github.com/donovanmessager0-tech/Flask.git
cd Flask
```

## 2) Créer un environnement virtuel

```bash
python -m venv .venv
```

Activer l'environnement :

- Linux / macOS

```bash
source .venv/bin/activate
```

- Windows PowerShell

```powershell
.venv\Scripts\Activate.ps1
```

## 3) Installer les dépendances

Le dépôt contient le fichier `requirements.text` (avec un `text` à la fin).

```bash
python -m pip install -r requirements.text
```

## 4) Configurer la base de données

L'application utilise les variables d'environnement suivantes :

| Variable | Valeur par défaut | Description |
| --- | --- | --- |
| `DB_HOST` | `localhost` | Hôte MySQL |
| `DB_USER` | `root` | Utilisateur MySQL |
| `DB_PASSWORD` | `""` | Mot de passe MySQL |
| `DB_NAME` | `test` | Nom de la base de données |

Exemples :

- Linux / macOS

```bash
export DB_HOST=localhost
export DB_USER=root
export DB_PASSWORD='votre_mot_de_passe'
export DB_NAME=test
```

- Windows PowerShell

```powershell
$env:DB_HOST = "localhost"
$env:DB_USER = "root"
$env:DB_PASSWORD = "votre_mot_de_passe"
$env:DB_NAME = "test"
```

## 5) Lancer l'application

```bash
python app.py
```

L'application démarrera sur le port `5000`.

Ouvrez ensuite l'URL suivante dans votre navigateur :

```text
http://localhost:5000/
```

## Vérification

Si la connexion à MySQL fonctionne, la page affiche :

```text
Database Connection Status: Connected
```

Sinon :

```text
Database Connection Status: Disconnected
```

## Docker

Le dépôt contient un `DockerFile` qui référence `requirements.txt`, alors que le fichier réel est `requirements.text`.

Cela signifie qu'une image Docker ne pourra pas être construite telle quelle sans corriger ce nom.

Pour lancer avec Docker après correction du fichier :

```bash
docker build -t flask-app .
docker run --rm -p 5000:5000 \
  -e DB_HOST=host.docker.internal \
  -e DB_USER=root \
  -e DB_PASSWORD='votre_mot_de_passe' \
  -e DB_NAME=test \
  flask-app
```

## Notes

- Le projet est minimal et conçu pour tester la connexion à MySQL.
- Le fichier de dépendances s'appelle `requirements.text` et non `requirements.txt` dans ce dépôt.
- Pour un environnement de développement, il est conseillé d'utiliser un virtualenv comme indiqué ci-dessus.
-nb \n# CI Status: Active


## Pistes et démarches
Création d'un fichier ci.yml afin d'automatiser les tests lors de la pull request
utilisation du ruleset de github pour enforcer les tests afin de pouvoir merge la pull request
