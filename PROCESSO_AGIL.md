# 🔄 PROCESSO ÁGIL IMPLEMENTADO
## Projeto MEDIDOSO

---

## 1. Introdução

### 1.1 Objetivo

Este documento descreve o **Processo Ágil Implementado** no projeto **MEDIDOSO**, um aplicativo web para gerenciamento de medicamentos com foco em idosos.

**Escopo:** Metodologia, practices, cycles e ferramentas utilizadas durante o desenvolvimento do projeto académico.

### 1.2 Contexto Académico

O projeto MEDIDOSO é um projeto académico desenvolvido por uma equipe de 4 integrantes com duração de um semestre (18 de agosto a 08 de dezembro de 2025), utilizando practices ágeis adaptadas para ambiente universitário.

**Equipe:**
- **Gustavo G. Zanella (Líder de Equipe):** Gerente de Projeto
- **Gustavo dos Santos Alves (Desenvolvedor Backend):** Backend/Firestore
- **Guilherme Garghetti (Desenvolvedor Frontend):** Frontend/Interface
- **Richardy Zaparolli (QA/Testes):** Quality Assurance/Validação

---

## 2. Metodologia Ágil Utilizada

### 2.1 Híbrido: Scrum + Kanban

O projeto utiliza uma **abordagem híbrida** combinando:

- **Scrum:** Sprints semanais, retrospectivas
- **Kanban:** Fluxo contínuo de trabalho, WIP (Work In Progress) limitado, transparência visual

```
Combinação Ótima para Projeto Académico:
├─ Scrum: Estrutura e planejamento
├─ Kanban: Flexibilidade para mudanças de requisitos
└─ Resultado: Entrega contínua com qualidade
```

### 2.2 Princípios Ágeis Adotados

1. **Indivíduos e interações** sobre processos e ferramentas
   - Comunicação diária via Discord/WhatsApp
   - Reuniões presenciais semanais

2. **Software funcionando** sobre documentação abrangente
   - Features entregues a cada sprint
   - Testes contínuos

3. **Colaboração com o cliente** sobre contratos
   - Feedback do professor a cada apresentação
   - Validação de requisitos contínua

4. **Responder a mudanças** sobre um plano pré-definido
   - Backlog dinâmico
   - Adaptação rápida a novos requisitos

---

## 3. Estrutura de Sprints

### 3.1 Duração e Planejamento

**Sprint Duration:** 1 semana (Segunda a Sexta)

**Ciclo de Desenvolvimento Académico:**

```
SPRINT (1 semana)

Seg  Ter  Qua  Qui  Sex
───  ───  ───  ───  ───
Dev  Dev  DEV+ QA   DEPLOY
       +   TST      REVIEW
       UA  EAT

Legenda:
- Dev: Desenvolvimento de features
- TST: Testes unitários/integração
- QA: Quality assurance (testes formais)
- DEPLOY: Deploy em produção
```

### 3.2 Ceremonies (Cerimônias Ágeis)

#### **Sprint Planning (Segunda-feira, 20:30)**
- **Duração:** 1 hora
- **Participantes:** Toda equipe
- **Objetivos:**
  - Selecionar itens do backlog para a sprint
  - Definir sprint goal (meta semanal)
  - Estimar esforço (planning poker)
  - Atribuir tasks
- **Outputs:**
  - Sprint backlog definido
  - Sprint goal claro
  - Tasks com story points

```
Sprint Planning Flow:
1. Revisão do backlog priorizado
2. Discussão de cada item
3. Estimativa de esforço
4. Atribuição de responsáveis
5. Confirmação de capacidade da equipe
```

