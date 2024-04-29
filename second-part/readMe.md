# Exercices d'introduction à Node.js

Veillez à bien regarder les informations dans l'environnement !

## Prérequis
- Installer Node.js
- Installer Postman

## Exercice 0 : Commencement


-   Initialiser votre projet grâce à npm

-   Créer l'arborescence de base

   ```
   ./
    ├── .env
    ├── package.json
    ├── index.js
    ├── routes/
    │   ├── routes.js
    |   ├── birthdayRoutes.js
    │   └── registerRoutes.js
    ├── middleware/
        └── existFileMiddleware.js
   ```

-   Installer Express

**Initialiser le premier serveur avec Express** :
   - Dans le fichier `server.js`, initialisez un serveur Express de base :

   Une fois cela bien fait vous devriez avoir ceci dans la console :
    ```
        Serveur sur le port 3000 !
    ```

    ATTENTION LE PORT NE DOIT PAS ÊTRE ECRIT EN DUR ! SERVEZ-VOUS DE L'ENVIRONNEMENT !

---

## Exercice 1 : CRUD

A l'aide de la méthode CRUD, créez ces différentes routes :

```
GET /birthday
POST /add-birthday
DELETE /delete-birthday
PUT /modify-birthday
```

### Description des routes :

1. **`GET /birthday`** :
   - Cette route permet de récupérer la liste des anniversaires à partir du fichier `birthday_list.txt`.
   - Lorsqu'un client envoie une requête GET à cette route, le serveur lit le contenu du fichier `birthday_list.txt` et renvoie la liste des anniversaires.

2. **`POST /add-birthday`** :
   - Cette route permet d'ajouter un nouvel anniversaire à la liste.
   - Lorsqu'un client envoie une requête POST à cette route avec les données de l'anniversaire à ajouter, le serveur les ajoute à la liste dans le fichier `birthday_list.txt`.

3. **`DELETE /delete-birthday`** :
   - Cette route permet de supprimer un anniversaire de la liste.
   - Lorsqu'un client envoie une requête DELETE à cette route avec l'identifiant de l'anniversaire à supprimer, le serveur supprime cet anniversaire de la liste dans le fichier `birthday_list.txt`.

4. **`PUT /modify-birthday`** :
   - Cette route permet de modifier un anniversaire existant dans la liste.
   - Lorsqu'un client envoie une requête PUT à cette route avec l'identifiant de l'anniversaire à modifier et les nouvelles données, le serveur met à jour cet anniversaire dans la liste dans le fichier `birthday_list.txt`.

### Test avec Postman :

- Utilisez Postman pour tester chacune des routes en envoyant des requêtes HTTP (GET, POST, DELETE, PUT) avec les données appropriées.
- Assurez-vous que chaque route fonctionne correctement et renvoie les réponses attendues.

---

## Exercice 2 : Middleware de vérification de fichier

Dans cet exercice, nous allons créer un middleware pour vérifier si un fichier existe avant de procéder à certaines opérations.


**Création du middleware de vérification de fichier** :
   - Dans le dossier `middleware`, créez un nouveau fichier nommé `existFileMiddleware.js`.
   - Dans ce fichier, implémentez un middleware qui vérifie si un fichier existe à un chemin spécifié.
   - Vérifiez si le fichier `birthday_list.txt` existe avant chaque route.
   - Si le fichier existe, le middleware appelle la fonction `next()` pour passer au middleware suivant dans la chaîne de middleware. Sinon, il renvoie le status 404.


### Test avec Postman :

- Utilisez Postman pour tester chaque route qui utilise le middleware de vérification de fichier.
- Assurez-vous que le middleware fonctionne correctement en vérifiant si le fichier existe avant de procéder aux opérations de lecture, d'écriture ou de suppression.

Voici l'exercice 3 qui consiste à créer une route "register" utilisant JSON Web Tokens (JWT) pour renvoyer un token :

---

## Exercice 3 : Authentification avec JWT

Dans cet exercice, nous allons créer une route "register" qui permettra aux utilisateurs de s'inscrire et de recevoir un token JWT en réponse.


**Création de la route "register"** :
   - Créez une nouvelle route POST `/register`.
   - Cette route recevra les informations de l'utilisateur (name et password) dans le corps de la requête.
   - la route générera un token JWT à l'aide d'une clé secrète et des informations de l'utilisateur et renverra ce token JWT dans la réponse.

**Utilisation de JWT pour générer et vérifier les tokens** :
   - Utilisez le module `jsonwebtoken` pour générer et vérifier les tokens JWT.

### Test avec Postman :

- Utilisez Postman pour envoyer une requête POST à la route `/register` avec les informations d'inscription d'un utilisateur.
- Assurez-vous que la route renvoie un token JWT valide en réponse ou 500.
- Utilisez le token JWT renvoyé pour accéder à d'autres routes sécurisées de votre application (par exemple, en utilisant un middleware d'authentification).
