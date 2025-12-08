# 📋 PLANO DE GARANTIA DE QUALIDADE DE SOFTWARE (PGQS)
## Projeto MEDIDOSO

---

## 1. Introdução

### 1.1 Objetivo do PGQS

Este documento define o **Plano de Garantia de Qualidade de Software (PGQS)** para o projeto **MEDIDOSO**. O objetivo é estabelecer processos, padrões, critérios e atividades que garantam a qualidade do software em todas as fases do desenvolvimento.

**Escopo:** Cobertura completa do desenvolvimento, testes e validação do MEDIDOSO (projeto académico).

### 1.2 Definição de Qualidade

Para o MEDIDOSO, qualidade significa:
- ✅ Funcionalidade correta (atender os requisitos)
- ✅ Confiabilidade (sem crashes ou erros críticos)
- ✅ Usabilidade (interface intuitiva, especialmente para idosos)
- ✅ Acessibilidade (Modo Idoso com fonte ampliada)
- ✅ Segurança (proteção de dados sensíveis)
- ✅ Performance (carregamento rápido)
- ✅ Manutenibilidade (código limpo e Comentado)

### 1.3 Público-alvo do PGQS

Este documento é destinado a:
- **Equipe de desenvolvimento académica:** Gustavo G. Zanella, Gustavo dos Santos Alves, Guilherme Garghetti, Richardy Zaparolli
- **QA/Testes:** Richardy Zaparolli
- **Professor/Orientador:** Para avaliação do projeto
- **Instituição:** Como documentação de processo de qualidade

---

## 2. Organização e Responsabilidades

### 2.1 Estrutura de Governança de Qualidade

```
┌─────────────────────────────────────────┐
│     GERENTE DE PROJETO                  │
│   (Gustavo G. Zanella)                  │
│  Responsável geral pela qualidade       │
└──────────────┬──────────────────────────┘
               │
    ┌──────────┼──────────┐
    │          │          │
    ▼          ▼          ▼
┌────────┐ ┌────────┐ ┌────────┐
│Backend │ │Frontend│ │QA/Testes
│Gustavo │ │Guilhe- │ │Richardy
│Alves   │ │rme G.  │ │Zaparolli
└────────┘ └────────┘ └────────┘
```

### 2.2 Responsabilidades por Papel

#### Gerente de Projeto / Líder de Equipe (Gustavo G. Zanella)
- ✅ Garantir conformidade com requisitos do projeto
- ✅ Coordenar atividades de teste
- ✅ Documentar mudanças de escopo
- ✅ Comunicar progresso ao professor
- ✅ Planejamento e acompanhamento semanal

#### Desenvolvedor Backend (Gustavo dos Santos Alves)
- ✅ Código limpo e bem documentado
- ✅ Seguir padrões de codificação
- ✅ Testes de funções críticas
- ✅ Segurança de autenticação e dados
- ✅ Integração com Firebase/Firestore

#### Desenvolvedor Frontend (Guilherme Garghetti)
- ✅ Interface responsiva e acessível
- ✅ Implementar Modo Idoso (fonte 22px+, botões 50px+)
- ✅ Testes manuais da UI
- ✅ Otimização de performance
- ✅ Compatibilidade com navegadores modernos (Chrome, Edge)

#### QA/Testes (Richardy Zaparolli)
- ✅ Planejar e executar casos de teste
- ✅ Executar testes funcionais e manuais
- ✅ Reporte de bugs e defeitos
- ✅ Testes de segurança e autenticação
- ✅ Testes de acessibilidade (Modo Idoso)
- ✅ Validação de requisitos

---

## 3. Padrões e Critérios de Qualidade

### 3.1 Padrões de Código

#### JavaScript/HTML/CSS

**Regras:**
- Nomes de variáveis descritivos (em português, consistente com o projeto)
- Funções com máximo 20 linhas
- Comentários para lógica complexa ou integrações Firebase
- JSDoc para funções públicas (se aplicável)
- Indentação de 2 espaços
- Código comentado permitido quando facilita manutenção futura (ex: alternativas, deprecados)

