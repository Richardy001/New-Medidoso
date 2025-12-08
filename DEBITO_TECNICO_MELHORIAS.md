# 📊 DÉBITO TÉCNICO E MELHORIAS
## Projeto MEDIDOSO

---

## 1. Introdução

### 1.1 Objetivo

**Projeto:** MEDIDOSO  
**Equipe:** 4 membros (Gustavo Zanella, Gustavo Alves, Guilherme Garghetti, Richardy Zaparolli)  
**Nota:** Diogo Felipe Alves saiu durante desenvolvimento; funções assumidas por Guilherme

Este documento mapeia o **débito técnico** acumulado durante o desenvolvimento do MEDIDOSO e propõe **melhorias** para versões futuras, garantindo sustentabilidade e qualidade do código.

### 1.2 Definição de Débito Técnico

Débito técnico refere-se a decisões de projeto que foram priorizadas para entregar rápido, mas que acumulam custo técnico (manutenção, refatoração, testes).

---

## 2. Débito Técnico Identificado

### 2.1 Nível de Criticidade

| Nível | Impacto | Urgência |
|-------|---------|----------|
| 🔴 **CRÍTICO** | Afeta funcionalidade ou segurança | Resolver imediatamente |
| 🟠 **ALTO** | Dificulta manutenção ou performance | Resolver em curto prazo (< 1 mês) |
| 🟡 **MÉDIO** | Melhoraria código, mas não bloqueia | Resolver em médio prazo (1-3 meses) |
| 🟢 **BAIXO** | Nice-to-have, melhoria de experiência | Resolver em longo prazo |

---

## 3. Débitos Técnicos Mapeados

### 3.1 Frontend

#### 3.1.1 Falta de Componentização (MÉDIO)

**Situação Atual:**
- Código HTML/CSS/JS espalhado em múltiplos arquivos
- Repetição de componentes (ex: modais, formulários)
- Difícil manutenção e reutilização

**Impacto:**
- Código duplicado (~20% dos arquivos)
- Tempo de manutenção aumenta
- Dificuldade para novos desenvolvedores

**Solução Proposta:**
```
Criar estrutura de componentes reutilizáveis
├── components/
│   ├── modal.html
│   ├── formulario.html
│   ├── botoes.css
│   └── validacao.js
└── Usar template literals ou Web Components
```

**Esforço:** 20-30 horas
**Prioridade:** 🟡 Médio
**Próxima versão:** v2.0

---

#### 3.1.2 Falta de Build Process (MÉDIO)

**Situação Atual:**
- Sem minificação de CSS/JS
- Sem optimização de imagens
- Arquivos não compactados

**Impacto:**
- Tamanho maior dos arquivos (~30% a mais)
- Performance reduzida em conexões lentas
- Tempo de download aumentado

**Solução Proposta:**
```
Implementar build process com Vite ou Webpack
├── Minificação de CSS/JS
├── Remover código não usado
├── Compressão de imagens (WebP)
├── Sourcemaps para debug
└── Bundle analysis
```

**Tecnologia:** Vite (mais leve que Webpack)
**Esforço:** 15-20 horas
**Prioridade:** 🟡 Médio
**Próxima versão:** v2.0

---

#### 3.1.3 Testes Automatizados para UI (ALTO)

**Situação Atual:**
- Testes 100% manuais
- Sem testes de regressão automatizados
- Sem testes de acessibilidade automáticos

**Impacto:**
- Risco de regressão ao adicionar features
- Testes lentos e propensos a erros
- Impossível testar em CI/CD

**Solução Proposta:**
```
Implementar testes com Cypress ou Playwright
├── Testes E2E (fluxos completos)
├── Testes de visual regression
├── Testes de acessibilidade (axe-core)
└── Integração com CI/CD
```

**Tecnologia:** Cypress (mais fácil)
**Esforço:** 30-40 horas
**Prioridade:** 🟠 Alto
**Próxima versão:** v2.0

---

### 3.2 Backend / Firestore

#### 3.2.1 Falta de Rate Limiting (CRÍTICO)

**Situação Atual:**
- Sem proteção contra força bruta no login
- Sem limite de requisições por usuário
- Vulnerável a ataques de negação de serviço (DoS)

**Impacto:**
- Risco de segurança crítico
- Contas podem ser hackeadas (força bruta)
- Custo alto no Firebase (requisições excessivas)

**Esforço:** 8-12 horas
**Prioridade:** 🔴 Crítico
**Próxima versão:** v1.1 (patch urgente)

---

#### 3.2.2 Falta de Validação de Regras Firestore (ALTO)

**Situação Atual:**
- Regras Firestore básicas
- Sem validação de dados no servidor

**Impacto:**
- Vulnerabilidade de segurança
- Dados inconsistentes
- Violação de privacidade

**Esforço:** 6-10 horas
**Prioridade:** 🟠 Alto
**Próxima versão:** v1.1

---

#### 3.2.3 Sem Backup Manual (MÉDIO)

**Situação Atual:**
- Confia apenas em backup automático do Firebase
- Sem estratégia de disaster recovery
- Sem teste de restauração

**Impacto:**
- Risco de perda de dados
- Sem plano B em caso de falha crítica
- Tempo de recuperação desconhecido