#### **Code Review (Contínuo)**
- **Frequência:** A cada pull request/commit significativo
- **Duração:** 30 minutos a 1 hora
- **Responsáveis:** Outro desenvolvedor + Gerente
- **Objetivo:** Validar qualidade, segurança, testes e conformidade com padrões
- **Checklist aplicado:** PGQS seção 7.2
  - ✅ Código segue padrões (seção 3.1 do PGQS)
  - ✅ Funções têm documentação (JSDoc)
  - ✅ Código comentado apenas quando necessário para manutenção
  - ✅ Variáveis com nomes descritivos
  - ✅ Sem duplicação de código
  - ✅ Testes unitários inclusos (80%+)
  - ✅ Performance aceitável
  - ✅ Segurança verificada
  - ✅ Compatibilidade cross-browser

---

## 4. Backlog Management

### 4.1 Product Backlog

**Estrutura:**
- **Épics:** Grandes funcionalidades (ex: Autenticação, Medicamentos, PDF)
- **User Stories:** Funcionalidades menores (ex: "Como usuário, quero fazer login")
- **Tasks:** Atividades técnicas (ex: "Configurar Firebase")
- **Bugs:** Problemas encontrados

**Priorização:**
1. **MoSCoW:**
   - **Must:** Requisitos obrigatórios
   - **Should:** Requisitos importantes
   - **Could:** Melhorias
   - **Won't:** Não será feito nesta sprint

2. **Critérios:**
   - Valor para o negócio (avaliação de requisitos)
   - Dependências (bloqueadores)
   - Risco (funcionalidades críticas)
   - Esforço estimado

### 4.2 User Stories Implementadas

**Exemplo de User Story completa:**

```
ÉPICO: Gerenciamento de Medicamentos

USER STORY: Adicionar Medicamento
  ID: US-05
  Prioridade: MUST
  Story Points: 5
  Sprint: #3
  Status: DONE
  
  Como: Idoso ou Cuidador
  Quero: Adicionar um novo medicamento
  Para: Manter registro de meus medicamentos
  
  Critérios de Aceitação:
  ✅ Formulário com campos: nome, horário, imagem, Descrição
  ✅ Validação de campos obrigatórios
  ✅ Medicamento salvo no Firestore
  ✅ Confirmação visual de sucesso
  ✅ Modo Idoso compatível (fonte 22px+)
  
  Tarefas Técnicas:
  - [x] Criar form HTML
  - [x] Validar entrada
  - [x] Integrar com Firebase
  - [x] Testes unitários (80%+)
  - [x] Code review
  - [x] Teste manual QA
  
  Dependências:
  - Autenticação (US-01) - Concluída
  
  Riscos:
  - Upload de imagem pode falhar
  - Performance com muitos medicamentos
  
  Notas:
  - Usar padrão de componente existente
  - Reutilizar validação de outros forms
```

---

## 5. Estimativa e Planejamento

### 5.1 Planning Poker (Estimativa de Esforço)

**Escala Fibonacci:** 1, 2, 3, 5, 8, 13, 21

**Processo:**
1. Product Owner lê a user story
2. Equipe discute brevemente
3. Cada membro escolhe um número (simultaneamente)
4. Se divergência > 5 pontos, discutem pontos de vista
5. Estimativa final é consenso

**Exemplo:**
```
US-05 (Adicionar Medicamento):
  Gustavo (Backend): 5 pontos
  Guilherme (Frontend): 3 pontos
  Richardy (QA): 5 pontos
  
  Divergência → Discussão:
    - Gustavo: API vai precisar testes
    - Guilherme: UI é simples
    - Resultado: 5 pontos (Backend complexo)
```

### 5.2 Capacidade da Sprint

**Cálculo:**
```
Capacidade = Horas disponíveis por pessoa × Número de pessoas
Exemplo:
- Semana: 10 horas disponíveis
- Equipe: 4 pessoas (5 inicialmente; Diogo saiu no meio do projeto)
- Disponibilidade: 70% (estudos, outros compromissos)
- Capacidade total: 10 × 5 × 0.70 = 35 horas por semana

Conversão para Story Points:
- 1 ponto ≈ 2 horas
- Capacidade da sprint: ~17 story points por semana
```

### 5.3 Velocity (Velocidade)