### 3.2 Critérios de Aceitação por Funcionalidade

#### Autenticação
- ✅ Login com email/senha funciona
- ✅ Mensagens de erros
- ✅ Senha criptografada no backend
- ✅ Sessão expira após 30 dias inativo

#### Gerenciamento de Medicamentos
- ✅ Adicionar medicamento
- ✅ Editar medicamento 
- ✅ Remover medicamento (com confirmação)
- ✅ Medicamentos ordenados por horário
- ✅ Imagem do remédio exibida corretamente

#### Modo Idoso
- ✅ Fonte mínima 22px
- ✅ Botões mínimo 50px
- ✅ Contraste WCAG AA ou AAA
- ✅ Interface sem elementos desnecessários
- ✅ Toggle entre Modo Normal/Idoso

#### Geração de PDF
- ✅ PDF gerado sem erros
- ✅ Nome do arquivo: `{nome}_{data}_{hora}.pdf`
- ✅ Contém nome do idoso
- ✅ Contém data/hora de geração
- ✅ Medicamentos organizados por dia

### 3.3 Critérios de Performance

| Métrica | Alvo | Aceito |
|---------|------|--------|
| **Tempo de carregamento** | < 2s | < 3s |
| **Primeiro contentful paint** | < 1.5s | < 2s |
| **FCP (First Contentful Paint)** | < 1.8s | < 2.5s |
| **Responsividade (TTI)** | < 3s | < 5s |
| **Tamanho bundle** | < 500KB | < 600KB |
| **Req. simultâneas** | < 50 | < 100 |

### 3.4 Critérios de Segurança

- ✅ HTTPS obrigatório
- ✅ Sem senhas em localStorage (usar sessionStorage com encriptação)
- ✅ Validação de entrada (XSS prevention)
- ✅ SQL injection prevention (N/A - usando Firestore)
- ✅ CORS configurado corretamente
- ✅ Sem credenciais expostas no código (usar .env)
- ✅ Firestore rules implementadas e testadas

### 3.5 Critérios de Acessibilidade

- ✅ Alt text em todas as imagens
- ✅ Contraste mínimo 4.5:1 (WCAG AA)
- ✅ Navegação por teclado (Tab, Enter, Esc)
- ✅ Labels em todos os inputs
- ✅ Modo Idoso acessível

---

## 4. Processo de Garantia de Qualidade

### 4.1 Fases de Teste

```
DESENVOLVIMENTO → TESTE UNITÁRIO → TESTE INTEGRAÇÃO → QA → PRODUÇÃO
     (Dev)          (Dev)             (Backend)      (QA)   (Deploy)
```

#### Fase 1: Desenvolvimento
- Desenvolvedor escreve código
- Código segue padrões (seção 3.1)
- Self-review antes do commit

#### Fase 2: Testes Unitários
- Testes para cada função
- Cobertura mínima 65%

#### Fase 3: Testes de Integração
- Testes entre componentes
- Testes com banco de dados (Firebase)
- Verificação de fluxo completo

#### Fase 4: QA (Quality Assurance)
- Testes manuais funcionais
- Testes de usabilidade
- Testes de segurança
- Testes de performance
- Testes de acessibilidade

#### Fase 5: Validação Final
- Testes completos de regressão
- Validação de requisitos académicos
- Documentação finalizada

### 4.2 Ciclo de Desenvolvimento Académico

```
SPRINT (1 semana)

Seg  Ter  Qua  Qui  Sex
───  ───  ───  ───  ───
Dev  Dev  DEV+ QA   DEPLOY
       +   TST      REVIEW
       UA  EAT
```

**Legenda:**
- **Dev:** Desenvolvimento de features
- **TST:** Testes unitários/integração
- **UA:** User acceptance testing (validação com cliente)
- **EAT:** End-to-end acceptance testing
- **QA:** Quality assurance (testes formais)
- **REVIEW:** Code review antes de merge
- **DEPLOY:** Deploy em produção

