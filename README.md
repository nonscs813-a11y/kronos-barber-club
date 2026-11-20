# Kronos Barber Club — `kronos-barber-club`

[![Enterprise CI, Firebase TLS, OWASP & LGPD](https://img.shields.io/badge/Testes_Automatizados-20%2F20_Passing-10B981?style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/nonscs813-a11y/kronos-barber-club)
[![Firebase TLS 1.3](https://img.shields.io/badge/Firebase_Firestore-TLS_1.3_%26_Circuit_Breaker-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)](https://github.com/nonscs813-a11y/kronos-barber-club)
[![OWASP Top 10](https://img.shields.io/badge/Segurança-OWASP_Top_10_%26_CSP-0EA5E9?style=for-the-badge)](https://github.com/nonscs813-a11y/kronos-barber-club)
[![LGPD Privacy-by-Design](https://img.shields.io/badge/Privacidade-LGPD_Art._6_7_18-8B5CF6?style=for-the-badge)](https://github.com/nonscs813-a11y/kronos-barber-club)

> **Sistema Web Empresarial 10/10** para **Barbearia & Estética Masculina** — Desenvolvido com **1 arquivo HTML (`index.html`) + 1 arquivo CSS (`styles.css`) + 1 arquivo JavaScript (`app.js`) + Transporte Seguro Firebase Cloud Firestore v1 (`agendamentos_barbearia`)**, blindagem **OWASP Top 10**, conformidade **LGPD (Privacy-by-Design)** e **20 testes automatizados (`node --test`)**.

🌐 **Aplicação Ao Vivo (Produção):** [**`https://nonscs813-a11y.github.io/kronos-barber-club/`**](https://nonscs813-a11y.github.io/kronos-barber-club/)

---

## 🔥 Arquitetura de Conexão Segura Firebase Cloud (Zero-Trust & TLS 1.3)

1. **Validação Anti-SSRF e Enforcement TLS 1.3 (`validateFirebaseEndpoint`):** Bloqueia conexões `http://`, credenciais embutidas em URL e qualquer domínio fora da whitelist oficial do Google Cloud (`firestore.googleapis.com`, `firebaseio.com`, `identitytoolkit.googleapis.com`).
2. **Protocolo Oficial Google Cloud Firestore v1 (`toFirestoreDocument` / `fromFirestoreDocument`):** Serialização tipada (`fields.stringValue`, `booleanValue`, `timestampValue`) com verificação automática de assinatura criptográfica FNV-1a 64-bit na leitura e na escrita.
3. **Injeção Segura de Tokens (`buildSecureHeaders`) & Zero Credenciais Expostas:** Suporte nativo a `Authorization: Bearer <idToken>` e `X-Firebase-AppCheck`, auditado pelo scanner automatizado de segredos (*Secret Leak Scanner* — Teste #10).
4. **Circuit Breaker (`CloudCircuitBreaker`) + `AbortController` Timeout (4.5s):** Protege a aplicação contra lentidão de rede, transicionando automaticamente entre `CLOSED`, `OPEN` e `HALF_OPEN` com persistência local assinada criptograficamente.

---

## 🧪 Suíte de 20 Testes Automatizados (`tests/enterprise.test.js`)

```bash
npm test
# ou diretamente:
node --test tests/enterprise.test.js
```

Todos os **20 testes automatizados** (XSS, Vetores de Injeção, NoSQLi/Prototype Pollution, RateLimiter, Hash FNV-1a, Validação Firebase TLS 1.3 & Anti-SSRF, Serialização Firestore v1 Wire Format, CloudCircuitBreaker, Headers Auth/AppCheck, Secret Leak Scanner, Mascaramento de PII LGPD, Consentimento Obrigatório LGPD, Limites de Schema, Injeção em Formulário, Motor Financeiro em Centavos, Roundtrip Monetário, Persistência CRUD Firebase, Direito ao Esquecimento LGPD, Auditoria HTML/CSP/WCAG e Auditoria Firestore Rules/HSTS) passam com **100% de aprovação**.

---

## 📋 Catálogo Operacional Configurado

| ID | Serviço / Solução | Categoria | Duração / Ref | Valor |
| :-: | :--- | :---: | :---: | :---: |
| `s1` | **Corte Executivo & Degradê Navalhado** | `Cabelo` | `45 min` | **R$ 65,00** |
| `s2` | **Barba Terapia com Toalha Quente & Ozônio** | `Barba` | `35 min` | **R$ 50,00** |
| `s3` | **Combo Prime (Corte + Barba Terapia + Sobrancelha)** | `Combos` | `75 min` | **R$ 105,00** |
| `s4` | **Camuflagem de Fios Brancos (Cabelo ou Barba)** | `Química` | `40 min` | **R$ 75,00** |
| `s5` | **Hidratação Profunda & Detox Capilar** | `Tratamento` | `30 min` | **R$ 55,00** |
| `s6` | **Plano Mensal VIP Club (4 Cortes + 4 Barbas)** | `Assinatura` | `Mensal` | **R$ 290,00** |

---

**Arquitetura e Engenharia Web Sênior por [Julio Cesar (`@nonscs813-a11y`)](https://github.com/nonscs813-a11y)**
