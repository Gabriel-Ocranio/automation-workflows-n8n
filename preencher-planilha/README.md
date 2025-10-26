# 🧾 Automação de Preenchimento de Planilha de Notas – n8n + Python

## 💡 Contexto

Uma colega da área administrativa precisava preencher, a cada 15 dias, uma planilha com informações extraídas de vários arquivos `.txt`.

O processo era totalmente manual: ela abria cada arquivo, copiava dados e colava nas colunas correspondentes da planilha — uma tarefa demorada e sujeita a erros.

Durante uma conversa, notei que os nomes dos arquivos já continham todos os dados necessários, separados por hífens.

**Exemplo:**
clienteA-350.00-2025-10-15.txt

Nesse caso, bastava extrair as informações `clienteA`, `350.00` e `2025-10-15` e enviá-las diretamente para a planilha.

Assim surgiu este fluxo, que automatiza todo o processo de coleta e preenchimento — reduzindo o tempo de execução de horas para segundos.

## ⚙️ Como funciona

* **`Schedule Trigger`** → Executa automaticamente a cada 15 dias, às 08h da manhã.
* **`Execute Command`** → Acessa a pasta local com os arquivos `.txt`.
* **`Code in Python (Beta)`** →
    * Lê os nomes dos arquivos;
    * Divide as informações usando o separador "-";
    * Estrutura os dados para envio.
* **`Append or Update Row in Sheet`** → Atualiza a planilha do Google Sheets com as informações extraídas.
* **`Code in Python (Beta)`** → Realiza verificações adicionais e tratamento de erros.
* **`Send a Message (Gmail)`** → Envia um e-mail informando o sucesso (ou falha) do processo.

## 🕒 Agendamento (cron)

O fluxo é executado automaticamente conforme a expressão abaixo:

```cron
0 8 */15 * *