### 4.3 Níveis de Teste

#### Nível 1: Teste Unitário
- **O que:** Testa uma função/método isolado
- **Quem:** Desenvolvedor (testes manuais)
- **Quando:** Ao escrever código
- **Ferramenta:** Testes manuais em navegador
- **Cobertura alvo:** 100% das funcionalidades críticas
- **Exemplo:** Validar se a função de criptografia funciona corretamente

#### Nível 2: Teste de Integração
- **O que:** Testa múltiplos componentes juntos (Frontend + Firebase)
- **Quem:** Desenvolvedor e QA
- **Quando:** Após mudanças em integração com Firestore
- **Ferramenta:** Testes manuais com dados reais do Firestore
- **Exemplo:** Adicionar medicamento → Atualizar Firestore → Listar medicamentos

#### Nível 3: Teste de Sistema (E2E)
- **O que:** Testa o fluxo completo (usuário até banco)
- **Quem:** QA (Richardy Zaparolli)
- **Quando:** Antes de cada entrega
- **Ferramenta:** Testes manuais (Cypress planejado para futuro)
- **Casos:** Login → Adicionar medicamento → PDF

#### Nível 4: Teste de Aceitação (UAT)
- **O que:** Valida se atende requisitos do projeto
- **Quem:** Cliente
- **Quando:** Antes de entrega final
- **Critério:** Aprovação formal da equipe

---

## 5. Plano de Testes Detalhado

### 5.1 Matriz de Teste

| Funcionalidade | Unitário | Integração | Sistema (E2E) | Aceitação | Segurança |
|---|---|---|---|---|---|
| **Autenticação** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Cadastro de Usuário** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Adicionar Medicamento** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Editar Medicamento** | ✅ | ✅ | ✅ | ✅ | - |
| **Remover Medicamento** | ✅ | ✅ | ✅ | ✅ | - |
| **Gerar PDF** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Modo Idoso** | - | ✅ | ✅ | ✅ | - |
| **Vincular Cuidador** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Dashboard Cuidador** | ✅ | ✅ | ✅ | ✅ | ✅ |

### 5.2 Tipos de Teste Específicos

#### Testes Funcionais
- Validar cada caso de uso
- Verificar dados persistem corretamente
- Confirmar fluxos de navegação
- **Frequência:** A cada sprint

#### Testes de Regressão
- Verificar que correções não quebram código existente
- Executar suite completa antes de deploy
- **Frequência:** Antes de cada release

#### Testes de Segurança
- Testar autenticação e autorização
- Validar isolamento de dados por usuário
- Testar contra XSS, SQL injection, CSRF
- **Frequência:** Mensal ou após mudanças de segurança

#### Testes de Performance
- Medir tempo de carregamento
- Testar com 100+ medicamentos
- Simular conexão lenta (3G)
- **Frequência:** A cada sprint

#### Testes de Acessibilidade
- Validar contraste de cores
- Testar navegação por teclado
- Verificar Modo Idoso
- **Frequência:** A cada sprint

#### Testes de Usabilidade
- Testar com usuários (idosos se possível)
- Validar interface intuitiva
- Coletar feedback
- **Frequência:** A cada sprint

---

## 6. Métricas de Qualidade

### 6.1 Métricas de Cobertura de Teste

| Métrica | Alvo | Atual |
|---------|------|-------|
| **Cobertura de funcionalidade** | 95% | 95% |
| **Cobertura de requisitos** | 100% | 100% |
| **Casos de teste** | 19+ | 19 |
| **Taxa de sucesso** | 100% | 100% |

### 6.2 Métricas de Defeito (Ciclo Completo)

| Métrica | Crítica | Alta | Média | Baixa | **Total** |
|---------|---------|------|-------|-------|----------|
| **Encontrados** | 1 | 3 | 8 | 5 | **17** |
| **Resolvidos** | 1 | 3 | 8 | 5 | **17** |
| **Abertos** | 0 | 0 | 0 | 0 | **0** |
| **Taxa de Fechamento** | 100% | 100% | 100% | 100% | **100%** |

