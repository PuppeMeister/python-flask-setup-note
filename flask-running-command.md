## Running Flask Application in Powershell

### 1. Adding FLASK_APP and FLASK_ENV Variable

```
$env:FLASK_APP='[NAME-OF-THE-MAIN-APPLICATION-MODULE]'
$env:FLASK_ENV='development'
flask run
```
