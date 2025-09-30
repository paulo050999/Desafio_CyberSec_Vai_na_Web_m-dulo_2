# Desafio_CyberSec_Vai_na_Web_modulo_2

🛡️ Arquitetura de Defesa – LojaZeta
📌 Visão Geral

A LojaZeta é um e-commerce em crescimento que utiliza Nginx + Node.js + PostgreSQL hospedados em IaaS na nuvem.
Devido a tentativas recentes de SQL Injection, XSS e brute-force em /login, foi elaborado um plano de defesa em camadas, monitoramento centralizado e resposta a incidentes baseada no NIST IR.

⚙️ Arquitetura de Defesa em Camadas

A segurança foi estruturada segundo o modelo Defense in Depth, cobrindo as seguintes camadas:

Perímetro → WAF para mitigar SQLi, XSS e brute-force.

Rede → Segmentação em sub-redes (Web/App e Banco de Dados).

Host → Hardening Linux e atualizações automáticas.

Aplicação → Helmet.js, validação de inputs e cabeçalhos de segurança no Nginx.

Identidade → IAM com MFA no painel de operações e segregação de acessos.

Dados → Criptografia em repouso e em trânsito, backups diários com testes regulares.

📌 O diagrama de camadas está disponível em:
/docs/arquitetura_defesa_camadas.png

🔍 Monitoramento & SIEM

Fontes de log: Nginx, Node.js, PostgreSQL, SO.

Alertas principais: brute-force, SQLi/XSS, indisponibilidade, falha em backups.

KPIs:

MTTD (Mean Time to Detect)

MTTR (Mean Time to Respond)

% de cobertura de logs

Tentativas bloqueadas pelo WAF

🚨 Resposta a Incidentes (NIST IR)

Fluxo estruturado conforme o NIST 800-61:

Detecção → Alertas do SIEM/WAF.

Contenção → Bloqueio de IPs, isolamento de instâncias.

Erradicação → Patches, revisão de código, reinstâncias limpas.

Recuperação → Restauração de backups validados.

Lições aprendidas → Registro e atualização de runbooks.

Runbooks implementados:

SQL Injection / XSS

Brute-force em /login

Indisponibilidade de serviço

📅 Roadmap (80/20)

0–30 dias (Quick Wins):

WAF básico configurado

Centralização mínima de logs

Alertas de brute-force e falha em backups

Teste de restauração de backup

90 dias:

SIEM open-source (Wazuh/ELK)

CIS Hardening em servidores

Runbooks documentados

180 dias:

Automação de resposta simples

MFA integrado em identidade

Exercícios simulados de incidentes

⚠️ Riscos e Assunções

Riscos: equipe pequena e orçamento limitado → pode impactar resposta rápida.

Assunções: ambiente continua em IaaS; sem requisitos regulatórios pesados (ex.: PCI-DSS).

Custos: foco em soluções open-source e serviços gerenciados básicos.

✅ Conclusão

A LojaZeta passa a ter camadas de defesa efetivas, monitoramento acionável e um plano de resposta estruturado mesmo com recursos limitados. O modelo 80/20 garante ganhos rápidos e evolução contínua.
