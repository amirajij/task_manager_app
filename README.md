# Task Manager App  
Projeto de Sistemas Móveis Empresariais

---

## Autoria

- **Nome:** Amir Ajij e Duarte Almeida  
- **Curso:** Informática de Gestão  
- **Unidade Curricular:** Sistemas Móveis Empresariais  
- **Ano Letivo:** 2024/2025  
- **Docente:** Prof. Rui Santos

---

## Objetivo do Projeto

Desenvolver uma aplicação móvel de produtividade em **Flutter** para gestão de tarefas diárias com integração em **Firebase Firestore** e atualização em tempo real.

A aplicação segue:
- Princípios de **arquitetura multi-camada**
- **Gestão de estado** (Provider)
- Operações **CRUD** completas
- **Boas práticas de UX/UI** com Material Design

---

## Funcionalidades Principais

| Funcionalidade             | Descrição                                                                                             |
|----------------------------|-------------------------------------------------------------------------------------------------------|
| Criar Tarefa               | Formulário validado: título, descrição, data limite, prioridade e categoria.                          |
| Editar Tarefa              | Atualização com pré-preenchimento de campos e gravação no Firestore.                                  |
| Eliminar Tarefa            | Remoção com diálogo de confirmação e feedback ao utilizador.                                          |
| Marcar Concluída           | Alternar entre concluída e pendente em tempo real.                                                   |
| Listagem em Tempo Real     | Tarefas atualizadas automaticamente via `StreamBuilder`.                                              |
| Filtros                    | Visualizar “Todas”, “Pendentes” ou “Concluídas”.                                                      |
| Integração com API Externa | Exibe estado do tempo atual através da **Open-Meteo API** (temperatura e vento).                      |
| UI/UX Consistente          | Tema Material 3 (Deep Purple), Snackbars, estados de carregamento e erro.                             |

---

## Estrutura da Aplicação

lib/
│
├── main.dart
├── models/
│ └── task_item.dart
├── providers/
│ └── task_provider.dart
├── services/
│ ├── firestore_service.dart
│ └── weather_service.dart
├── screens/
│ ├── list_screen.dart
│ ├── add_edit_screen.dart
│ └── detail_screen.dart
└── widgets/
├── task_card.dart
├── weather_widget.dart
├── empty_state.dart
├── error_dialog.dart
└── loading_spinner.dart


---

## Estrutura de Dados (Firestore)

**Coleção:** `tasks`

| Campo      | Tipo      | Descrição                          |
|------------|-----------|------------------------------------|
| title      | String    | Título da tarefa                   |
| description| String    | Descrição curta                    |
| dueDate    | Timestamp | Data limite                        |
| priority   | int       | Nível de prioridade (1-3)          |
| category   | String    | Categoria (ex: “Estudos”)          |
| isDone     | bool      | Estado (true/false)                |
| createdAt  | Timestamp | Data de criação                    |
| updatedAt  | Timestamp | Data da última atualização         |

---

## Integração com API Externa

- **API Utilizada:** [Open-Meteo](https://open-meteo.com/)
- **Endpoint:**  
  `https://api.open-meteo.com/v1/forecast?latitude=38.72&longitude=-9.13&current_weather=true`
- **Dados exibidos:**
  - Temperatura atual (°C)
  - Velocidade do vento (km/h)
  - Atualização manual via botão de refresh

**Justificação:**  
API gratuita, sem chave, ideal para fins educativos e demonstrações.

---

## Tecnologias e Bibliotecas

| Tecnologia        | Finalidade                        |
|-------------------|-----------------------------------|
| Flutter           | Framework mobile                   |
| Firebase Core     | Inicialização do Firebase          |
| Cloud Firestore   | Base de dados em tempo real        |
| Provider          | Gestão de estado global            |
| HTTP              | Requisições à API de meteorologia  |
| Material Design 3 | Interface moderna e responsiva     |

---

## Gestão de Estado

- **Provider:** Gestão centralizada das tarefas.
- **StreamBuilder:** Sincroniza UI com Firestore em tempo real.
- **setState:** Usado apenas para estados locais (formulários, efeitos visuais).

---

## Instalação e Execução

1. Clonar o projeto ou extrair o `.zip`.
2. Instalar dependências:
3. Configurar Firebase:
- Adicionar `google-services.json` na pasta `android/app/`
- Confirmar o plugin `com.google.gms.google-services` no `build.gradle`
4. Executar a aplicação:


---

## Testes Realizados

- Criação, edição e eliminação de tarefas.
- Atualização automática via Firestore (`StreamBuilder`).
- Validação de formulários e tratamento de erros.
- Exibição correta da meteorologia.
- Testes offline: comportamento controlado sem falhas.
- Filtros por estado e atualização visual imediata.

---

## Conclusão

O projeto demonstra o ciclo completo de desenvolvimento de uma aplicação Flutter integrada com Firebase e API externa. Aplicou-se arquitetura modular, cloud services, gestão de estado reativa e boas práticas de UI/UX.

Pronta para futuras evoluções: autenticação, notificações e dashboards.
