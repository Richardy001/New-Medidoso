# SEGURANÇA DO SOFTWARE - MEDIDOSO
## Análise de Riscos e Ameaças

---

## 1. Introdução

**Projeto:** MEDIDOSO  
**Equipe:** 4 membros (Gustavo Zanella, Gustavo Alves, Guilherme Garghetti, Richardy Zaparolli)  
**Nota:** Diogo Felipe Alves saiu durante desenvolvimento; funções assumidas por Guilherme

Este documento mapeia os **riscos e ameaças de segurança** identificados no projeto MEDIDOSO e as **ações mitigadoras** implementadas ou planejadas.

**Escopo:** Segurança da aplicação web, autenticação, dados sensíveis, infraestrutura Firebase.

---

## 2. Classificação de Riscos

### 2.1 Matriz de Risco

| Nível | Probabilidade | Impacto | Ação |
|-------|--------------|---------|------|
| 🔴 **CRÍTICO** | Alta | Muito Alto | Mitigar IMEDIATAMENTE |
| 🟠 **ALTO** | Alta/Média | Alto | Mitigar em curto prazo |
| 🟡 **MÉDIO** | Média | Médio | Monitorar e planejar |
| 🟢 **BAIXO** | Baixa | Baixo | Documentar |

---

## 3. Riscos de Segurança Identificados

### 3.1 Ameaças de Autenticação

#### 🔴 RISCO 1: Força Bruta no Login
**Probabilidade:** 🔴 Alta | **Impacto:** 🔴 Muito Alto | **Risco:** CRÍTICO

**Descrição:**
Usuários mal-intencionados podem tentar múltiplas combinações de email/senha automaticamente para hackear contas.

**Status Atual:** ❌ NÃO IMPLEMENTADO
- Sem limite de tentativas de login
- Sem bloqueio de IP após múltiplas falhas
- Sem notificação de tentativas suspeitas

**Mitigação Planejada (v1.1 - Jan 2026):**
- Rate Limiting: Máx 5 tentativas por hora por email
- Bloqueio de IP: 1 hora após 10 tentativas
- Log de tentativas suspeitas
- Notificação ao usuário via email

**Esforço:** 8-12 horas

---

#### 🟠 RISCO 2: Senha Fraca
**Probabilidade:** 🟠 Média-Alta | **Impacto:** 🔴 Alto | **Risco:** ALTO

**Descrição:**
Usuários podem cadastrar senhas fracas (ex: "123456", "password").

**Status Atual:** ⚠️ PARCIALMENTE IMPLEMENTADO
- ✅ Firebase impõe mínimo 6 caracteres
- ❌ Sem validação de complexidade (maiúscula, número, símbolo)

