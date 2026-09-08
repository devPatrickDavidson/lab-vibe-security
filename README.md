# lab-vibe-security

# 🛡️ PatrickSec AI — LLM Application Security Lab

Laboratório prático de **Segurança em Aplicações de Inteligência Artificial (AppSec)** demonstrando os riscos associados ao desenvolvimento rápido sem salvaguardas arquiteturais (*Vibe Coding*) versus a implementação de controles defensivos baseados no **OWASP Top 10 for LLMs**.

---

## 🎯 Visão Geral do Projeto

Aplicações integradas a Modelos de Linguagem (LLMs) frequentemente introduzem vulnerabilidades críticas ao tratar saídas da IA como confiáveis ou ao delegar a segurança exclusivamente ao alinhamento semântico do modelo (RLHF). 

O **PatrickSec AI** é um ambiente interativo construído em Python e Streamlit que permite testar e comparar lado a lado dois paradigmas arquiteturais:
1. **Modo Vulnerável (Vibe Coding):** Concatenação crua de prompts, credenciais operacionais expostas no contexto de runtime, ausência de RBAC e renderização de saídas sem sanitização.
2. **Modo Seguro (Hardened Architecture):** Segregação estrita de papéis (`system` vs `user`), princípio do menor privilégio (RBAC), sanitização e escape de código no DOM e controle de exaustão de contexto.

---

## 🧪 Matriz de Riscos & Vulnerabilidades Avaliadas

| ID OWASP | Vulnerabilidade | Vetor de Ataque Simulado | Mitigação Arquitetural |
| :--- | :--- | :--- | :--- |
| **LLM01** | Prompt Injection | Quebra de contexto operacional via técnica de sumarização para extração de diretrizes internas. | Segregação nativa de papéis via API de chat e isolamento da camada de instruções. |
| **LLM02** | Sensitive Information Disclosure | Obtenção de topologia de VPC, host de banco de dados e tokens em solicitações cotidianas de onboarding. | Remoção de credenciais do contexto de prompt e restrição de escopo de dados em tempo de execução. |
| **LLM05** | Improper Output Handling | Injeção de componentes HTML/CSS interpretados diretamente pelo navegador da aplicação. | Desativação de flags inseguras (`unsafe_allow_html=False`) e encoding estrito de caracteres no frontend. |
| **LLM06** | Excessive Agency | Obtenção de comandos operacionais destrutivos (`$ psql` de superusuário) sem checagem de autorização. | Aplicação de Controle de Acesso Baseado em Papéis (RBAC) e bloqueio de ações críticas por política. |

---

## 🛠️ Tecnologias Utilizadas

- **Linguagem:** Python 3.12+
- **Interface & Dashboard:** Streamlit
- **Motor de Inferência (Inference Engine):** Groq SDK (`openai/gpt-oss-20b`)
- **Persistência Local:** JSON Storage
- **Segurança da Informação:** OWASP Top 10 for LLMs Guidelines

---

## 🚀 Como Executar o Projeto Localmente

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/devPatrickDavidson/lab-vibe-security
   cd lab-vibe-security
