# 📡 NextGen Social Network Backend

Un backend moderne et sécurisé pour un réseau social temps réel, basé sur **FastAPI**, **MongoDB**, **JWT**, **WebSockets** et **contenu chiffré avec Fernet**.  
Conçu pour être **rapide, modulaire et facilement extensible**.

---

## 🚀 Fonctionnalités

- ✅ Inscription / Connexion avec email + mot de passe (bcrypt + JWT)
- ✅ Création de posts **chiffrés** (cryptographie symétrique)
- ✅ Affichage des posts avec déchiffrement côté serveur
- ✅ Like des posts
- ✅ Ajout de commentaires
- ✅ WebSocket en temps réel pour les nouveaux posts (`/ws/feed`)
- ✅ Rate limiting intégré avec `slowapi`
- ✅ REST API documentée automatiquement avec Swagger

---

## 🛠️ Prérequis

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- Python 3.11 (pour exécution locale)

---

## ⚙️ Installation

### 1. Cloner le dépôt

```bash
git clone https://github.com/ton-utilisateur/nextgen-social-backend.git
cd nextgen-social-backend
2. Configurer les variables d'environnement
Copier le fichier .env.example et compléter les secrets :

bash
Copier
Modifier
cp .env.example .env
Pour générer une clé Fernet (32 bytes encodée base64) :

bash
Copier
Modifier
python -c "from cryptography.fernet import Fernet; print(Fernet.generate_key().decode())"
🐳 Lancer avec Docker
bash
Copier
Modifier
docker-compose up --build -d
L'API sera disponible sur http://localhost:8000.

🧪 Lancer en local sans Docker
bash
Copier
Modifier
pip install -r requirements.txt
uvicorn app.main:app --reload
🔐 Authentification
JWT via Authorization: Bearer <token>

Token obtenu via /auth/login

📚 Principaux Endpoints

Méthode	Route	Description
POST	/auth/register	Créer un compte
POST	/auth/login	Obtenir un token JWT
GET	/posts?limit=50	Lister les derniers posts
POST	/posts	Créer un post (auth)
POST	/posts/{id}/like	Liker un post (auth)
POST	/comments/{post_id}	Commenter un post (auth)
WS	/ws/feed	WebSocket pour nouveaux posts
📦 Stack Technique
FastAPI – Framework web moderne et rapide

MongoDB (Motor) – Base NoSQL asynchrone

Pydantic – Validation des schémas

JWT / Bcrypt – Authentification sécurisée

Fernet (Cryptography) – Chiffrement du contenu

SlowAPI – Limitation du nombre de requêtes

WebSockets – Notifications temps réel

✨ Idées d'améliorations
Pagination avec cursor/timestamp

Refresh token JWT

WebSocket aussi pour likes / commentaires

Tests automatisés avec pytest et httpx

Frontend React ou Vue avec WebSocket intégré
