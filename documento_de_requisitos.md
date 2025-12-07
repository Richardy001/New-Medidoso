# 📑 Documento de Requisitos (DR)

**Projeto:** Medidoso  
**Equipe:** Gustavo G. Zanella, Gustavo dos Santos Alves, Guilherme Garghetti, Richardy Zaparolli

---

## 1. INTRODUÇÃO

### 1.1 Objetivo

Este documento tem como objetivo especificar os requisitos funcionais e não funcionais do sistema Medidoso, uma aplicação web para gerenciamento de medicamentos voltada para idosos e seus cuidadores. O documento serve como referência técnica para desenvolvimento, validação e testes do software.

### 1.2 Escopo resumido

O Medidoso é um sistema web que permite que cuidadores/responsáveis gerenciem agendas de medicamentos de idosos de forma centralizada, enquanto os idosos acessam uma interface simplificada e acessível para visualizar seus remédios diários organizados por horários e dias da semana. O sistema busca aumentar a segurança, autonomia e qualidade de vida dos idosos, reduzindo riscos associados ao esquecimento ou confusão no uso de medicamentos.

---

## 2. DESCRIÇÃO GERAL

### 2.1 Usuários do sistema

O sistema possui dois perfis principais de usuários:

- **Idosos**: Usuários finais que visualizam suas agendas de medicamentos em interface adaptada (letras grandes, cores contrastantes, navegação simplificada).
- **Cuidadores/Responsáveis**: Usuários que gerenciam as agendas de medicamentos dos idosos sob sua responsabilidade, realizando cadastro, edição e exclusão de medicamentos.

### 2.2 Funcionalidades gerais

- Autenticação segura de usuários (idosos e cuidadores)
- Cadastro, edição e exclusão de medicamentos por cuidadores
- Organização de medicamentos em agenda semanal por horários
- Visualização simplificada da rotina de medicamentos para idosos (Modo Idoso)
- Associação de imagens aos medicamentos para facilitar identificação
- Painel de controle para cuidadores monitorarem múltiplos idosos
- Histórico básico de medicamentos cadastrados
- Download/impressão da agenda semanal em PDF
- Interface responsiva adaptada para diferentes dispositivos

### 2.3 Restrições e premissas

**Restrições técnicas:**
- Sistema deve ser executado em navegadores web modernos (Chrome, Firefox, Edge, Safari)
- Utilização de Firebase para autenticação e armazenamento de dados (Firestore)
- Hospedagem em Firebase Hosting (ambiente gratuito)
- Desenvolvimento web-first (sem aplicativo mobile nativo nesta versão)

**Premissas de qualidade:**
- Sistema deve estar em compliance com a LGPD (proteção de dados pessoais)
- Interface acessível seguindo diretrizes de usabilidade para idosos
- Responsividade para acesso em desktop, tablet e smartphone

**Limitações:**
- Notificações push/SMS não implementadas na versão atual
- Sem integração com farmácias ou sistemas de saúde externos
- Sem controle de estoque de medicamentos
- Sem funcionalidades de telemedicina

---

## 3. REQUISITOS ESPECÍFICOS

### 3.1 Requisitos Funcionais (RF)

#### Autenticação e Controle de Acesso
- **RF01** – O sistema deve permitir o cadastro de novos usuários (idosos e cuidadores).
- **RF02** – O sistema deve autenticar usuários via email e senha utilizando Firebase Authentication.
- **RF03** – O sistema deve permitir que o usuário redefina sua senha em caso de esquecimento.
- **RF04** – O sistema deve permitir edição do perfil do usuário (nome, email, foto).
- **RF05** – O sistema deve diferenciar perfis de idoso e cuidador.

#### Gerenciamento de Medicamentos (Cuidador)
- **RF06** – O sistema deve permitir que o cuidador cadastre medicamentos com: nome, horário, dia(s) da semana, observações e imagem.
- **RF07** – O sistema deve permitir que o cuidador edite medicamentos já cadastrados.
- **RF08** – O sistema deve permitir que o cuidador exclua medicamentos da agenda.
- **RF09** – O sistema deve organizar medicamentos por horário dentro de cada dia da semana.
- **RF10** – O sistema deve permitir que o cuidador associe uma imagem ao medicamento.
- **RF11** – O sistema deve permitir cadastro do mesmo medicamento em múltiplos dias da semana.

#### Visualização de Medicamentos (Idoso)
- **RF12** – O sistema deve exibir a agenda semanal de medicamentos para o idoso.
- **RF13** – O sistema deve disponibilizar um "Modo Idoso" com interface adaptada (letras grandes, alto contraste).
- **RF14** – O sistema deve exibir medicamentos organizados por dia da semana e horário.
- **RF15** – O sistema deve exibir imagem, nome, horário e observações de cada medicamento.
- **RF16** – O idoso deve poder visualizar medicamentos em modo somente-leitura quando gerenciado por cuidador.

