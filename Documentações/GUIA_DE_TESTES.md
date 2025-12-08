# 🧪 GUIA DE TESTES - PROJETO MEDIDOSO

## 1. Introdução

**Projeto:** MEDIDOSO  
**Equipe:** 4 membros (Gustavo Zanella, Gustavo Alves, Guilherme Garghetti, Richardy Zaparolli)  
**Nota:** Diogo Felipe Alves saiu durante desenvolvimento; funções assumidas por Guilherme

Este documento descreve o plano de testes, os casos de teste e os procedimentos para validar a funcionalidade, usabilidade, confiabilidade e segurança do sistema MEDIDOSO. Os testes abrangem cenários de autenticação, gerenciamento de medicamentos, diferenciação de perfis (cuidador/idoso) e modo acessível.

**Objetivo:** Garantir que o sistema funcione conforme especificado, sem erros críticos, e seja seguro e acessível para idosos e cuidadores.

---

## 2. Escopo de Testes

### 2.1 Funcionalidades Cobertas

✅ **Autenticação e Cadastro**
- Login com email/senha
- Login com Google
- Cadastro de novo usuário
- Recuperação de senha
- Logout

✅ **Gerenciamento de Medicamentos**
- Adicionar medicamento
- Editar medicamento
- Remover medicamento
- Visualizar medicamentos na agenda
- Ordenar medicamentos por horário

✅ **Diferenciação de Perfis**
- Funcionalidades disponíveis para cuidador
- Funcionalidades disponíveis para idoso
- Restrições de acesso adequadas

✅ **Modo Idoso (Acessibilidade)**
- Ativar/desativar modo idoso
- Interface com fontes ampliadas
- Contraste adequado
- Navegação simplificada
- Botões maiores

✅ **Geração de Relatórios**
- Gerar PDF com agenda semanal
- Incluir nome do paciente
- Incluir data/hora de geração
- Download funcional

✅ **Dashboard do Cuidador**
- Visualizar lista de pacientes
- Gerenciar pacientes conectados
- Visualizar agendas de cada paciente

✅ **Segurança**
- Autenticação obrigatória
- Isolamento de dados por usuário
- Proteção contra acesso não autorizado

---

## 3. Tipos de Teste

### 3.1 Testes Funcionais
Validam se as funcionalidades operam conforme especificado.

### 3.2 Testes de Usabilidade
Validam se a interface é intuitiva e acessível.

### 3.3 Testes de Confiabilidade
Validam se o sistema mantém integridade de dados e recuperação de erros.

### 3.4 Testes de Segurança
Validam se os dados são protegidos e o acesso é restrito.

### 3.5 Testes de Performance
Validam se o sistema responde em tempo aceitável.

---

## 4. Ambiente de Teste

**Navegadores:** Chrome, Edge (versões recentes)

**Dispositivos:** Desktop

**Conexão:** Conexão de internet estável

**Conta de Teste:**
- Cuidador: `cuidador@teste.com` / senha: `teste123`
- Idoso: `idoso@teste.com` / senha: `teste123`

**Banco de Dados:** Firebase (ambiente de desenvolvimento)

---

## 5. Casos de Teste

### 🔐 **MÓDULO 1: AUTENTICAÇÃO E CADASTRO**

#### TC-001: Login com Email/Senha (Sucesso)
**Pré-condição:** Usuário já possui conta cadastrada

| Campo | Valor |
|-------|-------|
| Email | cuidador@teste.com |
| Senha | teste123 |

**Passos:**
1. Acessar página index.html
2. Clicar em "Entrar"
3. Inserir email e senha
4. Clicar em "Fazer Login"

**Resultado esperado:** 
- ✅ Login realizado com sucesso
- ✅ Redirecionado para dashboard-cuidador.html
- ✅ Nome do usuário exibido na interface

**Status:** ✅ PASSOU
**Data de execução:** [08/12/2025]
**Executado por:** [Richardy Zaparolli]

---

#### TC-002: Login com Dados Inválidos
**Pré-condição:** Nenhuma

| Campo | Valor |
|-------|-------|
| Email | teste@invalido.com |
| Senha | senhaErrada |

**Passos:**
1. Acessar página index.html
2. Inserir email inválido
3. Inserir senha incorreta
4. Clicar em "Fazer Login"

**Resultado esperado:**
- ✅ Mensagem de erro exibida
- ✅ Usuário permanece na página de login
- ✅ Sem redirecionamento

**Status:** ✅ PASSOU

---

