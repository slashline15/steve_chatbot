# steve_chatbot
Esse é um teste para a criação de um chatbot utilizando git para versionamento 

### @hoje
import datetime

print(datetime.date.today())

```mermaid
graph TD
    %% INÍCIO DO FLUXO
    A[Webhook - Início da Conversa] --> B[Query Usuário - Supabase: Query]

    %% CHECAGEM DO USUÁRIO
    B -- Usuário Existe --> D[Registrar Mensagem do Usuário - Supabase: Insert]
    B -- Usuário Não Existe --> C[Criar Usuário - Supabase: Insert]

    %% REGISTRAR MENSAGEM
    C --> D
    D --> E[Identificar Intenção - OpenAI GPT]

    %% IDENTIFICAÇÃO DA INTENÇÃO
    E --> F{Processar Intenção e Contexto}

    %% PROCESSAR INTENÇÃO E CONTEXTO
    F -- Atualizar Contexto ou Preferências --> G[Atualizar Contexto e Preferências - Supabase: Upsert]
    F -- Sem Ação Necessária --> H[Gerar Resposta - Function Node]

    %% GERAR RESPOSTA
    G --> H
    H --> I[Responder ao Usuário - Chatbot ou API de Mensagem]
    I --> J[Fim]

    %% TRATAMENTO DE ERROS
    B ----> K(Tratamento de Erros)
    C ----> K
    D ----> K
    E ----> K
    F ----> K
    G ----> K
    H ----> K
    I ----> K
    K --> J

    %% DESCRIÇÃO DAS RELAÇÕES ENTRE OS NÓS
    %% Nota: A estrutura explica o caminho e a condição de cada nó.
    subgraph Explicação_do_Fluxo
        A --> B
        B -->|Usuário Existente| D
        B -->|Usuário Novo| C
        C --> D
        D --> E
        E --> F
        F -->|Atualiza Contexto| G
        F -->|Não Atualiza| H
        G --> H
        H --> I
    end
```