#### Gerenciamento de Múltiplos Idosos (Cuidador)
- **RF17** – O sistema deve permitir que um cuidador gerencie agendas de múltiplos idosos.
- **RF18** – O sistema deve exibir lista de idosos vinculados ao cuidador em dashboard específico.
- **RF19** – O sistema deve permitir que o cuidador selecione qual idoso deseja gerenciar.
- **RF20** – O sistema deve permitir vincular/desvincular idosos do perfil do cuidador.

#### Relatórios e Exportação
- **RF21** – O sistema deve permitir download da agenda semanal em formato PDF.
- **RF22** – O PDF gerado deve conter todos os medicamentos organizados por dia e horário.
- **RF23** – O sistema deve permitir visualização de histórico básico de medicamentos cadastrados.

#### Interface e Navegação
- **RF24** – O sistema deve ter menu lateral para navegação entre páginas (perfil, agenda, dashboard, sair).
- **RF25** – O sistema deve exibir nome do usuário logado na interface.
- **RF26** – O sistema deve permitir logout seguro do usuário.

### 3.2 Requisitos Não Funcionais (RNF)

#### Desempenho
- **RNF01** – O sistema deve carregar a agenda semanal em até 3 segundos.
- **RNF02** – O sistema deve responder a ações do usuário (cadastro, edição, exclusão) em até 2 segundos.
- **RNF03** – O sistema deve suportar acesso simultâneo de até 100 usuários sem degradação perceptível.

#### Usabilidade
- **RNF04** – A interface do Modo Idoso deve utilizar fontes com tamanho mínimo de 20px.
- **RNF05** – A interface deve ter contraste adequado para facilitar leitura (WCAG AA).
- **RNF06** – O sistema deve ser responsivo e adaptar-se a telas de 320px a 1920px de largura.
- **RNF07** – Botões e elementos interativos devem ter área mínima de toque de 44x44px (mobile).

#### Segurança
- **RNF08** – O sistema deve criptografar senhas dos usuários.
- **RNF09** – O sistema deve validar sessões de autenticação em todas as páginas protegidas.
- **RNF10** – O sistema deve estar em compliance com a LGPD para proteção de dados pessoais.
- **RNF11** – O sistema deve implementar proteção contra SQL Injection e XSS (uso de Firestore mitiga isso).

#### Confiabilidade
- **RNF12** – O sistema deve ter disponibilidade mínima de 95% ao mês.
- **RNF13** – O sistema deve realizar backup automático de dados no Firestore.
- **RNF14** – Em caso de falha, o sistema deve exibir mensagens de erro claras ao usuário.

#### Manutenibilidade
- **RNF15** – O código deve seguir padrões de nomenclatura e organização (comentários, funções modulares).
- **RNF16** – O sistema deve ter versionamento de código utilizando Git/GitHub.
- **RNF17** – Alterações críticas devem passar por revisão de código (code review).

#### Portabilidade
- **RNF18** – O sistema deve funcionar nos navegadores Chrome, Firefox, Edge e Safari (versões atuais).
- **RNF19** – O sistema deve ser acessível via URL pública (Firebase Hosting).

---

## 4. CASOS DE USO

### **UC01 – Cadastrar novo usuário**
- **Ator**: Idoso ou Cuidador
- **Pré-condição**: Nenhuma
- **Fluxo principal**:
  1. Usuário acessa página de cadastro
  2. Sistema exibe formulário com campos: nome, email, senha, tipo (idoso/cuidador)
  3. Usuário preenche dados e confirma
  4. Sistema valida dados e cria conta no Firebase Authentication
  5. Sistema cria documento de perfil no Firestore
  6. Sistema redireciona usuário para página de login

### **UC02 – Fazer login**
- **Ator**: Idoso ou Cuidador
- **Pré-condição**: Usuário possui conta cadastrada
- **Fluxo principal**:
  1. Usuário acessa página de login
  2. Sistema exibe formulário de email e senha
  3. Usuário preenche credenciais e confirma
  4. Sistema autentica via Firebase Authentication
  5. Sistema carrega dados do perfil do Firestore
  6. Sistema redireciona para agenda (idoso) ou dashboard (cuidador)

### **UC03 – Cadastrar medicamento**
- **Ator**: Cuidador
- **Pré-condição**: Cuidador autenticado e idoso selecionado
- **Fluxo principal**:
  1. Cuidador acessa agenda semanal
  2. Cuidador clica em um dia da semana
  3. Sistema abre modal de cadastro
  4. Cuidador preenche: nome, horário, observações, seleciona dia(s), adiciona imagem (opcional)
  5. Cuidador confirma cadastro
  6. Sistema valida dados e salva no Firestore
  7. Sistema atualiza agenda na tela