#### TC-003: Cadastro de Novo Usuário
**Pré-condição:** Nenhuma

| Campo | Valor |
|-------|-------|
| Nome | João Silva |
| Email | joao.silva@teste.com |
| Tipo de Usuário | Idoso |
| Idade | 72 |
| Telefone | (49) 99999-9999 |
| Senha | senha123 |

**Passos:**
1. Acessar página cadastro.html
2. Preencher todos os campos obrigatórios
3. Clicar em "Cadastrar"

**Resultado esperado:**
- ✅ Cadastro realizado com sucesso
- ✅ Mensagem de confirmação exibida
- ✅ Redirecionado para login ou dashboard
- ✅ Dados salvos no Firebase

**Status:** ✅ PASSOU

---

#### TC-004: Logout
**Pré-condição:** Usuário autenticado

**Passos:**
1. Clicar no menu lateral
2. Selecionar "Sair"

**Resultado esperado:**
- ✅ Sessão encerrada
- ✅ Redirecionado para página de login

**Status:** ✅ PASSOU

---

### 💊 **MÓDULO 2: GERENCIAMENTO DE MEDICAMENTOS**

#### TC-005: Adicionar Medicamento (Cuidador)
**Pré-condição:** Cuidador autenticado, agenda aberta

| Campo | Valor |
|-------|-------|
| Nome do Medicamento | Dipirona |
| Horário | 08:00 |
| Dia da Semana | Segunda |
| Observações | 1 Comprimido |
| Imagem | [selecionar imagem] |

**Passos:**
1. Clicar em "+ Adicionar Medicamento"
2. Preencher formulário
3. Clicar em "Adicionar"

**Resultado esperado:**
- ✅ Medicamento adicionado à agenda
- ✅ Medicamento aparece no dia selecionado
- ✅ Dados salvos no Firebase
- ✅ Mensagem de sucesso exibida

**Status:** ✅ PASSOU

---

#### TC-006: Editar Medicamento (Cuidador)
**Pré-condição:** Cuidador autenticado, medicamento cadastrado

**Passos:**
1. Clicar no botão editar (ícone de lápis) no medicamento
2. Alterar horário para 09:00
3. Clicar em "Salvar Alterações"

**Resultado esperado:**
- ✅ Medicamento atualizado
- ✅ Horário novo refletido na agenda
- ✅ Dados atualizados no Firebase
- ✅ Medicamentos reordenados por horário

**Status:** ✅ PASSOU

---

#### TC-007: Remover Medicamento (Cuidador)
**Pré-condição:** Cuidador autenticado, medicamento cadastrado

**Passos:**
1. Clicar no botão remover (ícone de lixo) no medicamento
2. Confirmar exclusão
3. Clicar em "Sim, remover"

**Resultado esperado:**
- ✅ Medicamento removido da agenda
- ✅ Dados deletados do Firebase
- ✅ Mensagem de confirmação exibida
- ✅ Interface atualizada imediatamente

**Status:** ✅ PASSOU

---

#### TC-008: Visualizar Medicamentos na Agenda (Idoso)
**Pré-condição:** Idoso autenticado

**Passos:**
1. Acessar página agenda-semanal.html
2. Observar medicamentos listados por dia

**Resultado esperado:**
- ✅ Medicamentos exibidos com horário
- ✅ Medicamentos ordenados por horário crescente
- ✅ Observações visíveis
- ✅ Imagem do medicamento exibida (se disponível)

**Status:** ✅ PASSOU

---

#### TC-009: Tentar Remover Medicamento em Modo Idoso
**Pré-condição:** Idoso autenticado, medicamentos cadastrados

**Passos:**
1. Entrar em modo idoso
2. Tentar clicar em botão de remover

**Resultado esperado:**
- ✅ Botão de remover não aparece ou está desabilitado
- ✅ Idoso não consegue deletar medicamentos
- ✅ Mensagem informativa exibida no topo da tela

**Status:** ✅ PASSOU

---

### 👥 **MÓDULO 3: DIFERENCIAÇÃO DE PERFIS**

#### TC-010: Cuidador Visualizar Dashboard
**Pré-condição:** Cuidador autenticado

**Passos:**
1. Fazer login como cuidador
2. Acessar dashboard-cuidador.html

**Resultado esperado:**
- ✅ Dashboard carregado
- ✅ Lista de pacientes/idosos visível
- ✅ Opção para gerenciar pacientes
- ✅ Botão "Adicionar Medicamento" disponível
- ✅ Menu com "Dashboard" visível