**Esforço:** 10-15 horas
**Prioridade:** 🟡 Médio
**Próxima versão:** v1.1

---

### 3.3 Infraestrutura / DevOps

#### 3.3.1 Sem CI/CD Pipeline (ALTO)

**Situação Atual:**
- Deploy manual via Firebase CLI
- Sem testes automáticos antes de publicar
- Sem controle de qualidade em pull requests

**Impacto:**
- Risco de bugs em produção
- Sem rastreamento de mudanças
- Deploy lento e propenso a erros

**Esforço:** 12-18 horas
**Prioridade:** 🟠 Alto
**Próxima versão:** v2.0

---

#### 3.3.2 Sem Logging Estruturado (MÉDIO)

**Situação Atual:**
- Console.log manual espalhado no código
- Sem centralização de logs
- Difícil debug em produção

**Impacto:**
- Impossível rastrear erros em produção
- Tempo gasto em debug aumentado
- Sem histórico de eventos

**Esforço:** 8-12 horas
**Prioridade:** 🟡 Médio
**Próxima versão:** v2.0

---

## 4. Mapa de Melhorias por Versão

### 4.1 v1.1 (Patch - 1-2 meses)

🟠 **Críticos / Altos:**
- ✅ Rate Limiting (CRÍTICO)

🟠 **Altos:**
- ✅ Validação Firestore (ALTO)
- ✅ CI/CD Pipeline (ALTO)

🟡 **Médios:**
- ✅ Backup Manual (MÉDIO)
- ✅ Documentação API (MÉDIO)
- ✅ Logging Estruturado (MÉDIO)

**Esforço Total:** 50-70 horas

---

### 4.2 v2.0 (Major - 3-4 meses)

🟠 **Altos:**
- ✅ Testes Automatizados E2E (ALTO)

🟡 **Médios:**
- ✅ Componentização Frontend (MÉDIO)
- ✅ Build Process (MÉDIO)

🟢 **Baixos:**
- ✅ README Atualizado (BAIXO)

**Esforço Total:** 80-110 horas
**Features Novas:** Otimização de performance

---

### 4.3 v3.0 (Major - Futuro)

- 🌟 Aplicação Mobile (React Native / Flutter)
- 🌟 Dashboard para cuidadores
- 🌟 Integração com API de farmácias
- 🌟 Notificações push
- 🌟 Sincronização offline

---

## 5. Roadmap Visual

```
v1.0 (Atual)
├── Funcionalidade base ✅
├── Testes manuais ✅
└── Documentação básica ✅

v1.1 (2-3 semanas)
├── Rate Limiting ⏳
├── Validação Firestore ⏳
├── Testes E2E ⏳
└── Backup Manual ⏳

v2.0 (2-3 meses)
├── Componentização ⏳
├── Build Process ⏳
├── CI/CD ⏳
└── PWA Support ⏳

v3.0 (Futuro)
├── Mobile App 📱
├── Dashboard Cuidador 👥
└── Integrações 🔗
```

---

## 6. Matriz de Priorização

| Débito | Impacto | Urgência | Esforço | Prioridade |
|--------|---------|----------|---------|-----------|
| Rate Limiting | 🔴 Crítico | Imediato | 12h | 🔴 #1 |
| Validação Firestore | 🟠 Alto | Curto prazo | 10h | 🟠 #2 |
| Testes E2E | 🟠 Alto | Curto prazo | 40h | 🟡 #3 |
| CI/CD | 🟠 Alto | Médio prazo | 18h | 🟡 #4 |
| Componentização | 🟡 Médio | Médio prazo | 30h | 🟢 #5 |
| Build Process | 🟡 Médio | Médio prazo | 20h | 🟢 #6 |

---

## 7. Responsabilidades e Atribuições

| Débito | Responsável | Data Estimada | Status |
|--------|------------|----------------|----|  
| Rate Limiting | Gustavo Alves (Backend) | Jan 2026 | 📝 Planejado |
| Validação Firestore | Gustavo Alves (Backend) | Jan 2026 | 📝 Planejado |
| CI/CD Pipeline | Gustavo Zanella (Lead) | Jan 2026 | 📝 Planejado |
| Testes E2E | Richardy Zaparolli (QA) | Mar 2026 | 📝 Planejado |
| Componentização | Guilherme (Frontend) | Fev 2026 | 📝 Planejado |
| Build Process | Guilherme (Frontend) | Fev 2026 | 📝 Planejado |---

## 8. Referências

- [Technical Debt Quadrant](https://martinfowler.com/bliki/TechnicalDebtQuadrant.html) - Martin Fowler
- [OWASP Top 10](https://owasp.org/www-project-top-ten/) - Security Best Practices
- [Google Web Vitals](https://web.dev/vitals/) - Performance Standards

---

**Documento versão:** v1.0
**Data de criação:** 08/12/2025
**Próxima revisão:** 30/01/2026
**Responsável:** Gustavo G. Zanella (Líder de Equipe)

---

Para discussão sobre débitos técnicos, contactar:
- 📧 Email: guga.zanella@hotmail.com
- 📱 WhatsApp: (49) 99964-6406