**Critérios desejados:**
- Mínimo 8 caracteres
- Pelo menos 1 maiúscula
- Pelo menos 1 número
- Pelo menos 1 símbolo (!@#$%^&*)
- Não conter nome do usuário

**Mitigação Planejada (v1.1):**
- Validar complexidade de senha no cadastro
- Usar biblioteca zxcvbn para força de senha
- Sugerir senhas fortes

**Esforço:** 3-4 horas

---

#### 🔴 RISCO 3: Acesso Não Autorizado aos Dados
**Probabilidade:** 🔴 Alta | **Impacto:** 🔴 Muito Alto | **Risco:** CRÍTICO

**Descrição:**
Usuários poderiam acessar medicamentos de outros usuários modificando IDs nas requisições (Insecure Direct Object Reference - IDOR).

**Status Atual:** ⚠️ PARCIALMENTE IMPLEMENTADO
- ✅ Autenticação obrigatória via Firebase
- ❌ Validação fraca nas regras Firestore
- ❌ Sem validação de propriedade do recurso

**Mitigação Implementada (Atual):**
- Regras Firestore básicas verificam autenticação
- Mas não verificam se medicamento pertence ao usuário

**Mitigação Planejada (v1.1 - URGENTE):**
- Verificar userId de cada medicamento
- Impedir acesso cruzado entre usuários
- Validar tamanho de campos

**Esforço:** 4-6 horas

---

#### 🟡 RISCO 4: Exposição de Dados Sensíveis
**Probabilidade:** 🟡 Média | **Impacto:** 🔴 Alto | **Risco:** MÉDIO

**Descrição:**
Dados de saúde (medicamentos) poderiam ser expostos em logs, erros ou backup.

**Status Atual:** ✅ IMPLEMENTADO
- ✅ Firebase criptografa dados em trânsito (HTTPS)
- ✅ Firebase criptografa dados em repouso
- ✅ Sem exposição de dados em console.log
- ✅ Sem credenciais no código

**Mitigação Planejada:**
- Implementar Cloud Logging centralizado
- Mascarar dados sensíveis em logs
- Política de retenção de logs (30 dias)

**Esforço:** 6-8 horas

---

### 3.2 Ameaças de Injeção

#### 🟠 RISCO 5: Injeção de Código (XSS)
**Probabilidade:** 🟠 Média-Alta | **Impacto:** 🔴 Alto | **Risco:** ALTO

**Descrição:**
Usuários poderiam injetar código JavaScript em campos de texto para executar ações maliciosas.

**Status Atual:** ✅ IMPLEMENTADO
- ✅ Usando `.textContent` ao invés de `.innerHTML`
- ✅ Sem eval() ou construção dinâmica de código
- ✅ Bootstrap sanitiza inputs

**Mitigação Planejada:**
- Adicionar bibliotecas de sanitização (DOMPurify)
- Validar input no servidor (Cloud Functions)
- Content Security Policy (CSP) headers

**Esforço:** 4-6 horas

---

#### 🟡 RISCO 6: Injeção de SQL (NoSQL Injection)
**Probabilidade:** 🟡 Média | **Impacto:** 🔴 Alto | **Risco:** MÉDIO

**Descrição:**
Mesmo usando Firestore (não SQL), queries poderiam ser manipuladas se construídas dinamicamente.

**Status Atual:** ✅ IMPLEMENTADO
- ✅ Usando Firestore SDK (queries paramétrizadas)
- ✅ Sem concatenação de queries
- ✅ Sem eval() de dados do usuário

---

### 3.3 Ameaças de Sessão

#### 🟠 RISCO 7: Expiração de Token JWT
**Probabilidade:** 🟠 Média | **Impacto:** 🟡 Médio | **Risco:** ALTO

**Descrição:**
Token de autenticação Firebase pode expirar, deixando usuário logado mas sem permissão para operações.

**Status Atual:** ⚠️ PARCIALMENTE IMPLEMENTADO
- ✅ Firebase gerencia tokens automaticamente
- ✅ Revalidação automática em background
- ❌ Sem notificação ao usuário
- ❌ Sem página de reautenticação graceful

**Mitigação Planejada (v1.1):**
- Interceptar 401 Unauthorized
- Mostrar dialog de reautenticação
- Redirect suave ao login

**Esforço:** 3-4 horas

---

### 3.4 Ameaças de Infraestrutura

#### 🟢 RISCO 8: Disponibilidade do Serviço (DoS)
**Probabilidade:** 🟢 Baixa | **Impacto:** 🟡 Médio | **Risco:** BAIXO

**Descrição:**
Usuários mal-intencionados poderiam fazer requisições em excesso para derrubar o serviço.

**Status Atual:** ✅ IMPLEMENTADO
- ✅ Firebase Hosting escala automaticamente
- ✅ Rate Limiting no Firestore
- ✅ Quotas de projeto configuradas

**Mitigação Implementada:**
- Firebase Hosting: Auto-scaling
- Firestore: Limite de operações por segundo
- Cloud Functions: Timeout automático

**Esforço:** Nenhum (Firebase gerencia)

---

#### 🟢 RISCO 9: Exposição de Chave do Firebase
**Probabilidade:** 🟢 Muito Baixa | **Impacto:** 🔴 Alto | **Risco:** BAIXO

**Descrição:**
Chave pública do Firebase exposta no cliente, permitindo acesso à API.

**Status Atual:** ✅ IMPLEMENTADO
- ✅ Chave pública do Firebase (normal para SPAs)
- ✅ Sem chave privada no código
- ✅ Firestore Rules restringem acesso
- ✅ Sem API Keys expostas

---

## 4. Resumo de Riscos por Status

### 4.1 Riscos Implementados ✅

| Risco | Status | Ação |
|-------|--------|------|
| XSS (Injeção de código) | ✅ Protegido | Usar .textContent |
| NoSQL Injection | ✅ Protegido | Usar SDK paramétrico |
| Dados em repouso | ✅ Criptografado | Firebase padrão |
| Dados em trânsito | ✅ Criptografado | HTTPS obrigatório |
| Credenciais expostas | ✅ Protegido | Sem chaves privadas |

### 4.2 Riscos Críticos a Mitigar 🔴

| Risco | Criticidade | Prazo | Ação |
|-------|------------|-------|------|
| Force Brute | 🔴 CRÍTICO | Jan 2026 | Rate Limiting |
| IDOR | 🔴 CRÍTICO | Jan 2026 | Validação Firestore |
| Senha fraca | 🟠 ALTO | Jan 2026 | Validação complexidade |

### 4.3 Riscos a Monitorar 🟡

| Risco | Criticidade | Ação |
|-------|------------|------|
| Exposição de dados | 🟡 MÉDIO | Logging centralizado |
| XSS avançado | 🟠 ALTO | DOMPurify |
| Token expirado | 🟠 ALTO | Reautenticação graceful |

---

## 5. Mapa de Mitigação por Versão

### 5.1 v1.0 (Atual - COMPLETA)

✅ **Implementadas:**
- Autenticação Firebase
- HTTPS em toda aplicação
- Sem XSS (usando .textContent)
- Sem SQL/NoSQL injection
- Dados criptografados

---

### 5.2 v1.1 (Janeiro 2026 - URGENTE)

🔴 **CRÍTICOS:**
1. **Rate Limiting** (8-12h)
   - Máx 5 tentativas login/hora
   - Bloqueio de IP após 10 falhas
   - Notificação via email

2. **Validação Firestore Rules** (4-6h)
   - Verificar userId de cada medicamento
   - Impedir acesso cruzado entre usuários
   - Validar tamanho de campos

🟠 **ALTOS:**
3. **Validação de Senha** (3-4h)
   - Mínimo 8 caracteres
   - Incluir maiúscula, número, símbolo
   - Usar zxcvbn

4. **Logging Centralizado** (6-8h)
   - Cloud Logging
   - Mascarar dados sensíveis
   - Retenção 30 dias

**Esforço Total v1.1:** 25-35 horas

---

### 5.3 v2.0 (Fevereiro-Março 2026)

🟠 **ALTOS:**
- DOMPurify para sanitização avançada
- Content Security Policy (CSP)
- Testes de segurança E2E
- Reautenticação graceful

---

## 6. Checklist de Segurança

### 6.1 Autenticação & Autorização

- ✅ Autenticação obrigatória
- ✅ Sessão segura (Firebase)
- ⚠️ Rate Limiting (planejado v1.1)
- ✅ Validação de permissões
- ⚠️ Validação senha complexa (planejado v1.1)

### 6.2 Proteção de Dados

- ✅ HTTPS em toda aplicação
- ✅ Dados criptografados em repouso
- ✅ Dados criptografados em trânsito
- ✅ Sem dados sensíveis em logs
- ⚠️ Logging centralizado (planejado v1.1)

### 6.3 Injeção & XSS

- ✅ Sem .innerHTML com dados do usuário
- ✅ Usando .textContent
- ✅ Sem eval()
- ⚠️ DOMPurify (planejado v2.0)
- ⚠️ Content Security Policy (planejado v2.0)

### 6.4 Infraestrutura

- ✅ Firebase Hosting com SSL
- ✅ Auto-scaling habilitado
- ✅ Firestore quotas configuradas
- ✅ Backups automáticos
- ✅ Sem IP fixo expostos

---

## 7. Responsabilidades

| Atividade | Responsável | Data |
|-----------|------------|------|
| **Rate Limiting** | Gustavo Alves (Backend) | Jan 2026 |
| **Validação Firestore** | Gustavo Alves (Backend) | Jan 2026 |
| **Validação Senha** | Gustavo dos Santos | Jan 2026 |
| **Logging Centralizado** | Gustavo Zanella (Lead) | Jan 2026 |
| **Testes Segurança** | Richardy Zaparolli (QA) | Fev 2026 |

---

## 8. Referências de Segurança

- **OWASP Top 10:** https://owasp.org/www-project-top-ten/
- **Firebase Security:** https://firebase.google.com/docs/rules
- **WCAG Segurança:** https://www.w3.org/WAI/
- **CWE/CVSS:** https://cwe.mitre.org/

---

## 9. Conclusão

**Status Geral de Segurança:** 🟡 **MÉDIO-ALTO**

✅ **Protegido:**
- Autenticação (Firebase)
- Criptografia (dados + trânsito)
- XSS (usando .textContent)
- Infraestrutura (Firebase)

🔴 **Riscos Críticos:**
- Rate Limiting (implementar v1.1)
- IDOR no Firestore (implementar v1.1)
- Senha fraca (implementar v1.1)

**Próxima Ação:** Implementar 3 riscos críticos em janeiro de 2026.

---

**Documento versão:** v1.0  
**Data:** 08/12/2025  
**Responsável:** Gustavo Alves (Segurança) + Gustavo Zanella (Liderança)

Para dúvidas sobre segurança:
- 📧 Email: guga.zanella@hotmail.com
- 📱 WhatsApp: (49) 99964-6406