**Status:** ✅ PASSOU

---

#### TC-011: Idoso Visualizar Apenas Sua Agenda
**Pré-condição:** Idoso autenticado

**Passos:**
1. Fazer login como idoso
2. Acessar agenda-semanal.html

**Resultado esperado:**
- ✅ Agenda do idoso carregada
- ✅ Apenas seus medicamentos exibidos
- ✅ Botão "Adicionar" não disponível
- ✅ Menu "Dashboard" não aparece
- ✅ Sem acesso a dados de outros pacientes

**Status:** ✅ PASSOU

---

#### TC-012: Restrição de Acesso - Idoso Não Acessa Dashboard Cuidador
**Pré-condição:** Idoso autenticado

**Passos:**
1. Tentar acessar dashboard-cuidador.html diretamente via URL
2. Verificar redirecionamento

**Resultado esperado:**
- ✅ Idoso redirecionado à agenda-semanal.html
- ✅ Dados de outros pacientes não são exibidos

**Status:** ✅ PASSOU

---

### 👓 **MÓDULO 4: MODO IDOSO (ACESSIBILIDADE)**

#### TC-013: Ativar Modo Idoso
**Pré-condição:** Idoso autenticado, agenda aberta

**Passos:**
1. Clicar em "Modo Idoso" (botão verde)
2. Observar mudanças visuais

**Resultado esperado:**
- ✅ Fontes aumentadas (mínimo 22px)
- ✅ Contraste alto (WCAG AA)
- ✅ Botões maiores (50px altura mínima)
- ✅ Cores otimizadas
- ✅ Layout simplificado
- ✅ Botão agora diz "Modo Normal"

**Status:** ✅ PASSOU

---

### 📄 **MÓDULO 5: GERAÇÃO DE RELATÓRIOS (PDF)**

#### TC-016: Gerar PDF da Agenda
**Pré-condição:** Idoso/Cuidador autenticado, medicamentos cadastrados

**Passos:**
1. Clicar em "Baixar Agenda" (ícone de download)
2. Aguardar geração do PDF
3. Arquivo deve baixar automaticamente

**Resultado esperado:**
- ✅ PDF gerado sem erros
- ✅ Nome do arquivo: `[nome]_[data]_[hora].pdf`
- ✅ PDF contém:
  - Nome do paciente
  - Data e hora de geração
  - Medicamentos organizados por dia
  - Horários corretos
- ✅ Arquivo baixa corretamente
- ✅ PDF abrir/salvar normalmente

**Status:** ✅ PASSOU

---

#### TC-017: PDF com Medicamentos Vazios
**Pré-condição:** Sem medicamentos cadastrados

**Passos:**
1. Clicar em "Baixar Agenda"
2. Verificar PDF gerado

**Resultado esperado:**
- ✅ PDF gerado sem erros
- ✅ Mensagem "Nenhum medicamento" ou dias vazios
- ✅ Sem crash da aplicação

**Status:** ✅ PASSOU

---

### 🔒 **MÓDULO 6: SEGURANÇA**

#### TC-018: Autenticação Obrigatória
**Pré-condição:** Nenhuma (sessão encerrada)

**Passos:**
1. Tentar acessar agenda-semanal.html sem estar logado
2. Verificar redirecionamento

**Resultado esperado:**
- ✅ Redirecionado para index.html (login)

**Status:** ✅ PASSOU

---


### ⚡ **MÓDULO 7: PERFORMANCE**

#### TC-021: Tempo de Carregamento da Página
**Pré-condição:** Conexão normal

**Passos:**
1. Acessar agenda-semanal.html
2. Medir tempo até página estar interativa

**Resultado esperado:**
- ✅ Carregamento < 3 segundos
- ✅ Sem lag ou travamentos

**Status:** ✅ PASSOU
**Tempo medido:** ~2.5s

---

#### TC-022: Desempenho com Muitos Medicamentos
**Pré-condição:** 20+ medicamentos cadastrados

**Passos:**
1. Acessar agenda com muitos medicamentos
2. Rolar página
3. Interagir (clique em botões)

**Resultado esperado:**
- ✅ Sem travamento
- ✅ Rolagem suave
- ✅ Botões responsivos

**Status:** ✅ PASSOU

---


### 📱 **MÓDULO 8: RESPONSIVIDADE**

#### TC-025: Desktop (1920x1080)
**Passos:**
1. Acessar em desktop
2. Verificar layout

**Resultado esperado:**
- ✅ Layout otimizado para desktop
- ✅ Elementos alinhados
- ✅ Sem overflow