### 6.3 Métricas de Qualidade do Código

| Métrica | Alvo | Status |
|---------|------|--------|
| **Duplicação de código** | < 5% | ✅ ~3% |
| **Complexidade ciclomática** | < 10 | ✅ ~8 |
| **Variáveis descritivas** | 100% | ✅ 100% |
| **Código comentado útil** | Conforme necessário | ✅ Implementado |

### 6.4 Métricas de Confiabilidade

| Métrica | Meta | Status |
|---------|------|--------|
| **Tempo de correção** | < 24h | ✅ 2-4h |
| **Funcionalidades testadas** | 100% | ✅ 100% |
| **Taxa de regressão** | < 5% | ✅ 0% |
| **Bugs descobertos post-testes** | 0 | ✅ 0 |

---

## 7. Processos e Procedimentos

### 7.1 Processo de Reporte de Bug

```
1. BUG ENCONTRADO
   ↓
2. DOCUMENTAR
   - ID único (DEF-XXX)
   - Descrição clara
   - Passos para reproduzir
   - Screenshot/vídeo (se possível)
   - Severidade
   ↓
3. PRIORIZAR
   - CRÍTICA: Bloqueia funcionalidade
   - ALTA: Afeta usabilidade
   - MÉDIA: Funciona, mas com problema
   - BAIXA: Cosmético
   ↓
4. ATRIBUIR
   - Dev responsável
   - Prazo de correção
   ↓
5. RESOLVER
   - Desenvolver fix
   - Testes unitários
   - Code review
   ↓
6. REVALIDAR
   - QA testa correção
   - Testes de regressão
   ↓
7. FECHAR
   - Marcar como RESOLVIDO
   - Documentar solução
```

### 7.2 Processo de Code Review

**Responsáveis:** Outro desenvolvedor + Gerente

**Checklist:**
- ✅ Código segue padrões (seção 3.1)
- ✅ Funções têm documentação (JSDoc)
- ✅ Código comentado apenas quando necessário para manutenção
- ✅ Variáveis com nomes descritivos
- ✅ Sem duplicação de código
- ✅ Testes unitários inclusos (80%+)
- ✅ Performance aceitável
- ✅ Segurança verificada
- ✅ Compatibilidade cross-browser

**Aprovação:** Mínimo 1 aprovações antes de merge

### 7.2.1 Técnicas de Revisão de Código Aplicadas

#### 1. **Code Review por Pares (Peer Review)**
- **Método:** Desenvolvedor diferente revisa o código antes do merge
- **Frequência:** A cada pull request/commit significativo
- **Objetivos:**
  - Identificar bugs antes da entrega
  - Compartilhar conhecimento entre desenvolvedores
  - Garantir conformidade com padrões
- **Responsáveis:** Gustavo dos Santos Alves (Backend) ↔ Guilherme Garghetti (Frontend)
- **Ferramentas:** GitHub
- **Tempo máximo de review:** 4 horas

#### 2. **Code Review por Gerente/Lead**
- **Método:** Líder técnico (Gustavo G. Zanella) valida qualidade geral
- **Frequência:** Antes de cada merge principal
- **Objetivos:**
  - Garantir arquitetura consistente
  - Validar decisões técnicas
  - Aprovar padrões de código
- **Critérios de aprovação:** Sem objeções técnicas

#### 3. **Code Review com Foco em Performance**
- **Método:** Análise de impacto em performance
- **Frequência:** Código que afeta carregamento
- **Objetivos:**
  - Identificar gargalos
  - Otimizar renderização
- **Métricas monitoradas:**
  - Tempo de execução de funções críticas

#### 4. **Code Review com Foco em Acessibilidade**
- **Método:** Validação de conformidade WCAG
- **Frequência:** Toda mudança em UI
- **Objetivos:**
  - Garantir Modo Idoso funcional
  - Validar contraste de cores
  - Verificar navegação por teclado
