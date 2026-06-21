# Plano de Conteúdo — **Vibe Coding na Prática**

> **Construa automações e agentes de IA conversando — do primeiro workflow ao app no ar.**
> Curso original INEMA.CLUB no formato v2 (dark premium, camada de aprendizagem). Conteúdo técnico próprio; nenhuma fonte, comunidade, plataforma ou autor original é citado.

- **courseId:** `vibe-coding`
- **Formato:** Curso INEMA v2 (HTML self-contained + camada de aprendizagem: progresso, marcar-lido, dúvida, anotação/highlight, "minha jornada", export/import, temas)
- **Público:** pessoas que querem construir automações e aplicações com IA conversando em linguagem natural, mesmo sem saber programar.
- **Promessa:** sair do zero (nunca usou um assistente de código) e chegar a um app de verdade no ar — com automações, deploy, autenticação e pagamento.
- **Pré-requisitos:** um computador, contas gratuitas nas ferramentas usadas, vontade de iterar. Nenhum conhecimento prévio de programação.

---

## Visão geral — 4 trilhas, 10 módulos, 80 tópicos

| Trilha | Cor | Tema | Módulos | Tópicos |
|--------|-----|------|---------|---------|
| **T1 — Fundamentos & Primeiro Workflow** | Emerald 🟢 | Montar o ambiente e construir/depurar/otimizar o primeiro workflow conversando | 3 | 22 |
| **T2 — Domínio do Agente de Código** | Blue 🔵 | Workflows agênticos, o framework WAT, MCP, skills e gestão de tokens | 3 | 25 |
| **T3 — Hospedagem & Deploy** | Purple 🟣 | Tirar a automação do local e colocá-la rodando sozinha na nuvem | 2 | 16 |
| **T4 — Construindo Frontends & Apps** | Amber 🟡 | Transformar a automação em um app completo com design, login e pagamento | 2 | 17 |

**Arco de aprendizagem:** Fundamentos → Domínio → Produção → Produto.
T1 ensina a conversar com a IA para construir. T2 ensina a estruturar isso como sistemas agênticos reutilizáveis. T3 coloca no ar rodando sozinho. T4 dá uma cara de produto (interface, usuários, receita).

---

## Trilha 1 — Fundamentos & Primeiro Workflow 🟢 *(Emerald)*

> Objetivo: entender o que é "vibe coding", montar o ambiente completo e percorrer o ciclo Plan → Build → Troubleshoot → Optimize construindo um agente de suporte por e-mail de verdade.

### Módulo 1.1 — Fundamentos & Ambiente
*Do conceito ao ambiente conectado e verificado.*
1. **O que é vibe coding** — construir descrevendo o resultado em linguagem natural; a IA cuida da implementação.
2. **O assistente de código no editor** — o que ele faz (ler arquivos, escrever/editar, rodar comandos, conectar ferramentas via MCP); assinatura vs API e a economia de tokens.
3. **Projeto dedicado + CLAUDE.md** — uma pasta por projeto; o CLAUDE.md como "system prompt" persistente (papel, contexto, preferências).
4. **Conectando o n8n via MCP server** — o que é o n8n; o MCP que deixa a IA ler/criar/depurar workflows; credenciais só no `.env`.
5. **Skills do n8n** — documentação que ensina a IA os tipos de nós, parâmetros e padrões.
6. **Verificação das 4 conexões** — diretório do projeto, conexão MCP, leitura de workflows e documentação dos nós.

