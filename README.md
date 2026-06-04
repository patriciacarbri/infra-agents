\# Infra para agentes



Configuração da infraestrutura de agentes de IA e automação da Carbri.



\## Stack



\- \*\*VPS\*\* —Ubuntu 22.04 LTS

\- \*\*Paperclip\*\* — Orquestração de agentes de IA

\- \*\*n8n\*\* — Automação de workflows e postagens



\## Serviços



| Serviço | URL | Status |

|---------|-----|--------|

| n8n | https://n8n.SEU\_DOMINIO | ✅ Ativo |

| Paperclip | http://localhost:3100 (via túnel SSH) | ✅ Ativo |



\## Segurança



\- Firewall UFW ativo

\- Fail2ban protegendo SSH

\- HTTPS com Let's Encrypt (renovação automática)

\- Paperclip acessível apenas via túnel SSH



\## Documentação



\- \[ACESSO.md](./ACESSO.md) — Como acessar os serviços e troubleshooting



\## Missão



> Make good content for tech women 🚀

