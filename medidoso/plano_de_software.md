# 📒 PLANO DE SOFTWARE

O **Plano de Software** (PS) tem como propósito organizar e orientar o desenvolvimento do projeto, definindo visão, objetivos, escopo, equipe, cronograma e processos a serem seguidos. Ele funciona como guia de referência para garantir alinhamento entre os membros da equipe, rastreabilidade das atividades e evolução estruturada do software ao longo de seu ciclo de vida.

## 📋 IDENTIFICAÇÃO DO PROJETO

- **Nome do projeto:** Medidoso
- **Equipe:**
  - Gustavo G. Zanella (_Líder_)
  - Gustavo dos Santos Alves
  - Guilherme Garghetti
  - Richardy Zaparolli
  - Diogo Felipe Alves

* **Repositório Git:** (https://github.com/Richardy001/New-Medidoso)
* **Data de início:** 18 de agosto de 2025
* **Previsão de término:** 08 de dezembro de 2025
* **Versão do PS:** v2025.08.18

---

## ⭐ INTRODUÇÃO

### Contexto

O crescimento da população idosa no Brasil e no mundo tem trazido novos desafios relacionados à saúde e à qualidade de vida. Entre esses desafios, destaca-se o uso contínuo de medicamentos, que muitas vezes precisa seguir horários rígidos e combinações específicas. Muitos idosos acabam esquecendo doses ou tomando remédios em horários incorretos, o que pode causar riscos sérios à saúde.
O projeto Medidoso surge nesse cenário, como uma ferramenta digital que permite que um responsável/cuidador gerencie agendas de medicamentos, enquanto o idoso tem uma interface simplificada e acessível para acompanhar seus remédios diários.

### Problema

O problema identificado é a dificuldade que idosos encontram em organizar e seguir corretamente seus tratamentos medicamentosos. Esquecimentos, confusões entre horários e dosagens, além da ausência de um sistema centralizado para controle, geram riscos à saúde, reincidência de internações e dependência excessiva de terceiros.
Além disso, cuidadores e familiares enfrentam falta de ferramentas práticas para monitorar e gerenciar os remédios, precisando recorrer a anotações em papel ou aplicativos genéricos que não atendem às necessidades desse público.

### Objetivos

#### Objetivo geral

Desenvolver um sistema web acessível que permita o gerenciamento centralizado de agendas de medicamentos por parte do responsável/cuidador e que forneça ao idoso uma interface clara e intuitiva para acompanhar quais remédios devem ser tomados, em que horários e em quais dias da semana.

#### Objetivos específicos

Criar um painel de controle para que o responsável possa cadastrar, editar e excluir medicamentos nas agendas.
Disponibilizar ao idoso uma visualização simples e adaptada (com letras maiores, contraste adequado e navegação facilitada).
Implementar um sistema de lembretes/notificações para ajudar no cumprimento dos horários.
Garantir que o sistema seja seguro e confiável, protegendo os dados dos usuários com autenticação.
Fornecer relatórios básicos de uso, permitindo que o cuidador acompanhe a adesão ao tratamento.

### Público-alvo

O público-alvo principal são idosos que fazem uso contínuo de medicamentos e seus responsáveis/cuidador(es).

Idosos: serão diretamente beneficiados ao terem uma ferramenta de fácil acesso para se orientar sobre seus remédios diários, aumentando a autonomia, segurança e confiança no tratamento.
Responsáveis/cuidadores: terão maior controle e organização, podendo cadastrar e monitorar facilmente as agendas, reduzindo a chance de erros e esquecimentos.

---

## 🏗️ ESCOPO

<h6 style="color: red;">AULA 04</h6>

**📌 O detalhamento completo dos requisitos pode ser encontrado no [Documento de Requisitos (DR)](https://www.example.com/).**

### Resumo

O Medidoso é um sistema digital voltado para auxiliar idosos no acompanhamento de seus medicamentos diários. Ele permite que um responsável organize e gerencie uma agenda de remédios, enquanto o idoso acessa uma interface simples para visualizar quais medicamentos tomar, em quais horários e em quais dias da semana. Dessa forma, o sistema busca aumentar a segurança, a autonomia e a qualidade de vida dos idosos, além de facilitar o trabalho dos cuidadores.

### Principais funcionalidades

Cadastro, edição e exclusão de medicamentos por parte do responsável.
Organização de medicamentos em uma agenda por horários e dias da semana.
Visualização simplificada da rotina de medicamentos pelo idoso.
Painel de controle para o responsável monitorar os remédios cadastrados.
Interface acessível com letras grandes, cores contrastantes e usabilidade adequada para idosos.
Registro de horários de uso e histórico básico de medicamentos.
Possibilidade de múltiplos medicamentos organizados em uma mesma agenda.

### Restrições / Limitações

O sistema está parcialmente já desenvolvido, serão feitas melhorias específicas para melhor funcionamento/comportamento.
O projeto terá infraestrutura simplificada, utilizando recursos gratuitos ou de baixo custo (ex.: hospedagem em nuvem gratuita, banco de dados).
O foco inicial será em versão web, sem entrega de aplicativo mobile nativo nesta etapa.
Recursos como notificações automáticas (push/SMS) e relatórios detalhados podem ser apenas prototipados, sem implementação completa.

### Fora do escopo

Integração com farmácias ou sistemas de saúde.
Controle de estoque de medicamentos (quantidade disponível).
Lembretes por SMS/push notificação em versão final (somente previsto como futura evolução).
Recursos de telemedicina ou comunicação direta com médicos.
Integração com dispositivos de IoT (caixas de remédio inteligentes, smartwatches).

---

## 🤝 ORGANIZAÇÃO E PAPÉIS

### Papéis da equipe de desenvolvimento

#### Papel (ex.: Desenvolvedor)

- **Desempenhado por:** Gustavo G. Zanella (Gerente)
- **Principais atribuições:**
  - Coordenar o andamento do projeto e garantir cumprimento do cronograma.
  - Distribuir tarefas conforme prioridades.
  - Acompanhar as entregas parciais e finais.

- **Desempenhado por:** Gustavo dos Santos Alves (Backend)
- **Principais atribuições:**
  - Implementar autenticação e autorização (JWT).
  - Estruturar o banco de dados.
  - Garantir a segurança e integridade dos dados.

- **Desempenhado por:** Guilherme Garghetti (frontend)
- **Principais atribuições:**
  - Criar o layout responsivo e acessível do sistema.
  - Implementar telas do idoso e do responsável.
  - Integrar o frontend com a API.
  - Garantir acessibilidade e usabilidade da interface.

- **Desempenhado por:** Richardy Zaparolli (Testes)
- **Principais atribuições:**
  - Elaborar e executar casos de teste funcionais.
  - Identificar e reportar falhas ou inconsistências.
  - Validar usabilidade junto ao público-alvo (idosos).
  - Apoiar na documentação técnica e evidências.

- **Desempenhado por:** Diogo Felipe Alves
- **Principais atribuições:**
  - Criar protótipos e fluxos de navegação.
  - Realizar pesquisas rápidas de acessibilidade.
  - Apoiar na documentação de requisitos e atas de reunião.
  - Centralizar feedbacks e propor melhorias.

### Estrutura de trabalho

#### Divisões

A equipe foi organizada em dois subgrupos principais:
  - Desenvolvimento (Backend + Frontend): responsável pela implementação técnica do sistema.
  - Suporte (Gerência, QA/Testes e UX/Documentação): responsável por planejamento, qualidade, documentação e validação.
  - Cada integrante atua em sua especialidade, mas todos podem apoiar em testes e documentação.

#### Comunicação interna

##### Canais utilizados para comunicação:
  - Discord: reuniões semanais de planejamento e acompanhamento.
  - WhatsApp: alinhamentos rápidos e decisões emergenciais.
  - GitHub: versionamento de código, issues, e acompanhamento técnico.
  - Google Drive: repositório de atas, relatórios e documentos complementares.

##### Reuniões e periodicidade
  - Reunião de planejamento: toda segunda-feira às 19h, via Discord, com objetivo de definir as tarefas da semana.
  - Reunião de acompanhamento: toda quinta-feira às 19h, via Discord, para verificar progresso e identificar bloqueios.
  - Checkpoints pontuais: conversas rápidas via WhatsApp, quando houver necessidade de ajustes imediatos.

#### Distribuição de tarefas
  - As tarefas são registradas e priorizadas no GitHub Projects. Cada atividade é atribuída a um membro de acordo com o papel definido no RACI:
    - Backend (Gustavo Santos Alves), Frontend (Guilherme Garghetti), QA (Richardy Zaparolli), UX (Diogo), Gerência (Gustavo Zanella).
    - O Gerente revisa a priorização semanalmente.

#### Documentação e rastreabilidade
  - Todos os documentos ficam armazenados no Google Drive.
  - Cada reunião gera uma ata com decisões registradas.
  - As issues no GitHub são usadas para rastrear desenvolvimento técnico e bugs.

#### Integração de feedbacks
  - Os feedbacks recebidos em sala de aula são documentados no Google Drive e imediatamente avaliados na reunião de quinta-feira. Caso aprovados, viram issues no GitHub e entram no backlog do projeto.

#### Coordenação de entregas parciais
  - O Gerente do Projeto (Gustavo G. Zanella) é responsável por acompanhar prazos e garantir que as entregas parciais sejam concluídas conforme cronograma.
    - Ele monitora atividades no GitHub.
    - Confere semanalmente os marcos definidos no cronograma.
    - Alinha ajustes com a equipe em caso de atrasos ou mudanças.

---

## 💻 PROCESSO DE DESENVOLVIMENTO

### Processo ágil

<h6 style="color: red;">AULA 08</h6>

Descrever qual é/será o processo ágil implementado e de que maneira ele é/será implementado.

### Definição de pronto (DoD)
  - Um requisito, tarefa ou funcionalidade será considerado “Pronto” quando:
    - Código desenvolvido e testado localmente sem erros.
    - Revisão de código realizada por pelo menos 1 membro da equipe.
    - Funcionalidade integrada ao repositório principal sem conflitos.
    - Casos de teste executados com sucesso (mínimo 80% de cobertura).
    - Documentação ou comentário de uso atualizado no repositório.
    - Validado pelo responsável de QA (Richardy Zaparolli).

---

## 🗓️ CRONOGRAMA
  - O cronograma do projeto foi elaborado no formato de Gráfico de Gantt (já gerado anteriormente), com base no EAP e nas estimativas de duração.
    - Ferramenta utilizada: Python + Matplotlib (imagem de Gantt anexada ao relatório). 
    - Organização: Atividades sequenciadas por fases (Iniciação → Requisitos → Design → Backend → Frontend → Testes → Relatórios → Entrega).
    - Regras de acompanhamento: revisado semanalmente nas reuniões de quinta-feira.

---

## ⚙️ GESTÃO DE CONFIGURAÇÃO

### Estratégia de branches
  - Main (produção) → branch estável, somente código final aprovado.
  - Develop (integração) → branch principal de integração contínua.
  - **Feature/nome → cada funcionalidade desenvolvida em branch própria.
  - **Hotfix/nome → correções críticas em produção.
  - Regras:
    - Commits só podem ser feitos em feature branches.
    - Integração em develop via pull request com aprovação do gerente e ao menos 1 reviewer.
    - Após testes, merge de develop em main.

### Política de commits
  - Padrão de mensagem: tipo: descrição curta
    - feat: nova funcionalidade
    - fix: correção de bug
    - docs: alteração de documentação
    - test: criação ou ajuste de testes
  - Frequência esperada: commits diários por tarefa ativa.
  - Rastreabilidade: cada commit deve estar vinculado a uma issue no GitHub.

### Gestão de mudanças
  - Alterações de requisitos registradas em atas no Google Drive e vinculadas ao Kanban no GitHub Projects.
  - Mudanças devem ser aprovadas pelo Gerente do Projeto.
  - Ajustes de prioridade são discutidos nas reuniões semanais.
  - Se houver impacto significativo no cronograma, a mudança gera revisão do Gantt.

---

## ☑️ GARANTIA DA QUALIDADE

<h6 style="color: red;">AULA 05</h6>

O detalhamento completo de como será realizada a gestão de qualidade do projeto pode ser encontrado no [Plano de Garantia de Qualidade de Software (PGQS)](https://www.example.com/).

---

## 📐 ARQUITETURA

<h6 style="color: red;">AULA 07</h6>

O detalhamento completo da arquitetura do projeto pode ser encontrado no [Documento de Arquitetura de Software (DAS)](https://www.example.com/).

---

## ☠️ RISCOS E MITIGAÇÕES

Listar riscos reais ou potenciais e ações práticas que serão aplicadas para mitigá-los.

| Risco                                               | Probabilidade                 | Impacto                        | Ação de mitigação            |
| --------------------------------------------------- | ----------------------------  | -----------------------------  | ---------------------------- |
| Risco                                               | 🟥Alta / 🟨 Média / 🟩 Baixa | 🟥 Alto / 🟨 Médio / 🟩 Baixo | Ação                                                                                           |
| Atraso na implementação de funcionalidades críticas | 🟨 Média                      | 🟥 Alto                       | Redistribuir tarefas; focar no MVP antes de melhorias extras.                                  |
| Bugs críticos não detectados                        | 🟨 Média                      | 🟥 Alto                       | Revisões de código regulares + testes automatizados básicos.                                   |
| Problemas de integração entre backend e frontend    | 🟨 Média                      | 🟨 Médio                      | Revisões de código regulares                                                                   |
| Falhas de usabilidade para idosos                   | 🟥 Alta                       | 🟥 Alto                       | Testes de usabilidade com idosos antes da entrega final; ajustes rápidos baseados em feedback. |
| Indisponibilidade de algum membro da equipe         | 🟨 Média                      | 🟨 Médio                      | Garantir backup de responsáveis em tarefas críticas; documentação atualizada para transição. |
| Problemas de comunicação entre membros              | 🟩 Baixa                      | 🟨 Médio                      | Reuniões semanais fixas + alinhamentos rápidos via WhatsApp. |
| Perda de arquivos ou falhas em repositórios         | 🟩 Baixa                      | 🟨 Médio                      | Uso de GitHub (versionamento) e Google Drive (backup de docs). |

---

## 🗂️ RECURSOS

### Hardware/ambiente
  - Computadores pessoais dos integrantes da equipe.
  - Acesso à internet estável para reuniões e desenvolvimento remoto.
  - Ambiente de desenvolvimento configurado localmente (Node.js, SQLite, Angular).
  - Hospedagem em ambiente gratuito (Heroku ou Railway) para deploy acadêmico.

### Softwares/ferramentas
  - IDE: Visual Studio Code.
  - Controle de versão: Git + GitHub.
  - Gerenciamento de tarefas: GitHub Projects (Kanban).
  - Prototipagem e design: Figma (versão gratuita).
  - Banco de dados: SQLite.
  - Backend: Node.js com Express.
  - Frontend: Angular (versão atual LTS).
  - Comunicação: Discord (reuniões), WhatsApp (alinhamentos rápidos), Google Drive (documentação).

---