### Módulo 1.2 — O Ciclo Completo: Plan → Build → Troubleshoot → Optimize
*O ciclo de quatro fases, demonstrado em um agente de suporte por e-mail com RAG.*
1. **Modos de permissão & Plan Mode** — pedir antes/editar automático/plano/auto/bypass; quando usar cada um.
2. **Fase 1 — Plan** — a IA pesquisa nós, faz perguntas de esclarecimento e propõe um plano para aprovar.
3. **Fase 2 — Build** — a IA cria e valida os nós no n8n; o que ela NÃO faz (credenciais, planilhas, mapeamento).
4. **Credenciais OAuth & chaves** — conectar Gmail/Google Sheets (OAuth2) e OpenAI (chave de API) com segurança.
5. **Fase 3 — Troubleshoot** — devolver a mensagem de erro para a IA diagnosticar e corrigir.
6. **Fase 4 — Optimize** — pedir melhorias em linguagem natural (ex.: mudar o intervalo de polling).
7. **Projeto-guia: agente de suporte (RAG)** — classificador de texto + vector store + agente de IA que rascunha respostas a partir de PDFs de política.
8. **Verificação & testes** — checklist visual; testar cenários reais; *green ≠ correto* (a IA deve recusar inventar o que não sabe).

### Módulo 1.3 — De "Funciona" a "Funciona Bem": Enhancement
*Transformar um workflow que "passa nos testes" em um pronto para o mundo real.*
1. **Filosofia de enhancement em camadas** — iterar uma mudança por vez; "funciona" vs "funciona bem".
2. **Ordem de prioridade** — erro → lógica → qualidade da saída → performance.
3. **Fallback sem match** — marcador de confiança + nó de código + IF + rascunho "vamos pesquisar e retornar".
4. **Filtro por tempo** — processar só e-mails mais novos que X minutos (sintaxe "newer than" no gatilho).
5. **Filtrar e-mails automáticos** — detectar no-reply/out-of-office/newsletter; a armadilha de case sensitivity.
6. **Voz/tom da marca** — atualizar o system prompt do agente e o rascunho de fallback.
7. **Personalização com nome do cliente** — extrair o nome da assinatura; fallback "Olá".
8. **Indicador de confiança** — badge alto/médio/baixo a partir do score do vector store (revisão interna).

---

## Trilha 2 — Domínio do Agente de Código 🔵 *(Blue)*

> Objetivo: sair do "construir um workflow" para "estruturar sistemas agênticos reutilizáveis" — entender o framework WAT, estender o agente com MCP, empacotar tudo em skills e gerir tokens.

### Módulo 2.1 — Workflows Agênticos & o Framework WAT
*A mentalidade e a arquitetura por trás de toda automação agêntica.*
1. **O assistente sob demanda (local)** — pesquisar, construir arquivos e ficar mais inteligente a cada uso; tudo roda na sua máquina.
2. **O que são workflows agênticos** — descrever o resultado, não os passos; a IA raciocina e se adapta.
3. **Determinístico vs não-determinístico** — automação tradicional é previsível; IA generativa varia por natureza.
4. **WAT — W = Workflows** — arquivos de instrução em markdown (como uma descrição de cargo/SOP).
5. **WAT — A = Agent** — o coordenador que lê os workflows, vê as ferramentas e decide qual usar.
6. **WAT — T = Tools** — scripts Python de um trabalho cada; a IA escreve e conserta, sem precisar programar.
7. **O loop de auto-melhoria** — rodar, errar, diagnosticar, consertar a ferramenta e atualizar o workflow.
8. **CLAUDE.md profissional** — documento de onboarding; estrutura de pastas (workflows/tools/temporary/.env); manter enxuto (< ~500 linhas).
9. **Primeiro workflow agêntico** — transformar notas brutas em um documento limpo e estruturado, com o loop de iteração.

### Módulo 2.2 — Estendendo o Agente: MCP & Pesquisa
*Dar superpoderes ao agente conectando ferramentas externas.*
1. **O que é MCP (Model Context Protocol)** — uma conexão que expõe muitas ferramentas; o agente decide qual chamar.
2. **Onde encontrar MCP servers** — diretórios e busca; categorias (scraping, bancos, documentos, comunicação).
3. **Instalar um MCP server** — gerar o `.mcp.json` e inserir a chave de API manualmente (nunca no chat).
4. **Verificar e diagnosticar** — comando `/mcp`; reiniciar quando o server não aparece.
5. **Workflow de pesquisa com Firecrawl** — dar um tema, pesquisar a web, sintetizar e gerar um documento (plan→build→run).
6. **Pipeline de saída** — produzir markdown e converter para documento via uma ferramenta gerada.
7. **Iteração & auto-cura** — feedback específico; se quebra, pedir para a própria IA se consertar.

