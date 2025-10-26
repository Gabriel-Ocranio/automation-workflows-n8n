# automation-workflows-n8n
Este repositório reúne workflows que desenvolvi no n8n para automatizar tarefas e conectar sistemas de forma prática e eficiente. Aqui compartilho automações reais, testes e ideias em desenvolvimento. Foram utilizadas as linguagens Python e JavaScript (Vanilla) para criar lógicas personalizadas dentro dos fluxos.


# 🚀 Introdução

Este repositório é uma coleção de automações desenvolvidas no **n8n**, com foco em resolver problemas reais através da integração de sistemas e otimização de tarefas repetitivas.

Cada workflow foi projetado para substituir processos manuais por fluxos automatizados, utilizando uma combinação de **Python** e **JavaScript (Node Vanilla)** para lógica e manipulação de dados.

As automações se conectam a serviços como **Google Sheets**, **Gmail**, **Discord**, **CRMs**, **bancos de dados** e **APIs REST**, demonstrando a versatilidade do n8n como plataforma de integração.

O propósito deste repositório é mostrar como a automação inteligente pode **economizar tempo**, **reduzir erros humanos** e **aumentar a eficiência operacional** — seja em contextos administrativos, técnicos ou de negócios.

Todas as automações são documentadas individualmente, com explicação do problema original, fluxo criado, tecnologias utilizadas e instruções para importação e personalização no seu próprio ambiente n8n.

---

## ⚙️ Tecnologias utilizadas

- **n8n** – plataforma de automação e integração visual  
- **Python** – processamento e manipulação de dados dentro dos fluxos  
- **JavaScript (Node Vanilla)** – lógica personalizada e controle condicional  
- **APIs REST** – integração com serviços externos  
- **Google Sheets / Gmail / Discord / CRM** – exemplos de conectores utilizados  

---

## 💾 Como importar um workflow no n8n

Você pode reproduzir qualquer automação deste repositório no seu próprio ambiente.

### Passos:

1. Baixe o arquivo `.json` do workflow desejado (exemplo: `preenchimento-planilhas.json`).
2. Abra o **n8n** (versão local ou em nuvem).
3. Clique em **Import from file** (ou “Importar de arquivo”).
4. Selecione o arquivo baixado.
5. Configure suas credenciais dos serviços necessários, como:
   - Google Sheets  
   - Gmail (ou outro serviço de e-mail)
6. Clique em **Activate Workflow** para habilitar a automação.

> 🔒 **Importante:**  
> Os arquivos `.json` não contêm suas credenciais pessoais — apenas a estrutura do fluxo.  
> Ao importar, o n8n solicitará que você conecte suas próprias contas.

## 📁 Estrutura do repositório

```text
estrutura-do-repositorio/
├── n8n-workflows/
│   ├── preenchimento-planilhas/
│   │   ├── README.md
│   │   └── preenchimento-planilhas.json
│   ├── notificacao-discord/
│   │   ├── README.md
│   │   └── notificacao-discord.json
│   └── sincronizacao-crm/
│       ├── README.md
│       └── sincronizacao-crm.json
│
└── README.md (este arquivo principal)
```
📝 Observação: > Os nomes dos projetos acima são apenas exemplos, visto que o repositório está em constante evolução.

💡 Contribuições
> Este projeto está em constante evolução. Sugestões, ideias de novas automações ou melhorias são sempre bem-vindas.