### **UC04 – Editar medicamento (Modo Idoso)**
- **Ator**: Cuidador
- **Pré-condição**: Cuidador autenticado, modo idoso ativado, medicamento já cadastrado
- **Fluxo principal**:
  1. Cuidador ativa Modo Idoso
  2. Cuidador clica sobre o medicamento na agenda
  3. Sistema abre modal de edição com dados preenchidos
  4. Cuidador altera informações desejadas
  5. Cuidador confirma alterações
  6. Sistema valida e atualiza dados no Firestore
  7. Sistema atualiza agenda na tela

### **UC05 – Excluir medicamento**
- **Ator**: Cuidador
- **Pré-condição**: Cuidador autenticado e medicamento cadastrado
- **Fluxo principal**:
  1. Cuidador acessa agenda
  2. Cuidador clica no botão "X" do medicamento
  3. Sistema exibe confirmação de exclusão
  4. Cuidador confirma exclusão
  5. Sistema remove medicamento do Firestore
  6. Sistema atualiza agenda na tela

### **UC06 – Visualizar agenda (Idoso)**
- **Ator**: Idoso
- **Pré-condição**: Idoso autenticado
- **Fluxo principal**:
  1. Idoso faz login
  2. Sistema carrega e exibe agenda semanal
  3. Sistema mostra medicamentos organizados por dia e horário
  4. Idoso visualiza nome, horário, observações e imagem de cada medicamento

### **UC07 – Gerenciar múltiplos idosos**
- **Ator**: Cuidador
- **Pré-condição**: Cuidador autenticado
- **Fluxo principal**:
  1. Cuidador acessa dashboard
  2. Sistema exibe lista de idosos vinculados
  3. Cuidador seleciona um idoso
  4. Sistema armazena seleção e redireciona para agenda do idoso
  5. Cuidador gerencia medicamentos do idoso selecionado

### **UC08 – Baixar agenda em PDF**
- **Ator**: Cuidador ou Idoso
- **Pré-condição**: Usuário autenticado
- **Fluxo principal**:
  1. Usuário clica em "Baixar Agenda"
  2. Sistema gera PDF com agenda semanal completa
  3. Sistema inicia download do arquivo PDF

### **UC09 – Ativar Modo Idoso**
- **Ator**: Cuidador
- **Pré-condição**: Cuidador autenticado
- **Fluxo principal**:
  1. Cuidador clica em botão "Modo Idoso"
  2. Sistema aumenta tamanho de fonte
  3. Sistema ajusta contraste e espaçamento
  4. Sistema habilita edição por clique em medicamentos
  5. Cuidador pode alternar de volta para modo normal

### **UC10 – Editar perfil**
- **Ator**: Idoso ou Cuidador
- **Pré-condição**: Usuário autenticado
- **Fluxo principal**:
  1. Usuário acessa página de perfil
  2. Sistema exibe dados atuais do usuário
  3. Usuário altera nome, email ou foto
  4. Usuário confirma alterações
  5. Sistema valida e atualiza dados no Firestore
  6. Sistema exibe confirmação de sucesso

---

## 5. RASTREABILIDADE

| ID Requisito | Caso de Uso |
|--------------|-------------|
| RF01 | UC01 – Cadastrar novo usuário |
| RF02, RF03 | UC02 – Fazer login |
| RF04 | UC10 – Editar perfil |
| RF05 | UC01, UC02 |
| RF06, RF09, RF10, RF11 | UC03 – Cadastrar medicamento |
| RF07 | UC04 – Editar medicamento |
| RF08 | UC05 – Excluir medicamento |
| RF12, RF14, RF15 | UC06 – Visualizar agenda (Idoso) |
| RF13 | UC09 – Ativar Modo Idoso |
| RF16 | UC06 – Visualizar agenda (Idoso) |
| RF17, RF18, RF19, RF20 | UC07 – Gerenciar múltiplos idosos |
| RF21, RF22 | UC08 – Baixar agenda em PDF |
| RF23 | - (funcionalidade de histórico) |
| RF24, RF25, RF26 | - (navegação geral do sistema) |
| RNF01, RNF02, RNF03 | Todos os casos de uso |
| RNF04, RNF05, RNF06, RNF07 | UC06, UC09 |
| RNF08, RNF09, RNF10, RNF11 | UC01, UC02, UC10 |
| RNF12, RNF13, RNF14 | Todos os casos de uso |
| RNF15, RNF16, RNF17 | - (processo de desenvolvimento) |
| RNF18, RNF19 | Todos os casos de uso |

---

## 6. GLOSSÁRIO

- **Firestore**: Banco de dados NoSQL em nuvem do Firebase
- **Firebase Authentication**: Serviço de autenticação do Firebase
- **Modo Idoso**: Interface adaptada com fontes grandes e alto contraste
- **LGPD**: Lei Geral de Proteção de Dados Pessoais
- **WCAG**: Web Content Accessibility Guidelines (diretrizes de acessibilidade)
- **Agenda Semanal**: Visualização de medicamentos organizados de segunda a domingo

---