**Status:** ✅ PASSOU

---

## 7. Relatório de Defeitos Encontrados

### Defeito 1: Botão de Remover Visível em Modo Idoso
**ID:** DEF-001
**Severidade:** 🔴 CRÍTICA
**Status:** ✅ RESOLVIDO
**Descrição:** Ao ativar modo idoso, o botão vermelho de remover medicamento ainda aparecia.
**Data encontrada:** 05/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Ajustado código para verificar `isCuidadorMode` antes de criar botão.

---

### Defeito 2: Menu Não Fecha ao Clicar no botão
**ID:** DEF-002
**Severidade:** 🟡 MÉDIA
**Status:** ✅ RESOLVIDO
**Descrição:** Menu lateral permanecia aberto após clicar no botao.
**Data encontrada:** 04/12/2025
**Data resolvida:** 04/12/2025
**Solução:** Adicionado evento para fechar menu após navegação.

---

### Defeito 3: PDF Gerado com Dados Incorretos
**ID:** DEF-003
**Severidade:** 🔴 CRÍTICA
**Status:** ✅ RESOLVIDO
**Descrição:** PDF não incluía todos os medicamentos cadastrados.
**Data encontrada:** 03/12/2025
**Data resolvida:** 04/12/2025
**Solução:** Refatoração da função `baixarAgenda()`.

---

### Defeito 4: Falta botão para excluir pacientes gerenciados
**ID:** DEF-004
**Severidade:** 🔴 CRÍTICA
**Status:** ✅ RESOLVIDO
**Descrição:** Cuidador não conseguia remover pacientes vinculados.
**Data encontrada:** 06/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Adicionado botão de exclusão na lista de pacientes gerenciados.

---

### Defeito 5: Imagem do medicamento não exibida na agenda
**ID:** DEF-005
**Severidade:** 🔴 CRÍTICA
**Status:** ✅ RESOLVIDO
**Descrição:** A imagem do remédio não aparecia no cartão da agenda.
**Data encontrada:** 05/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Corrigida renderização da imagem no componente da agenda.

---

### Defeito 6: Pacientes sem vínculo não apareciam para cuidador
**ID:** DEF-006
**Severidade:** 🔴 CRÍTICA
**Status:** ✅ RESOLVIDO
**Descrição:** Lista de pacientes disponíveis era prenchido manualmente causando multiplos erros.
**Data encontrada:** 05/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Ajustada consulta/listagem para incluir pacientes sem vínculo.

---

### Defeito 7: Função editar não aplicava alterações
**ID:** DEF-007
**Severidade:** 🔴 CRÍTICA
**Status:** ✅ RESOLVIDO
**Descrição:** Alterações de medicamento não eram substituidas.
**Data encontrada:** 05/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Corrigida lógica de update e reordenação após edição.

---

### Defeito 8: Código legado e duplicado causando inconsistência
**ID:** DEF-008
**Severidade:** 🟠 ALTA
**Status:** ✅ RESOLVIDO
**Descrição:** Partes antigas e funções repetidas impactavam o fluxo.
**Data encontrada:** 05/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Revisão, checagem e remoção de trechos não usados/duplicados.

---

### Defeito 9: Rolagem na tela do idoso inadequada
**ID:** DEF-009
**Severidade:** 🟠 ALTA
**Status:** ✅ RESOLVIDO
**Descrição:** Scroll da tela não funcionava bem na agenda do idoso quando tinha muitos medicamentos.
**Data encontrada:** 06/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Ajuste de estilo/layout para rolagem fluida.

---

### Defeito 10: Imagem do medicamento não abria em tamanho maior
**ID:** DEF-010
**Severidade:** 🟢 BAIXA
**Status:** ✅ RESOLVIDO
**Descrição:** Não era possível ampliar a imagem do remédio.
**Data encontrada:** 05/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Implementado clique para abrir imagem maior.

---

### Defeito 11: PDF sem dados de identificação
**ID:** DEF-011
**Severidade:** 🟠 ALTA
**Status:** ✅ RESOLVIDO
**Descrição:** PDF não exibia nome do idoso, data e hora.
**Data encontrada:** 04/12/2025
**Data resolvida:** 04/12/2025
**Solução:** Adicionadas informações de nome, data e hora ao gerar/baixar PDF.

---

### Defeito 12: Botão de edição ausente no painel do cuidador
**ID:** DEF-012
**Severidade:** 🟠 ALTA
**Status:** ✅ RESOLVIDO
**Descrição:** Cuidador não tinha botão para editar na agenda.
**Data encontrada:** 05/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Incluído botão de edição na tela do cuidador.