### Módulo 2.3 — Skills, Geração de Artefatos & Tokens
*Empacotar workflows como comandos reutilizáveis e dominar o orçamento de contexto.*
1. **O que são skills** — instruções em markdown na pasta de skills, chamáveis como slash command.
2. **Skill vs digitar** — quando empacotar (repetição, consistência, complexidade, time) e quando não.
3. **Skill na prática** — construir e invocar uma skill de "rascunhar e-mail" como `/draft-email`.
4. **Gerador de slide deck** — outro build WAT: documento → apresentação profissional.
5. **5 padrões de prompting** — objetivo (não passos), saída específica, Plan Mode primeiro, feedback (não correção), tratar a IA como especialista.
6. **Context rot & limiares** — qualidade degrada após ~60%; zonas 0-50/50-70/70-85/85%+.
7. **`/clear` vs `/compact`** — reset total vs resumo inteligente; quando usar cada um.
8. **Economia de tokens** — uma tarefa por sessão; definir "pronto"; skills em vez de CLAUDE.md gigante; desligar MCPs não usados.
9. **12 dicas finais** — checklist consolidado para construir workflows agênticos com qualidade.

---

## Trilha 3 — Hospedagem & Deploy 🟣 *(Purple)*

> Objetivo: tirar a automação do "rodar quando eu mando" e colocá-la rodando sozinha na internet — por agenda ou por evento — com retries, logs e alertas.

### Módulo 3.1 — Do Local ao Sempre-Ligado: GitHub & Trigger.dev
*A infraestrutura para automações que rodam sem ninguém olhando.*
1. **Automações hospedadas** — scripts que rodam sozinhos, por agenda (cron) ou disparados por evento (webhook).
2. **O "agentic gap"** — em produção a IA não está mais observando para se auto-curar; como fechar essa lacuna.
3. **Cron** — o padrão de 5 campos (ex.: `0 7 * * *` = 7h todo dia).
4. **GitHub como armazenamento de código** — commit/push/repo; histórico e rollback; deploy puxa da nuvem.
5. **gh CLI & `.gitignore`** — autenticação; a regra de ouro: o `.env` nunca sobe.
6. **Trigger.dev** — o motor de execução: sem timeout, retries automáticos, traces completos, alertas.
7. **Inicializar projeto + MCP do Trigger.dev** — `init`, worker de dev, anatomia do dashboard, dev vs produção.
8. **Secrets management** — variáveis de ambiente na nuvem injetadas em runtime; `.env.example`; checar dev *e* prod.

### Módulo 3.2 — Agentes em Produção: Agendados & Webhooks
*Dois builds reais de ponta a ponta, com erro tratado e debug em produção.*
1. **Masterclass: agente de pesquisa agendado** — cron → Firecrawl → síntese → linha no Google Sheets, rodando toda manhã.
2. **OAuth refresh token** — setup único; quando o Playground falha, o fallback via script no terminal.
3. **Debug que só aparece em produção** — formato de resposta inesperado da API; copiar o trace para a IA corrigir.
4. **Masterclass: relatório por webhook** — payload JSON → gerar `.docx` → salvar no Google Drive.
5. **Webhook como "campainha digital"** — URL que escuta dados; autenticação por header `Bearer`.
6. **Pipeline GitHub → Trigger.dev** — iterar no editor empurra pro GitHub, que faz deploy automático.
7. **Error handling em camadas** — log significativo em cada passo, try/catch, retries com backoff, alertas (e-mail/Slack).
8. **O loop humano de debug** — abrir o trace vermelho, copiar o erro, colar na IA, corrigir, redeployar.