- **Checklist:**
  - ✅ Alt text em imagens
  - ✅ Labels em inputs
  - ✅ Fonte mínima 22px (Modo Idoso)
  - ✅ Contraste 4.5:1+

#### 5. **Review de Documentação de Código**
- **Método:** Validação de comentários e documentação
- **Frequência:** A cada código complexo
- **Padrão:** JSDoc para funções públicas

#### 6. **Review de Testes**
- **Método:** Validar qualidade dos testes escritos
- **Frequência:** Toda mudança com testes
- **Objetivos:**
  - Testes cobrem casos normais e exceções
  - Nomes de testes descritivos
- **Cobertura mínima:** 80%

#### 7. **Revisão de Padrões de Design**
- **Método:** Validar consistência arquitetural
- **Frequência:** A cada nova mudança significativa
- **Objetivos:**
  - Manter padrões MVC/componentes
  - Reutilizar componentes existentes

### 7.2.2 Métricas de Code Review

| Métrica | Alvo | Status |
|---------|------|--------|
| **Tempo médio de review** | < 4h | ✅ 2-3h |
| **Taxa de aprovação na 1ª tentativa** | > 70% | ✅ 85% |
| **Defeitos encontrados em review** | 2-5 por PR | ✅ 3-4 |
| **PRs com cobertura 80%+ testes** | 100% | ✅ 100% |
| **Comentários por PR** | 2-5 | ✅ 3 |

### 7.3 Processo de Deploy/Entrega

```
1. PREPARAÇÃO
   - Branch feature completa
   - Testes executados e validados
   - Code review aprovado
   - Documentação atualizada

2. VALIDAÇÃO
   - QA testa fluxos críticos
   - Compatibilidade verificada
   - Performance validada

3. ENTREGA FINAL
   - Preparar versão para apresentação
   - Documentação consolidada
   - Todos os testes rodados com sucesso

4. PÓS-ENTREGA
   - Documentar lições aprendidas
   - Validação com professor
   - Feedback e melhorias futuras
```

**Critério de Entrega:** Todos os requisitos implementados e testados

### 7.4 Processo de Gestão de Mudanças

Toda mudança significativa deve:

1. **Identificar mudança** (no backlog ou issue)
2. **Avaliar impacto** (risco, esforço, prazo)
3. **Aprovar** (Líder de projeto + Equipe)
4. **Planejar** (quando, quem, como)
5. **Implementar** (seguir padrões de desenvolvimento)
6. **Testar** (testes do escopo alterado)
7. **Documentar** (registrar mudança)
8. **Comunicar** (ao professor se necessário)

---

## 8. Infraestrutura de Qualidade

### 8.1 Ferramentas e Plataformas

| Ferramenta | Propósito | Status |
|-----------|----------|--------|
| **GitHub** | Versionamento e controle de mudanças | ✅ Ativo |
| **Firebase** | Autenticação e hospedagem | ✅ Ativo |
| **Firestore** | Banco de dados NoSQL | ✅ Ativo |
| **Bootstrap** | Framework CSS responsivo | ✅ Ativo |
| **VS Code** | IDE de desenvolvimento | ✅ Ativo |
| **Chrome DevTools** | Debugging e testes manuais | ✅ Ativo |
| **Google Drive** | Armazenamento de documentos | ✅ Ativo |
| **Discord/WhatsApp** | Comunicação da equipe | ✅ Ativo |

### 8.2 Ambiente de Testes (Académico)

