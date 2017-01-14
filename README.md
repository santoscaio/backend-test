<p align="center">
  <a href="http://www.catho.com.br">
      <img src="http://static.catho.com.br/svg/site/logoCathoB2c.svg" alt="Catho"/>
  </a>
</p>
# backend-test

Uma pessoa esta a procura de emprego e dentre as várias vagas que existem no mercado (disponibilizadas nesse <a href="https://github.com/catho/backend-test/blob/master/vagas.json">JSON</a>) e ela quer encontrar vagas que estejam de acordo com o que ela saiba fazer, seja direto pelo cargo ou atribuições que podem ser encontradas na descrição das vagas. Para atender essa necessidade precisamos:

- uma API simples p/ procurar vagas (um GET p/ procurar as vagas no .json disponibilizado);
- deve ser possível procurar vagas por texto (no atributos title e description);
- deve ser possível procurar vagas por uma cidade;
- deve ser possível ordenar o resultado pelo salário (asc e desc);

O teste deve ser feito utilizando PHP (com ou sem framework, a escolha é sua). Esperamos como retorno, fora o GET da API funcionando, os seguintes itens:

- uma explicação do que é necessário para fazer seu projeto funcionar;
- como executar os testes, se forem testes de unidade melhor ainda;
- comentários nos códigos para nos explicar o que está sendo feito.

Lembre-se que na hora da avaliação olharemos para:

- organização de código;
- desempenho;
- manutenabilidade.



# API de Busca Vaga

## Configurações
1- criar um vhost
```
<VirtualHost *:80>
    DocumentRoot "C:/xampp/htdocs/busca.local"
    ServerName busca.local
    ErrorLog "logs/busca_local-error.log"
    CustomLog "logs/busca_local-access.log" common
</VirtualHost>
```

2- redirecionar o hosts
```
* C:\Windows\System32\drivers\etc\hosts
* 127.0.0.1	busca.local
```

3- substituir dados de vagas "vagas.json" na pasta caso haja uma nova listagem
```
* \storage\database
```

4- testar URL
    * Chamar a url "busca.local" e validar se retorna o seguinte texto:
```
Busca JSON
Autor: Caio Santos
Email: santoscaio@gmail.com
```

## Endpoints (*CRUD de contato*)
- Todos os retornos são respondidos em HTTP mais a informação em JSON
- Atualmente uso o postman para consumo e teste de api's
- Buscar vaga com palavra chave
    - Busca uma vaga no JSON
    - method: **GET**
    - http://busca.local/vaga/[KEYWORD]
    - ex: http://busca.local/vaga/Analista
    - Campo obrigatório: **[KEYWORD]** => Filtro no titulo ou descrição
    - Retorno: **dados da vaga(s)**
- Buscar vaga com palavra chave e ordenação
    - Busca uma vaga no JSON
    - method: **GET**
    - http://busca.local/vaga/[KEYWORD]/[ORDER]
    - ex: http://busca.local/vaga/Analista/desc/
    - Campo obrigatório: **[KEYWORD]** => Filtro no titulo ou descrição
    - Campo obrigatório: **[ORDER]** => Ordenação por valor do salário
    - Retorno: **dados da vaga(s)**
- Buscar vaga com palavra chave, ordenação e cidade
    - Busca uma vaga no JSON
    - method: **GET**
    - http://busca.local/vaga/[KEYWORD]/[ORDER]/[CITY]
    - ex: http://busca.local/vaga/Analista/asc/Florianópolis
    - Campo obrigatório: **[KEYWORD]** => Filtro no titulo ou descrição
    - Campo obrigatório: **[ORDER]** => Ordenação por valor do salário
    - Campo obrigatório: **[CITY]** => Filtra os resultados da busca pela cidade
    - Retorno: **dados da vaga(s)**

# Extra Documentation
## Semantics and Content of HTTP
https://tools.ietf.org/html/rfc7231

## List of HTTP status codes
https://en.wikipedia.org/wiki/List_of_HTTP_status_codes


# Lumen PHP Framework
## Official Documentation
Documentation for the framework can be found on the [Lumen website](http://lumen.laravel.com/docs).

## License
The Lumen framework is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)