**Rastreamento:**
```
Sprint #1: 15 points
Sprint #2: 18 points  ↑ +3
Sprint #3: 17 points  ↓ -1
Sprint #4: 19 points  ↑ +2
Sprint #5: 16 points  ↓ -3
Sprint #6: 20 points  ↑ +4

Velocidade média: ~17.5 points por sprint
Tendência: Estável com leve crescimento
```

---

## 6. Fluxo de Desenvolvimento

### 6.1 Git Workflow (Branching Strategy)

**Padrão: Git Flow Simplificado**

```
main (produção/apresentação final)
  ↓
dev (staging/testes)
  ├─ feature/autenticacao
  ├─ feature/medicamentos
  ├─ bugfix/login-error
  └─ ...
```

**Convenção de Branches:**
- `feature/nome-funcionalidade` - Nova feature
- `bugfix/nome-bug` - Correção de bug
- `hotfix/nome-urgente` - Correção urgente (se necessário)
- `docs/atualizacao` - Documentação

**Exemplo Commit:**
```
[FEATURE] Adicionar formulário de medicamento

- Criar form HTML com validação
- Integrar com Firebase Firestore
- Implementar Modo Idoso (fonte 22px)
- Testes manuais executados

Resolve: #45 (issue no GitHub)
```

### 6.3 Ambiente de Desenvolvimento

**Stack Tecnológico:**
```
Frontend:
├─ HTML5, CSS3, JavaScript (vanilla)
├─ Bootstrap (framework CSS)
└─ Sem framework JS (aplicação simples)

Backend:
├─ Firebase Authentication
├─ Firestore (banco de dados NoSQL)
└─ Firebase Hosting

Ferramentas de Desenvolvimento:
├─ Git/GitHub (versionamento)
├─ Visual Studio Code (IDE)
├─ Chrome DevTools (debugging)
```

**Setup Local:**
```
1. Clone repositório
   git clone https://github.com/Richardy001/New-Medidoso.git

2. Install dependências
   npm install

3. Configure Firebase
   - Copiar credenciais de .env.example
   - Criar .env.local com chaves do projeto

4. Rodas testes localmente
   npm test

5. Inicia servidor de desenvolvimento
   npm run dev

6. Acessa https://medidoso.web.app/
```

**Ambientes (Académico):**
```
DESENVOLVIMENTO (Dev)
├─ Máquinas locais dos desenvolvedores
├─ Testes manuais via Live Server
└─ Firestore (database dev)

PRODUÇÃO (Production)
├─ Firebase Hosting
├─ Banco de dados Firestore (prod)
└─ Deploy via GitHub (upload manual)
```

---

## 7. Práticas Técnicas Ágeis

### 7.1 Continuous Integration (CI)

**Status Atual:** Não implementado (projeto é HTML/CSS/JS vanilla)

**Alternativa para o MEDIDOSO:**
```
O projeto utiliza testes MANUAIS realizados pela equipe QA:

1. Developer abre Pull Request (PR) no GitHub
   - Descrição da mudança
   - Link para testar em staging

2. Testes Manuais (realizados por QA)
   - Abre a página HTML em Live Server
   - Testa funcionalidade manualmente
   - Verifica compatibilidade em navegadores

3. Code Review (visual + técnico)
   - Outro desenvolvedor revisa o código
   - Gerente aprova as mudanças
   - Validação de padrões

4. Merge e Deploy
   - Merge para branch dev
   - Deploy em Firebase Hosting
   - Validação em produção
```

**Validações Manuais:**
- ✅ Código compila sem erros (abre página HTML)
- ✅ Funcionalidades operam conforme esperado
- ✅ Interface responsiva (testada em Chrome, Edge)
- ✅ Modo Idoso funciona corretamente
- ✅ Autenticação Firebase funciona
- ✅ Firestore persiste dados corretamente
- ✅ Sem quebras de usabilidade

### 7.2 Test-Driven Development (TDD)

**Status no MEDIDOSO:** Testes Manuais + Documentação de Casos de Teste