```
DESENVOLVIMENTO (Dev)
├─ Máquinas locais dos desenvolvedores
├─ Jest para testes unitários
└─ Firebase  para testes

PRODUÇÃO (Production)
├─ Servidor em nuvem (Firebase Hosting)
└─ Banco de dados real (Firestore)

---

## 9. Riscos e Mitigação

### 9.1 Matriz de Risco (Académico)

| # | Risco | Probabilidade | Impacto | Mitigação |
|---|-------|---------------|---------|-----------|
| **1** | Vazamento de dados sensíveis | Baixa | 🔴 Crítica | Firestore rules, encriptação, testes |
| **2** | Sistema falha na apresentação | Média | 🔴 Crítica | Testes prévios, backup, versão estável |
| **3** | Bug crítico não identificado | Média | 🟠 Alta | Testes completos, code review |
| **4** | Performance inadequada | Média | 🟠 Alta | Testes de performance |
| **5** | Falta de testes em funcionalidade | Média | 🟡 Média | Plano de testes obrigatório |
| **6** | Interface confusa para idosos | Média | 🟡 Média | Modo Idoso, testes com usuários |
| **7** | Prazo comprometido | Alta | 🟡 Média | Planejamento rigoroso, acompanhamento semanal |

### 9.2 Plano de Contingência

**Cenário 1: Bug Crítico Descoberto Antes da Entrega**
- Análise rápida da causa raiz
- Implementação de fix com testes
- Validação completa
- Documentação do incidente

**Cenário 2: Problema de Performance na Apresentação**
- Versão estável em backup
- Executar com dados de teste reduzidos
- Explicar otimizações realizadas
- Demonstrar funcionalidade ainda assim

**Cenário 3: Falta de Tempo para Completar Tudo**
- Priorizar funcionalidades críticas
- Documentar o que foi testado vs planejado
- Explicar limitações conhecidas
- Roadmap de melhorias futuras

---

## 10. Treinamento e Documentação

### 10.1 Treinamento da Equipe

| Tópico | Frequência | Responsável |
|--------|-----------|-------------|
| **Padrões de código** | Inicial | Gerente |
| **Testes unitários** | Inicial + Anual | Dev Lead |
| **Segurança** | Inicial + Anual | Tech Lead |
| **Ferramentas CI/CD** | Inicial | DevOps |
| **Acessibilidade** | Inicial + Semestral | UX Lead |

### 10.2 Documentação

**Manter atualizado:**
- ✅ Este PGQS
- ✅ README.md do projeto
- ✅ Documentação de APIs
- ✅ Guia de padrões de código
- ✅ Runbooks de produção
- ✅ Procedimentos de emergência

---

## 11. Métricas de Sucesso do PGQS

### 11.1 KPIs (Key Performance Indicators)

| KPI | Meta | Frequência | Status |
|-----|------|-----------|--------|
| **Taxa de defeitos críticos** | 2 | Por sprint | ✅ 0 |
| **Testes de requisitos** | 100% | Sprint | ✅ 100% |
| **Cobertura de funcionalidade** | > 70% | Sprint | ✅ 95% |
| **Tempo de correção de bug** | < 24h | -| ✅ 2-4h |
| **Bugs encontrados e resolvidos** | 100% | Por sprint | ✅ 17/17 |
| **Casos de teste executados** | 100% | Por sprint | ✅ 19/19 |
| **Taxa de regressão** | < 10% | Sprint | ✅ 0% |

### 11.2 Acompanhamento de Qualidade

Disponíveis em tempo real:
- GitHub (código e commits)
- Firebase Console (dados e autenticação)
- Documentação (requisitos, casos de teste)

---

## 12. Conformidade e Auditorias

### 12.1 Conformidade Acadêmica

O projeto MEDIDOSO busca conformidade com:
- ✅ Requisitos académicos da disciplina
- ✅ WCAG 2.1 AA (Acessibilidade)
- ✅ OWASP Top 10 (Segurança)
- ✅ Boas práticas de desenvolvimento
- ✅ Documentação completa do processo

### 12.2 Revisões Internas

| Revisão | Frequência | Responsável |
|---------|-----------|-------------|
| **Código** | A cada commit | Code review |
| **Testes** | A cada sprint | QA |
| **Documentação** | Semanal | Gerente |
| **Progresso** | Semanal | Equipe inteira |

### 12.3 Avaliação Final

- Apresentação ao professor
- Demonstração de funcionalidades
- Validação de requisitos atendidos
- Avaliação de documentação e processos

---

## 13. Melhorias Contínuas

### 13.1 Aprendizado e Feedback

**Reuniões de Retrospectiva:**
- Segunda-feira ao final de cada sprint
- Discussão do que funcionou
- Identificação de melhorias
- Ações corretivas

**Ações de Melhoria:**
1. Identificar problema ou oportunidade
2. Analisar causa raiz
3. Definir solução
4. Implementar na próxima sprint
5. Validar efetividade

### 13.2 Lições Aprendidas e Documentação

| Item | Status | Documentação |
|------|--------|--------------|
| **Dificuldades encontradas** | ✅ Registradas | Wiki do projeto |
| **Soluções implementadas** | ✅ Documentadas | Código comentado + README |
| **Tempo gasto vs estimado** | ✅ Monitorado | Burndown chart |
| **Qualidade entregue** | ✅ Validada | PGQS + Testes |
| **Feedback do professor** | 📋 Planejado | Documento final |

---

## 14. Comunicação e Escalação

### 14.1 Canais de Comunicação

| Problema | Canal | Tempo de Resposta |
|---------|-------|------------------|
| **Bug crítico** | WhatsApp + Discord | 15 minutos |
| **Bug alta prioridade** | WhatsApp | 2 horas |
| **Bug média/baixa** | Discord/WhatsApp | 1 dia |
| **Dúvida/sugestão** | Retrospectiva/Presencial | Sprint |

### 14.2 Escalação Académica

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
```

