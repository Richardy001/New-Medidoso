# CONFIABILIDADE DO SOFTWARE
## Projeto MEDIDOSO

---

## 1. Objetivo

**Projeto:** MEDIDOSO  
**Equipe:** 4 membros (Gustavo Zanella, Gustavo Alves, Guilherme Garghetti, Richardy Zaparolli)  
**Nota:** Diogo Felipe Alves saiu durante desenvolvimento; funções assumidas por Guilherme

Este documento apresenta os critérios e práticas de **confiabilidade do software** implementados no projeto **MEDIDOSO**, garantindo que o sistema funcione de forma estável através da infraestrutura do Firebase, tratamento de erros e testes de confiabilidade.

---

## 2. Características de Confiabilidade Implementadas

### 2.1 Infraestrutura Confiável

A confiabilidade do MEDIDOSO é garantida pela infraestrutura do Firebase:

- **Firebase Hosting:** Hospedagem com CDN global, HTTPS obrigatório e certificado SSL automático
- **Firestore Database:** Banco de dados replicado automaticamente com backup
- **Uptime:** Sistema acessível 100% do tempo (conforme requisito do projeto)

### 2.2 Tratamento de Erros

Implementação de mecanismos para prevenir e recuperar de falhas:

- **Try-catch em operações críticas:**
  - Autenticação Firebase
  - Operações CRUD no Firestore
  - Geração de PDF

- **Mensagens de erro ao usuário:**
  - Em português
  - Sugestão de ação (ex: "Verifique sua conexão")
  - Sem expor detalhes técnicos

- **Log de erros:**
  - Console.error com contexto
  - Timestamp e stack trace

- **Validação de entrada:**
  - Validar email
  - Validar data e hora
  - Validar quantidade de medicamentos

### 2.3 Recuperação de Falhas

Estratégias implementadas para recuperação:

| Cenário | Ação de Recuperação |
|---------|-------------------|
| **Erro ao salvar medicamento** | Notificar ao usuário e permitir nova tentativa |
| **Perda de conexão** | Exibir mensagem de offline e sincronizar quando reconectar |
| **Erro de autenticação** | Reautenticar automaticamente ou solicitar novo login |

---

## 3. Testes de Confiabilidade Realizados

### 3.1 Testes Manuais

Conforme documentado em **GUIA_DE_TESTES.md**, realizamos:

- **19 casos de teste** cobrindo 100% das funcionalidades
- **100% de taxa de sucesso** nos testes
- **17 defetos encontrados e corrigidos** durante o processo
- **Zero bugs descobertos** após testes finais

### 3.2 Cenários Testados

- ✅ Autenticação e login
- ✅ Criação, leitura, atualização e exclusão de medicamentos
- ✅ Agendamento de medicamentos
- ✅ Geração de relatórios em PDF
- ✅ Validação de dados de entrada
- ✅ Comportamento sob erros de conexão

---

## 4. Métricas de Confiabilidade

| Métrica | Status |
|---------|--------|
| **Uptime** | 100% (Firebase Hosting) |
| **Taxa de sucesso de testes** | 100% (19/19 casos) |
| **Defetos corrigidos** | 100% (17/17) |
| **Bugs pós-release** | 0 |
| **Taxa de regressão** | 0% |

---

## 5. Monitoramento e Backup

### 5.1 Monitoramento

- **Firebase Console:** Monitoramento do banco de dados em tempo real
- **Chrome DevTools:** Performance local e detecção de erros
- **Logs do Firestore:** Auditoria de operações

### 5.2 Backup

- **Firestore:** Backup automático da infraestrutura Firebase
- **Retenção:** Dados mantidos conforme política de retenção do Firebase

---

## 6. Responsabilidades

| Papel | Responsabilidade |
|------|------------------|
| **Desenvolvedor** | Implementar tratamento de erro e validação |
| **QA** | Executar testes manuais e verificar confiabilidade |
| **Gerente** | Monitorar saúde do sistema |

---

## 7. Conclusão

A confiabilidade do MEDIDOSO é garantida através de:

✅ **Infraestrutura confiável** (Firebase com 100% uptime)
✅ **Código robusto** (try-catch, validação de entrada)
✅ **Testes completos** (19 casos, 100% cobertura, 17 defetos resolvidos)
✅ **Monitoramento** (Firebase Console e Chrome DevTools)

---

**Documento versão:** v1.0
**Data de criação:** 08/12/2025
**Responsável:** Gustavo G. Zanella (Líder de Equipe)