---

## Trilha 4 — Construindo Frontends & Apps 🟡 *(Amber)*

> Objetivo: dar cara de produto — transformar a automação invisível em um app de verdade com interface profissional, usuários autenticados, segurança e pagamento recorrente.

### Módulo 4.1 — Modelo Mental & Primeiro App
*Do que roda no fundo ao que o usuário vê — e o primeiro app no ar.*
1. **Background vs visível** — workflow/script (fundo) vs app (interface com que pessoas interagem).
2. **Frontend vs backend** — o que o usuário vê (navegador) vs a lógica no servidor.
3. **Ciclo request/response** — clique → requisição → processamento → resposta → UI atualiza.
4. **Tips de design** — fugir da "cara de IA" (layouts/cores/gradientes genéricos).
5. **Skill de design & referências** — usar a skill de design; clonar/inspirar-se em galerias; usar screenshots de referência.
6. **Linguagem de prompt de design** — descrever layout, componentes e tom visual com precisão; dar feedback específico.
7. **Build do AI Lead Qualifier** — backend no Trigger.dev + frontend no Vercel; do prompt ao app publicado.
8. **Conectar frontend ↔ backend** — chaves/variáveis de ambiente no Vercel; deploy automático a cada push.

### Módulo 4.2 — Produção Real: Auth, Segurança, Pagamentos & Integração
*Login, proteção de dados, receita e ligar um frontend a um workflow n8n.*
1. **Por que autenticar** — app aberto deixa qualquer um gastar seus tokens; proteger uso e dados.
2. **Autenticação com Supabase** — criar projeto, senha do banco vs login, região.
3. **Row-Level Security (RLS)** — regras no próprio banco para isolar dados entre usuários.
4. **Migração SQL & URLs de auth** — rodar o SQL gerado; configurar URL do app e redirect.
5. **Auditoria de segurança** — rotas protegidas, nenhuma chave exposta, segredos só em env vars, RLS ativo.
6. **Stripe: modelo freemium** — tier grátis limitado + tier pago (assinatura) via Checkout.
7. **Produto, chaves & webhook do Stripe** — criar produto recorrente, price ID, chaves, webhook e eventos; tabela de assinaturas.
8. **Frontend para workflow n8n** — trocar o nó de formulário por Webhook + "Respond to Webhook"; ligar via env var no Vercel.
9. **Iteração incremental (recap)** — começar pequeno, publicar cedo e crescer por camadas (design → auth → pagamento).

---

## Estrutura de arquivos do curso (formato v2)

```
vibe-coding/
├── PLANO-DE-CONTEUDO.md          # este documento
├── index.html                    # Landing (jornada + aparência + "continuar de onde parei")
├── assets/
│   ├── learn.css                 # camada de aprendizagem (temas, prefs, controles)
│   └── learn.js                  # window.INEMA (progresso, dúvida, highlight, jornada, export/import)
└── curso/
    ├── trilha1/  index.html + modulo-1-1.html, modulo-1-2.html, modulo-1-3.html
    ├── trilha2/  index.html + modulo-2-1.html, modulo-2-2.html, modulo-2-3.html
    ├── trilha3/  index.html + modulo-3-1.html, modulo-3-2.html
    └── trilha4/  index.html + modulo-4-1.html, modulo-4-2.html
```

Cada página de módulo: nav completo (logo + INEMA.CLUB + 4 botões de trilha + theme toggle), ≥1 diagrama SVG futurista, ≥6 tópicos expansíveis (cada um com "O que é / Por que aprender / Conceitos-chave"), variedade de componentes (grids ✓/✗, timeline, tip boxes, code boxes), manifesto do curso idêntico em todas as páginas e a camada de aprendizagem plugada.