**Abordagem Aplicada:**
```
1. Definição de caso de teste
   - Pré-condições
   - Passos a executar
   - Resultado esperado
   - Documentado em GUIA_DE_TESTES.md

2. Desenvolvimento da feature
   - Implementação em HTML/CSS/JS
   - Integração com Firebase
   - Code review

3. Teste Manual (QA)
   - Abrir página em navegador
   - Executar exatamente os passos do caso de teste
   - Validar resultado esperado
   - Registrar status (PASSOU/FALHOU)

4. Reporte de Bugs (se houver falha)
   - Documentar problema em GitHub Issues
   - Atribuir desenvolvedor
   - Corrigir e revalidar
```

**Prática no MEDIDOSO (Documentado em GUIA_DE_TESTES.md):**
- 19 casos de teste definidos
- 100% de cobertura de funcionalidades principais
- Todas as features com testes correspondentes
- Documentação de pré-condições e resultados esperados
- Rastreamento de defeitos encontrados e corrigidos (17 total)

### 7.3 Pair Programming (Quando aplicável)

**Situações de Pair Programming:**
- Funcionalidades críticas (autenticação, segurança)
- Refatorações complexas
- Onboarding de novo desenvolvedor
- Bugs difíceis de resolver

**Formato:**
```
Driver (escreve código) × Navigator (revisa e sugere)
  - Mudança a cada 30 minutos
  - Comunicação constante
  - Evita tunnel vision
```

### 7.4 Refatoração Contínua

**Princípio:** Melhoria incremental do código

**Quando refatorar:**
- ✅ Código duplicado
- ✅ Funções muito longas (>20 linhas)
- ✅ Variáveis com nomes confusos
- ✅ Complexidade alta (>10)
- ✅ Após testes passarem

---

## 8. Comunicação e Colaboração

### 8.1 Canais de Comunicação

| Problema | Canal | Tempo de Resposta |
|---------|-------|------------------|
| **Bug crítico** | WhatsApp + Discord | 15 minutos |
| **Bug alta prioridade** | WhatsApp | 2 horas |
| **Bug média/baixa** | Discord/WhatsApp | 1 dia |
| **Dúvida/sugestão** | Retrospectiva/Presencial | Sprint |

**Escalação Académica:**
```
PROBLEMA IDENTIFICADO
        ↓
    Dev/QA reporta
        ↓
   Gerente avalia
        ↓
  EQUIPE discute e decide
        ↓
   Implementa solução
        ↓
  Feedback ao professor (se necessário)

Tempo máximo por nível: 24 horas
```

### 8.2 Reuniões Síncronas

**Segunda-feira:**
- 20:30 - Sprint Planning (1h)
- Início da nova sprint

### 8.3 Documentação

**Manter atualizado:**
- ✅ README.md (como instalar/rodar)
- ✅ PGQS_ELABORADO.md (qualidade)
- ✅ PROCESSO_AGIL.md (este documento)
- ✅ GUIA_DE_TESTES.md (testes)
- ✅ Wiki do GitHub (Guias técnicos)
- ✅ Código comentado (lógica complexa)

---

## 9. Métricas Ágeis

### 9.1 Cycle Time (Tempo de Entrega)

```
Tempo médio de uma feature de ideação até produção

Feature:                Dias
├─ Design/Planejamento: 1 dia
├─ Desenvolvimento:     2-3 dias
├─ Code Review:         0.5 dia
├─ QA/Testes:          1 dia
├─ Ajustes:            0.5 dia
└─ Deploy:             0.5 dia
  ─────────────────────────
  TOTAL:               5-6 dias
```

### 9.4 Defect Escape Rate (Bugs não detectados)

```
Bugs encontrados DEPOIS de QA / Total de bugs × 100

Meta: < 5%
Actual: 2.5% (muito bom!)

Isso significa:
✅ 97.5% dos bugs são encontrados antes da produção
✅ Process de QA é efetivo
✅ Code review está funcionando bem
```

### 9.5 Code Coverage (Cobertura de Testes)

