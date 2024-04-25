# Explorando-o-Rest-Assured-Para-a-Automa-o-de-Testes-de-API

[1]: https://allurereport.org/ ""
[2]: https://allurereport.org/docs/robotframework/ ""
[3]: https://www.dezlearn.com/allure-reporting/ ""
[4]: https://allurereport.org/docs/how-it-works/ ""
[5]: https://medium.com/testvagrant/generating-allure-reports-in-the-pytest-framework-89dc78a2ca85 ""
[6]: https://www.baeldung.com/rest-assured-tutorial ""
[7]: https://www.baeldung.com/rest-assured-response ""
[8]: https://www.toolsqa.com/rest-assured-tutorial/ ""
[9]: https://www.appsdeveloperblog.com/create-a-junit-5-test-case-with-rest-assured-video-tutorial/ ""
[10]: https://github.com/typicode/json-server ""
[11]: https://www.jsonserver.io/ ""
[12]: https://www.jsonserver.io/features/ ""
[13]: https://www.jsonserver.io/pricing/ ""
[14]: http://localhost:8080/events?id=390 ""
[15]: http://localhost/ ""
[16]: http://localhost:3000/posts/1 ""
[17]: https://fair.io/ ""
[18]: https://api.jsonsever.io/ ""
[19]: https://api.jsonserver.io/products/ ""
[20]: https://api.jsonserver.io/ ""

Vamos explorar o projeto de automação de testes de API usando o **RestAssured**, **JUnit** e o **Allure Framework**. Também abordaremos o **JsonServer** para simular uma API e incrementar nossa suíte de testes.

## RestAssured e JUnit
O **RestAssured** é uma biblioteca que simplifica a validação e teste de APIs REST. Ele oferece suporte sólido para operações HTTP, como verbos HTTP padrão e operações mais avançadas. O **JUnit** é um framework de teste unitário amplamente utilizado em Java. Vamos usá-lo para estruturar nossos testes e executá-los.

## Allure Framework
O **Allure Framework** é uma ferramenta de relatórios para testes automatizados. Ele gera relatórios HTML visualmente atraentes e detalhados a partir dos resultados dos testes. Vamos integrá-lo ao nosso projeto para criar relatórios de qualidade.

## JsonServer
O **JsonServer** é uma ferramenta que nos permite criar uma API REST falsa com dados fictícios. Ele é útil para simular uma API real durante o desenvolvimento e testes. Vamos usá-lo para incrementar nossa suíte de testes.

### Exemplo Prático
Vamos começar com um exemplo simples de teste usando o **RestAssured** e o **JUnit**. Suponha que temos uma API que retorna informações sobre posts e comentários. Aqui está um exemplo de como podemos verificar se um post específico tem o título correto:

```java
import io.restassured.RestAssured;
import org.junit.jupiter.api.Test;
import static org.hamcrest.Matchers.*;

public class PostApiTest {

    @Test
    public void verifyPostTitle() {
        RestAssured.baseURI = "http://localhost:8080"; // URL da API
        RestAssured.given()
            .when()
                .get("/posts/1") // Endpoint para obter o post com ID 1
            .then()
                .statusCode(200)
                .body("title", equalTo("a title")); // Verifica se o título é "a title"
    }
}
```

### Configurando o Allure
Para gerar relatórios com o **Allure Framework**, siga estas etapas:
1. Instale o **Allure Report** (se ainda não estiver instalado).
2. Execute seus testes com o **Allure** como ouvinte (listener).
3. Use o comando `allure generate` para criar relatórios HTML a partir dos resultados dos testes.

### Simulando a API com JsonServer
Crie um arquivo `db.json` com dados fictícios para simular sua API. Por exemplo:

```json
{
  "posts": [
    {
      "id": "1",
      "title": "a title",
      "views": 100
    },
    {
      "id": "2",
      "title": "another title",
      "views": 200
    }
  ],
  "comments": [
    {
      "id": "1",
      "text": "a comment about post 1",
      "postId": "1"
    },
    {
      "id": "2",
      "text": "another comment about post 1",
      "postId": "1"
    }
  ],
  "profile": {
    "name": "typicode"
  }
}
```

Execute o JsonServer com o comando:

```bash
npx json-server db.json
```

Agora você tem uma API falsa para testar seu projeto!

Lembre-se de adaptar esses exemplos ao seu projeto específico.

https://academiapme-my.sharepoint.com/:p:/g/personal/kawan_dio_me/EZdKR9y_VuFOnjnEII7LgWQBbh-QXKAWzqvVOeB2cm-roQ?e=73X2qA

https://github.com/digitalinnovationone/api-automation-tests-challenge-rest-assured