---

### Defeito 13: Botão “ver agenda do paciente” redundante
**ID:** DEF-013
**Severidade:** 🟢 BAIXA
**Status:** ✅ RESOLVIDO
**Descrição:** Botão redundante dentro do painel do cuidador.
**Data encontrada:** 05/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Removido botão, já que o cuidador vê a mesma agenda do idoso no modo de cuidador.

---

### Defeito 14: Mudança de senha não salvava
**ID:** DEF-014
**Severidade:** 🟠 ALTA
**Status:** ✅ RESOLVIDO
**Descrição:** Alteração de senha não persistia no backend.
**Data encontrada:** 06/12/2025
**Data resolvida:** 06/12/2025
**Solução:** Corrigido fluxo de atualização de senha e confirmação.

---

### Defeito 15: Novo usuário carregava dados de outro usuário
**ID:** DEF-015
**Severidade:** 🔴 CRÍTICA
**Status:** ✅ RESOLVIDO
**Descrição:** Em alguns cadastros, dados de outro usuário eram exibidos.
**Data encontrada:** 06/12/2025
**Data resolvida:** 07/12/2025
**Solução:** Ajustado isolamento de dados na criação e carregamento inicial.

---

### Defeito 16: Terminologia de perfil inconsistente
**ID:** DEF-016
**Severidade:** 🟢 BAIXA
**Status:** ✅ RESOLVIDO
**Descrição:** Campo de criação usava rótulo "usuário" em vez de "idoso".
**Data encontrada:** 05/12/2025
**Data resolvida:** 05/12/2025
**Solução:** Atualizado rótulo para "idoso" na criação de conta para facilitar entendimento.

---

### Defeito 17: Idade não coletada na tela correta
**ID:** DEF-017
**Severidade:** 🟢 BAIXA
**Status:** ✅ RESOLVIDO
**Descrição:** Idade do idoso não era solicitada na tela de cadastro específica.
**Data encontrada:** 05/12/2025
**Data resolvida:** 05/12/2025
**Solução:** Migração do campo de idade para o fluxo de cadastro do idoso.

---

## 8. Métricas de Teste

| Métrica | Valor |
|---------|-------|
| **Total de Casos de Teste** | 19 |
| **Testes Executados** | 19 |
| **Testes Aprovados** | 19 |
| **Testes Reprovados** | 0 |
| **Taxa de Sucesso** | 100% (no escopo testado) |
| **Defeitos Encontrados** | 17 |
| **Defeitos Resolvidos** | 17 |
| **Defeitos Abertos** | 0 |
| **Cobertura de Funcionalidades** | ~70% (foco desktop) |
| **Data de Execução** | 08/12/2025 |

---

## 9. Lacunas e Pendências de Teste

- 📱 **Mobile/Tablet não testados:** apenas desktop validado.
- 🌐 **Resiliência de rede não testada:** perda/reconexão de internet não verificada.
- 🔐 **Isolamento de dados e XSS não testados:** regras completas do Firestore e sanitização de entrada ainda precisam de validação.
- ⚙️ **Performance em hardware modesto não testada:** apenas ambiente desktop comum.

---

## 10. Conclusão

O sistema MEDIDOSO foi submetido a testes funcionais e de performance **no escopo desktop**. Os 19 casos executados passaram.

**Resultado:** ✅ **APROVADO NO ESCOPO TESTADO**

**Sumário:**
- ✅ Funcionalidades core (login, CRUD de medicamentos, dashboard) operando
- ✅ Interface desktop acessível e responsiva
- ✅ Geração de PDF funcionando
- ⚠️ Itens pendentes: mobile/tablet, resiliência de rede, isolamento de dados completo e XSS

**Recomendações:**
- Continuar monitorando em produção
- Implementar testes automatizados para regressão (No Futuro)
- Coletar feedback de usuários reais (idosos, Cuidadores)
- Planejar melhorias contínuas

---
## 11. Assinatura e Aprovação

| Papel | Nome | Data | Assinatura |,0
|-------|------|------|-----------|
| QA/Testes | Richardy Zaparolli | 08/12/2025 | ✅ |
| Líder de Projeto | Gustavo G. Zanella | 08/12/2025 | ✅ |

---

**Documento versão:** v1.0  
**Data:** 08/12/2025  
**Próxima revisão:** Conforme mudanças no sistema
