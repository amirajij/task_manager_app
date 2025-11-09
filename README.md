# Task Manager App — Projeto de Sistemas Móveis Empresariais

## Autoria
**Nome:** Amir Ajij e Duarte Almeida
**Curso:** Informática de Gestão  
**Unidade Curricular:** Sistemas Móveis Empresariais  
**Ano Letivo:** 2024/2025  
**Docente:** Prof. Rui Santos

---

## Objetivo do Projeto
O objetivo deste projeto é desenvolver uma aplicação móvel de produtividade em **Flutter** que permita ao utilizador gerir tarefas diárias com integração em **Firebase Firestore** e atualização em tempo real.

A aplicação aplica princípios de **arquitetura multi-camada**, **gestão de estado com Provider**, **CRUD completo**, e **boas práticas de UX/UI** baseadas em Material Design.

---

## Funcionalidades Principais

| Funcionalidade | Descrição |
|----------------|------------|
| Criar Tarefa | Formulário validado com título, descrição, data limite, prioridade e categoria. |
| Editar Tarefa | Edição com pré-preenchimento dos campos e atualização no Firestore. |
| Eliminar Tarefa | Remoção com diálogo de confirmação e feedback ao utilizador. |
| Marcar Concluída | Alternar entre concluída e pendente em tempo real. |
| Listagem em Tempo Real | Tarefas atualizadas automaticamente através de `StreamBuilder`. |
| Filtros | Mostrar tarefas “Todas”, “Pendentes” ou “Concluídas”. |
| Integração com API Externa | Exibe o estado do tempo atual (temperatura e vento) via **Open-Meteo API**. |
| UI/UX Consistente | Tema Material 3 (Deep Purple), Snackbars e estados de carregamento/erro. |

---

## Estrutura da Aplicação

lib/
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

| Campo | Tipo | Descrição |
|--------|------|------------|
| title | String | Título da tarefa |
| description | String | Descrição curta |
| dueDate | Timestamp | Data limite |
| priority | int | Nível de prioridade (1-3) |
| category | String | Categoria (ex: “Estudos”) |
| isDone | bool | Estado (true/false) |
| createdAt | Timestamp | Data de criação |
| updatedAt | Timestamp | Data da última atualização |

---

## Integração com API Externa

**API Utilizada:** [Open-Meteo](https://open-meteo.com/)  
**Endpoint:**  
https://api.open-meteo.com/v1/forecast?latitude=38.72&longitude=-9.13&current_weather=true

**Dados exibidos:**
- Temperatura atual (°C)
- Velocidade do vento (km/h)
- Atualização manual através de botão de refresh

**Justificação:**  
API gratuita e sem necessidade de chave, ideal para fins educativos e demonstrações simples.

---

## Tecnologias e Bibliotecas

| Tecnologia | Finalidade |
|-------------|-------------|
| Flutter | Framework de desenvolvimento mobile |
| Firebase Core | Inicialização do Firebase |
| Cloud Firestore | Base de dados em tempo real |
| Provider | Gestão de estado global |
| HTTP | Requisições à API de meteorologia |
| Material Design 3 | Interface moderna e responsiva |

---

## Gestão de Estado

- `Provider` utilizado para gerir tarefas em toda a aplicação.
- `StreamBuilder` sincroniza a UI com o Firestore em tempo real.
- Estados locais (`setState`) apenas usados em formulários e pequenas interações visuais.

---

## Instalação e Execução

1. Clonar o projeto ou extrair o `.zip` submetido.
2. Instalar dependências:
   ```bash
   flutter pub get
Configurar Firebase:
Adicionar google-services.json em android/app/
Confirmar o plugin com.google.gms.google-services no build.gradle
Executar a aplicação:
flutter run
Testes Realizados
Criação, edição e eliminação de tarefas.
Atualização automática via Firestore (StreamBuilder).
Validação de formulários e mensagens de erro.
Exibição correta da meteorologia.
Testes offline (erro controlado e sem falhas).
Filtros por estado e atualização visual imediata.
Conclusão
O projeto Task Manager App demonstra o ciclo completo de desenvolvimento de uma aplicação Flutter integrada com Firebase e uma API externa.
Foram aplicados conceitos de arquitetura modular, integração de serviços cloud, estado reativo com Provider, e boas práticas de UI/UX.
A aplicação encontra-se funcional, estável e pronta para evolução futura, como autenticação de utilizadores, notificações ou dashboards de produtividade.

Referências
Flutter Documentation — https://flutter.dev
Firebase for Flutter — https://firebase.flutter.dev
Open-Meteo API — https://open-meteo.com
Provider Package — https://pub.dev/packages/provider