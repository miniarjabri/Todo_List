# 📝 To-Do List - Architecture Microservices

Ce projet est une **application To-Do List** développée en **architecture microservices**. Il comprend plusieurs services indépendants interconnectés via un **API Gateway**.

---

## 📌 **Architecture du Projet**
Le projet est composé des services suivants :

- **Frontend (React)** : Interface utilisateur de l'application  
- **API Gateway (Express.js)** : Router les requêtes vers les services correspondants  
- **Auth Service (Express.js + Passport.js + Google OAuth2)** : Gestion de l’authentification  
- **Task Service (Express.js + MongoDB)** : CRUD des tâches  

Chaque service fonctionne de manière indépendante et peut être **conteneurisé avec Docker**.

---

## 🚀 **Installation & Exécution**

### **1️⃣ Cloner le dépôt**
```sh
git clone <lien-du-repo-github>
cd micro-todo-list
```

### **2️⃣ Lancer les services avec Docker**
```sh
docker-compose up --build
```
ou bien
```sh
cd frontend
npm start 
```
... de meme pour chaque service
> Assurez-vous que **Docker** et **Docker Compose** sont installés sur votre machine.

### **3️⃣ Accéder à l’application**
- **Frontend (React)** : [http://localhost:3002](http://localhost:3002)
- **API Gateway** : [http://localhost:5000](http://localhost:5000)
- **Auth Service** : [http://localhost:4000](http://localhost:4000)
- **Task Service** : [http://localhost:6000](http://localhost:6000)

---

## ⚙️ **Configuration des Variables d’Environnement**
Avant de lancer le projet, créez un fichier **.env** dans chaque service :

### **Auth Service (`auth_service/.env`)**
Google Cloud Platform
```env
GOOGLE_CLIENT_ID=685484338448-bg8a4fmm0dtvlalifosqtdqcg1hekkhk.apps.googleusercontent.com
GOOGLE_CLIENT_SECRET=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
GOOGLE_CALLBACK_URL=http://localhost:4000/auth/google/callback
```
MangoDB
```env
MONGO_USERNAME=TER
MONGO_PASSWORD=TERoauth
MONGO_CLUSTER=cluster0.p3e6b.mongodb.net
MONGO_DB_NAME=todolist
```
### **Task Service (`task_service/.env`)**
```env
MONGO_URI=mongodb://mongo:27017/todo
PORT=6000
```

### **API Gateway (`api_gateway/.env`)**
```env
PORT=5000
AUTH_SERVICE_URL=http://auth_service:4000
TASK_SERVICE_URL=http://task_service:6000
```

### **Frontend (`frontend/.env`)**
```env
REACT_APP_API_URL=http://localhost:5000
```

---

## 📌 **Endpoints des Services**
### **Auth Service**
- `GET /auth/google` → Redirige vers Google OAuth  
- `GET /auth/google/callback` → Callback après login  
- `GET /auth/user` → Retourne les infos de l’utilisateur  
- `GET /auth/logout` → Déconnecte l’utilisateur  

### **Task Service**
- `GET /tasks` → Récupérer toutes les tâches  
- `POST /tasks` → Ajouter une nouvelle tâche  
- `PUT /tasks/:id` → Modifier une tâche  
- `DELETE /tasks/:id` → Supprimer une tâche  

---

## 🛠 **Technologies Utilisées**
- **Backend** : Node.js, Express.js, MongoDB, Passport.js  
- **Frontend** : React.js  
- **Auth** : Google OAuth2  
- **Infrastructure** : Docker, Docker Compose  

---