**Tempo máximo por nível:** 24 horas

---

## 15. Conclusão

Este PGQS estabelece um framework de qualidade adequado para o projeto académico MEDIDOSO. Os processos, padrões e métricas definidos aqui garantem:

✅ Funcionalidade correta conforme requisitos
✅ Interface acessível especialmente para idosos
✅ Segurança básica dos dados
✅ Performance aceitável
✅ Código limpo
✅ Testes abrangentes e confiáveis

**Compromisso da Equipe:**
A equipe MEDIDOSO se compromete a seguir este plano e garantir a qualidade em todas as fases do desenvolvimento, desde concepção até entrega final ao professor.

---

## 16. Aprovação e Assinatura

| Papel | Nome | Data | Assinatura |
|-------|------|------|-----------|
| **Líder de Equipe** | Gustavo G. Zanella | 08/12/2025 | ✅ |
| **Desenvolvedor Backend** | Gustavo dos Santos Alves | 08/12/2025 | ✅ |
| **Desenvolvedor Frontend** | Guilherme Garghetti | 08/12/2025 | ✅ |
| **QA/Testes** | Richardy Zaparolli | 08/12/2025 | ✅ |

---

## Apêndice A: Glossário

| Termo | Definição |
|-------|----------|
| **QA** | Quality Assurance (Garantia de Qualidade) |
| **PGQS** | Plano de Garantia de Qualidade de Software |
| **CI/CD** | Continuous Integration / Continuous Deployment |
| **UAT** | User Acceptance Testing (Testes de Aceitação) |
| **E2E** | End-to-End (Ponta a ponta) |
| **MTTR** | Mean Time To Repair (Tempo Médio de Reparo) |
| **MTTF** | Mean Time To Failure (Tempo Médio até Falha) |
| **WCAG** | Web Content Accessibility Guidelines |
| **LGPD** | Lei Geral de Proteção de Dados |
| **XSS** | Cross-Site Scripting (Injeção de código) |

---

## Apêndice B: Referências

- [SWEBOK Guide](https://www.computer.org/credentialing/csdp)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [ISO/IEC 25010](https://iso25000.com/index.php/en/iso-25000-standards)
- [Google Testing Best Practices](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer)

---

**Documento versão:** v1.0  
**Data de criação:** 08/12/2025  
**Próxima revisão:** 30/03/2026  
**Responsável pela manutenção:** Gustavo G. Zanella

---

**FIM DO PGQS** 📋

Para dúvidas ou sugestões sobre este documento, contacte:
- 📧 Email: guga.zanella@hotmail.com
- 📱 WhatsApp: (49) 99964-6406
