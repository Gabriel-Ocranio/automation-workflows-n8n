# Microserviço de Consulta e Enriquecimento de CNPJ (n8n)

Este projeto é um microserviço construído na plataforma de automação n8n. Ele expõe um endpoint (via Webhook) que recebe um número de CNPJ, realiza uma validação robusta, consulta uma API externa (ReceitaWS) e enriquece os dados antes de retorná-los ao solicitante.

O objetivo é centralizar a lógica de consulta e validação de CNPJ, oferecendo um serviço rápido e confiável que pode ser consumido por qualquer outra aplicação (CRM, ERP, formulários web, etc.).

## 💡 Funcionalidades Principais

* **Endpoint API via Webhook `GET`**: Permite a consulta de CNPJ através de um simples parâmetro na URL.
* **Validação de CNPJ (Pré-API)**: Antes de consultar a API externa, o fluxo valida o CNPJ (tamanho, dígitos verificadores e lista de exclusão de números inválidos) para economizar recursos e tempo.
* **Tratamento de Erros**: Retorna um status `HTTP 400 (Bad Request)` com uma mensagem de erro clara caso o CNPJ seja inválido.
* **Consulta à ReceitaWS**: Busca os dados cadastrais completos da empresa.
* **Enriquecimento de Dados**: Traduz o código da "Natureza Jurídica" (ex: "213-5") para uma classificação de conta legível (ex: "Entidades Empresariais").
* **Controle de Rate Limit**: Inclui um nó de "Wait" para garantir o respeito aos limites de requisição da API pública.

## ⚙️ Como Funciona (Fluxo do Workflow)

1.  **Webhook (GET)**: Recebe a requisição em `.../product/busca-cnpj-ws?cnpj=XXXXXXXXXXXXXX`. O `cnpj` é capturado como um *query parameter* (parâmetro de consulta) da URL.
2.  **Code (Valida CNPJ)**: Um nó de código JavaScript executa a validação completa dos dígitos verificadores e formato do CNPJ.
3.  **If (CNPJ Válido?)**:
    * **Se Falso**: O fluxo segue para um nó "Respond to Webhook" que retorna imediatamente um `HTTP 400` com a mensagem de erro.
    * **Se Verdadeiro**: O fluxo continua.
4.  **Wait**: Aguarda 1 segundo para evitar problemas de *rate limiting* com a API pública da ReceitaWS.
5.  **HTTP Request (ReceitaWS)**: Faz a chamada `GET` para `https://receitaws.com.br/v1/cnpj/[CNPJ]` para obter os dados.
6.  **Code (Classificação Empresa)**: Pega o código da `natureza_juridica` retornado pela API e o compara com uma tabela de "de-para" (hardcoded no nó) para adicionar uma nova chave `classificacao_conta` ao objeto.
7.  **Code (Prepara Retorno)**: Formata o JSON de saída final, padronizando a resposta.
8.  **Respond to Webhook (Status 200)**: Devolve o objeto JSON completo e enriquecido para o solicitante.

## 🚀 Uso da API

### Endpoint

`GET {URL_BASE_N8N}/webhook/product/busca-cnpj-ws`

### Parâmetros de Consulta (Query Params)

| Parâmetro | Tipo   | Obrigatório | Descrição                                  |
| :-------- | :----- | :---------- | :----------------------------------------- |
| `cnpj`    | string | Sim         | O número do CNPJ (pode conter máscara ou apenas números). |

### Exemplo de Requisição (usando cURL)

```bash
curl -X GET "[https://seu-dominio-n8n.com/webhook/product/busca-cnpj-ws?cnpj=27165729000174](https://seu-dominio-n8n.com/webhook/product/busca-cnpj-ws?cnpj=27165729000174)"


