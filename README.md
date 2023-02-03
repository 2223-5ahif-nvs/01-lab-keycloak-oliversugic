Start the Quarkus Application 
and get the access token with (replace user and password):
```
export access_token=$(\
    curl --insecure -X POST https://keycloak.jakobrathberger.eu/realms/quarkus/protocol/openid-connect/token \
    --user backend-service:secret \
    -H 'content-type: application/x-www-form-urlencoded' \
    -d 'username=<user>&password=<password>&grant_type=password' | jq --raw-output '.access_token' \
)
```

Curl the Endpoint

```
curl -v -X GET http://localhost:8080/api/users/me -H "Authorization: Bearer "$access_token
```