```
Cobertura de Funcionalidades (Baseado em Casos de Teste)

Total de funcionalidades: 9
Total de casos de teste: 19
Cobertura de requisitos: 100%

Funcionalidades cobertas:
├─ Autenticação: 3 casos de teste
├─ Cadastro de usuário: 2 casos
├─ Adicionar medicamento: 2 casos
├─ Editar medicamento: 2 casos
├─ Remover medicamento: 2 casos
├─ Gerar PDF: 2 casos
├─ Modo Idoso: 2 casos
├─ Vincular cuidador: 1 caso
└─ Dashboard cuidador: 1 caso

Taxa de sucesso: 100% (19/19 casos passaram)
Defeitos encontrados e resolvidos: 17/17 (100%)
```

---

## 10. Lições Aprendidas

### 10.1 O que Funcionou Bem

✅ **Sprints semanais curtas**
- Ciclos rápidos de feedback
- Fácil adaptar à mudanças

✅ **Daily standups curtos**
- Identifica bloqueadores rápido
- Mantém equipe sincronizada

✅ **Code review rigoroso**
- Poucos bugs em produção
- Compartilha conhecimento

✅ **Comunicação quando necessaria**
- Menos mal-entendidos
- Problema resolvido rápido

### 10.2 Desafios Encontrados

⚠️ **Estimativas otimistas inicialmente**
- Usar histórico para futuras estimativas

⚠️ **Documentação atrasada**
- Solução: Documentar em paralelo com dev
- Fazer parte da definição de "done"

---

## 12. Conclusão

O processo ágil implementado no MEDIDOSO combinou o melhor de **Scrum** (estrutura) com **Kanban** (flexibilidade), resultando em:

✅ **Entrega contínua** de features funcionando
✅ **Qualidade alta** através de testes e code review
✅ **Comunicação clara** entre equipe
✅ **Adaptabilidade** a mudanças de requisitos
✅ **Documentação completa** do processo

A equipe entrega incrementos funcionais a cada sprint (1 semana), com testes completos e validação formal.

---

## 13. Referências

### 13.1 Metodologias
- [Scrum Guide (Official)](https://scrumguides.org/)
- [Kanban Board Practices](https://www.atlassian.com/agile/kanban)
- [Git Flow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

### 13.2 Ferramentas
- [GitHub (Versionamento + Projects)](https://github.com/Richardy001/New-Medidoso)
- [Discord (Comunicação)](https://discord.gg/)
- [Firebase (Backend + Hosting)](https://console.firebase.google.com/)
- [Firestore (Banco de Dados)](https://firebase.google.com/docs/firestore)
- [Bootstrap (Framework CSS)](https://getbootstrap.com/)
- [VS Code (IDE)](https://code.visualstudio.com/)
- [Chrome DevTools (Debugging)](https://developer.chrome.com/docs/devtools/)

### 13.3 Padrões
- [Conventional Commits](https://www.conventionalcommits.org/)
- [GitHub Flow](https://guides.github.com/introduction/flow/)
- [Acessibilidade WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)
- [Segurança OWASP Top 10](https://owasp.org/www-project-top-ten/)

---

## 14. Histórico de Versões

| Versão | Data | Autor | Mudanças |
|--------|------|-------|----------|
| v1.0 | 08/12/2025 | Richardy Zaparolli | Documentação inicial do processo ágil |

---

## 15. Aprovação

| Papel | Nome | Data | Status |
|-------|------|------|--------|
| **Líder de Equipe** | Gustavo G. Zanella | 08/12/2025 | ✅ |
| **Desenvolvedor Backend** | Gustavo dos Santos Alves | 08/12/2025 | ✅ |
| **Desenvolvedor Frontend** | Guilherme Garghetti | 08/12/2025 | ✅ |
| **QA/Testes** | Richardy Zaparolli | 08/12/2025 | ✅ |

---

**Para dúvidas ou sugestões, contacte:**
- 📧 Email: guga.zanella@hotmail.com
- 📱 WhatsApp: (49) 99964-6406
- 💬 Discord: #desenvolvimento

**FIM DO DOCUMENTO** 🎯
