

## Requetes Curl

authentification sur back-user et tocken sur back-case

# Login (le token est dans la réponse), la requete de login sur back-user est la suivante :
```bash
curl -i -X POST localhost:8081/auth/login -H "Content-Type: application/json" -d '{"email":"ben@exemple.com","password":"Motdepasse1!"}'
```
# Utiliser le token (jq doit être installé, sinon copie le token à la main)
```bash
TOKEN=$(curl -s -X POST localhost:8081/auth/login -H "Content-Type: application/json" -d '{"email":"ben@exemple.com","password":"Motdepasse1!"}' | jq -r .token)
````

### Récupérer tous les dossiers

```bash
curl -i -X GET http://localhost:8082/api/cases \
-H "Authorization: Bearer $TOKEN" \
-H "Accept: application/json"
```

### Créer un dossier

```bash
curl -i -X POST http://localhost:8082/api/cases \
-H "Authorization: Bearer $TOKEN" \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-d '{
"firstName": "Marie",
"lastName": "Dupont",
"dateNaissance": "1980-05-12",
"sexe": "F",
"adresse": {
"numero": 10,
"line1": "rue de la Paix",
"line2": "",
"ville": "Paris",
"codePostal": "75002",
"pays": "France"
},
"phoneNumber": "0600000000"
}'
```# MEDILABO-CASE
