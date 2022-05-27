# Autenticação

Até agora, todas as APIs que usamos responderiam com prazer a qualquer solicitação. Na realidade, a maioria das APIs contém informações confidenciais que não devem ser acessíveis a todos.

Para proteger os dados, as APIs usam alguma forma de `autenticar` o usuário. Autenticar significa essencialmente: verificar a identidade do usuário. O servidor os "conhece" ou é um completo estranho?

A forma mais simples de autenticação é apropriadamente chamada de _basic_. Da mesma forma que você faz login em um site, a autenticação básica espera um nome de usuário e uma senha. Isso é enviado na solicitação como parte do cabeçalho, sob o tipo: `Autorização`. O conteúdo do cabeçalho é: `Basic <username>:<password>`.

Naturalmente, há captura. O nome de usuário e a senha não são enviados como texto simples, mas precisam ser codificados em base64, que é uma forma de codificação de texto para uso em HTTP.

Para este exercício, você fará uma solicitação de API usando o Node.js. Você fará uma solicitação a uma API que exige que você se autentique.

A API pode ser encontrada em https://restapiabasicauthe-sandbox.mxapps.io/api/books. Para usá-lo, você precisa usar as credenciais `admin:hvgX8KlVEa` para autenticar.

Siga os passos:

1. Visite https://www.base64encode.org/ para converter as seguintes credenciais para codificação base64:

``` md
administrador:hvgX8KlVEa
```

2. Defina o cabeçalho de autorização e o URL da API na solicitação GET (use `node-fetch`)

``` js
fetch(<INSERT_API_URL>, {
    headers: { 'Autorização': 'Básico <INSERT_BASE64_CREDENTIALS>' }
  });
```

3. Imprima a resposta no console

Use `async/await` e `try/catch`
