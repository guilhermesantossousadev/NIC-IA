Sim. Pesquisando o que está sendo feito em 2025–2026, eu faria uma mudança importante: **o CAP não deveria começar tentando construir o “cérebro da NIC”**. Primeiro vocês precisam descobrir **onde a IA realmente dói no trabalho da empresa**, quais conhecimentos são repetidos, onde há retrabalho e quais fluxos têm valor suficiente para justificar uma camada corporativa de contexto.

Isso combina bastante com o que está aparecendo no mercado. A Anthropic trata *context engineering* como evolução natural de *prompt engineering*: o problema passa a ser escolher o menor conjunto de informações de alto valor para produzir o comportamento desejado. :chatgpt-content-reference{index="0"} O Gartner, em webinar de setembro de 2026, vai ainda mais perto da ideia de vocês: descreve uma **enterprise context layer** que conecta conhecimento, políticas e lógica de negócio à execução de IA, e destaca inclusive a captura de processos e conhecimento institucional que hoje não estão documentados. :chatgpt-content-reference{index="1"}

Então eu reorganizaria o projeto inteiro desta maneira.

# 1. Não começar pela solução. Começar pelas dores

Hoje vocês já estão pensando em:

> Obsidian → MCP → Skills → RAG → memória → IA.

Eu inverteria:

> **Pessoas → trabalho → dores → conhecimento → casos de uso → experimentos → arquitetura → tecnologia.**

Antes de escrever uma linha do NIC AI Context Hub, faria uma **AI Discovery** dentro da NIC.

E evitaria simplesmente perguntar:

> "Como você usa IA?"

É uma pergunta ampla e normalmente gera respostas superficiais.

Perguntaria sobre **trabalho real**.

### Entrevista de 20–30 minutos

Escolham pessoas de áreas e níveis diferentes e perguntem coisas como:

**Trabalho**

> O que você fez ontem?

> Qual tarefa tomou mais tempo?

> Qual tarefa você faz repetidamente?

> Em que tarefa você normalmente precisa pedir ajuda?

> Qual tarefa exige conhecimento que só algumas pessoas possuem?

**IA**

> Em quais dessas tarefas você usou IA?

> Mostra um exemplo real?

> O que você precisou explicar para a IA antes dela entender?

> Quantas vezes precisou corrigir?

> O que ela fez errado?

> O problema foi falta de informação, instrução ruim ou incapacidade da IA?

**Conhecimento**

> Quando você não sabe alguma coisa, onde procura?

> Existe documentação?

> Você pergunta para alguém?

> Quem é a pessoa que "sempre sabe" sobre isso?

> Existe alguma coisa importante que só está na cabeça das pessoas?

**Repetição**

Essa eu considero especialmente importante:

> **O que você explicou para uma IA esta semana que provavelmente outra pessoa da NIC também já explicou?**

Isso começa a revelar o conhecimento que deveria virar contexto compartilhado.

---

# 2. Criaria um "Diário de IA" por 1–2 semanas

Entrevista captura percepção.

Eu também quero comportamento real.

Durante uma ou duas semanas, algumas pessoas registrariam usos relevantes da IA.

Algo simples:

| Campo | Exemplo |
|---|---|
| Área | SAP |
| Tarefa | Criar alteração ABAP |
| Ferramenta | ChatGPT |
| Tempo sem IA estimado | 60 min |
| Tempo com IA | 25 min |
| Precisou fornecer contexto? | Sim |
| Qual? | padrão cliente + código existente |
| Quantas correções? | 3 |
| Funcionou? | Parcial |
| Principal problema | desconhecia padrão do cliente |
| Informação existia onde? | projeto + conhecimento do dev |
| Seria reutilizável? | Sim |

Não precisa capturar conteúdo confidencial da conversa nessa fase; vocês querem primeiro entender **padrões de uso**.

Depois de duas semanas talvez apareça:

```text
87 usos de IA

        ↓

31 tiveram problema de contexto

        ↓

18 precisaram explicar
padrões do cliente

        ↓

12 procuraram documentação

        ↓

9 perguntaram para outra pessoa

        ↓

7 resolveram algo que
outra pessoa já havia resolvido
```

Aí vocês começam a ter evidência para o CAP.

---

# 3. Criaria um "Mapa de Fricção da IA"

Cada problema encontrado entraria em categorias.

Eu começaria com:

```text
FRICTION TAXONOMY

01 — Falta de contexto
02 — Contexto desatualizado
03 — Contexto difícil de encontrar
04 — Conhecimento não documentado
05 — Prompt/instrução ruim
06 — Resposta inconsistente
07 — Alucinação
08 — Falta de integração
09 — Limitação da ferramenta/modelo
10 — Segurança/permissão
11 — Custo/tokens
12 — Retrabalho humano
13 — Falta de padrão
14 — Conhecimento duplicado
15 — Contexto excessivo
```

Isso é extremamente importante.

Talvez vocês descubram que **token não é o problema principal**.

Pode ser que o maior problema seja:

> "As pessoas gastam 15 minutos explicando o projeto para a IA."

ou:

> "A IA gera algo tecnicamente correto, mas fora do padrão do cliente."

A direção do projeto deveria surgir dos dados.

---

# 4. Faria um inventário de conhecimento

Depois das entrevistas, vocês provavelmente descobrirão coisas como:

```text
"Fulano sabe isso."

"Isso está naquele PDF."

"Tem no Teams."

"Tem no código."

"Está no SharePoint."

"Pergunta para a Ju."

"Eu tenho um prompt salvo."

"Tem uma conversa antiga com IA."

"Tem uma documentação, mas está desatualizada."
```

Isso é ouro para o CAP.

Criaria um **Knowledge Map**:

```text
                    CONHECIMENTO NIC

                         │
       ┌─────────────────┼─────────────────┐
       ▼                 ▼                 ▼
   EXPLÍCITO          IMPLÍCITO          GERADO
       │                 │                 │
 documentos          pessoas           chats IA
 código              experiência       soluções
 Wiki                 práticas          prompts
 tickets              atalhos           descobertas
```

A parte mais interessante talvez seja justamente o **conhecimento implícito**.

O Gartner menciona especificamente capturar processos não documentados e conhecimento institucional como parte do desafio de contexto corporativo. :chatgpt-content-reference{index="2"}

---

# 5. Criaria um "Knowledge Gap Map"

Agora cruzem:

**O que a IA precisava saber**

versus

**Onde essa informação estava.**

Por exemplo:

| Conhecimento necessário | Existe? | Onde? | Atualizado? | IA acessa? |
|---|---|---|---|---|
| Padrão ABAP NIC | Sim | documento | Sim | Não |
| Padrão Cliente A | Sim | projeto | Parcial | Não |
| Regra funcional X | Sim | consultor | — | Não |
| Erro SAP Y | Sim | cabeça do dev | — | Não |
| Arquitetura projeto | Sim | Git | Sim | Parcial |
| Solução incidente Z | Sim | Teams | Sim | Não |

Isso mostra exatamente onde existe oportunidade.

---

# 6. Criaria um ranking de casos de uso — mas não por "ideia legal"

Usaria quatro dimensões internamente para seleção, sem precisar transformar isso numa nota pública:

```text
FREQUÊNCIA
Quantas vezes acontece?

FRICÇÃO
Quanto trabalho/desperdício gera?

CONTEXT DEPENDENCY
Quanto conhecimento da NIC é necessário?

MEASURABILITY
Conseguimos medir se melhorou?
```

E acrescentaria **risco** como filtro eliminatório.

Por exemplo, vocês podem descobrir três casos:

```text
A — Criar código ABAP seguindo padrão do cliente

B — Encontrar solução de incidente já resolvido

C — Gerar documentação técnica
```

Esses são experimentos muito melhores do que simplesmente:

> "Vamos testar RAG."

---

# 7. Separaria três problemas que hoje estão misturados

Essa mudança é importante.

### Prompt Engineering

**Como pedir?**

```text
"Analise essa classe e..."
```

### Context Engineering

**O que a IA precisa saber?**

```text
cliente
projeto
arquitetura
código
padrões
decisões
histórico
```

### Knowledge Engineering

**Como a empresa organiza aquilo que sabe?**

```text
Quem criou?
Quem validou?
Está atualizado?
É global?
É daquele cliente?
Quem pode acessar?
Qual versão?
```

Seu CAP começou em **Prompt Engineering**.

Pelas ideias que vocês levantaram, ele está naturalmente caminhando para **Context Engineering + Knowledge Engineering**.

Isso deixa o tema muito mais interessante.

---

# 8. A ideia de "um cérebro" eu mudaria conceitualmente

Eu evitaria:

> **Um cérebro central da NIC.**

Porque dá impressão de colocar tudo dentro de um modelo.

Eu usaria:

> **NIC Context Layer**

ou:

> **NIC Knowledge & Context Platform**

O modelo continua sendo substituível.

```text
                 FERRAMENTAS

 ChatGPT     Claude     Copilot     CLI
     \          |          |        /
      \         |          |       /
       ───────── NIC AI ─────────
                 │
          CONTEXT LAYER
                 │
        ┌────────┼────────┐
        ▼        ▼        ▼
     Pessoas   Projetos Clientes
        │        │        │
        └────────┼────────┘
                 ▼
          KNOWLEDGE GRAPH
                 │
       ┌─────────┼─────────┐
       ▼         ▼         ▼
     Docs       Git       SAP
```

A IA vira apenas **consumidora do conhecimento da NIC**.

---

# 9. Context Router vira uma peça muito importante

A Anthropic recomenda pensar contexto como recurso finito e buscar o menor conjunto de tokens de alto sinal necessário para obter o comportamento desejado. :chatgpt-content-reference{index="3"}

Então não faria:

```text
PERGUNTA
   ↓
TODO CONHECIMENTO NIC
   ↓
LLM
```

Faria:

```text
"Preciso alterar programa Z
do Cliente A."

        ↓

Context Router

        ↓

identifica:

Cliente A
Projeto SAP X
ABAP
Programa Z

        ↓

recupera:

padrão NIC
+
padrão Cliente A
+
arquitetura Projeto X
+
documentação Programa Z
+
3 decisões relacionadas
+
2 problemas anteriores

        ↓

CONTEXT PACKAGE

        ↓

LLM
```

Esse conceito de **Context Package** eu acrescentaria formalmente ao projeto.

---

# 10. O RAG não resolve sozinho

Isso também aparece nas referências atuais.

O Google destaca que a qualidade da recuperação é crítica: se o sistema recuperar informação irrelevante, a resposta pode estar "fundamentada" em material errado ou fora do contexto. Também cita métricas como *groundedness*, qualidade de resposta e cumprimento de instruções para avaliar sistemas desse tipo. :chatgpt-content-reference{index="4"}

Então vocês precisam avaliar duas coisas separadamente:

```text
RETRIEVAL

A IA encontrou
a informação certa?

        ↓

GENERATION

Usou essa informação
corretamente?
```

Essa separação é excelente para o CAP.

---

# 11. Eu acrescentaria proveniência

Toda informação entregue para a IA deveria carregar algo como:

```yaml
source: SAP_CLIENT_A_GUIDELINES.md
owner: SAP Architecture
scope: client-a
version: 4
updated: 2026-08-17
status: approved
confidence: authoritative
```

E idealmente a resposta conseguir dizer:

> "Estou seguindo o padrão definido em X."

Isso aumenta bastante a auditabilidade.

A arquitetura de Knowledge Retrieval da OpenAI também enfatiza respostas fundamentadas nos dados da organização, com citações e avaliações de confiabilidade. :chatgpt-content-reference{index="5"}

---

# 12. Introduziria "Knowledge Lifecycle"

Isso está faltando na ideia original.

Conhecimento envelhece.

Então:

```text
CAPTURADO
   ↓
PROPOSTO
   ↓
VALIDADO
   ↓
PUBLICADO
   ↓
USADO PELA IA
   ↓
MONITORADO
   ↓
ATUALIZADO
   ↓
DEPRECADO
```

Imagine uma regra SAP de 2024 que mudou em 2026.

Um RAG pode recuperá-la perfeitamente.

E ainda assim produzir a resposta errada.

Por isso **freshness** deveria ser requisito.

---

# 13. Acrescentaria feedback durante o uso

Depois que o sistema estiver funcionando:

```text
IA responde

    ↓

👍 resolveu
👎 incorreto
⚠ desatualizado
📚 contexto insuficiente

    ↓

telemetria

    ↓

Knowledge Gap

    ↓

melhoria da base
```

Isso transforma o NIC AI em algo que aprende **organizacionalmente**, sem necessariamente treinar os pesos do modelo.

Esse conceito está bastante alinhado com o Work Trend Index 2026 da Microsoft: o relatório descreve organizações mais maduras como *learning systems*, nas quais os resultados e aprendizados do uso de IA são capturados, compartilhados e incorporados à forma de trabalhar. O mesmo estudo encontrou associação bem maior entre fatores organizacionais e impacto percebido de IA do que fatores individuais. :chatgpt-content-reference{index="6"}

---

# 14. Skills teriam outro papel

Skill não seria memória.

Seria **procedimento**.

Por exemplo:

```text
KNOWLEDGE

"O Cliente X utiliza esse
padrão de desenvolvimento."

versus

SKILL

"Quando fizer code review
para Cliente X:

1. leia arquitetura
2. verifique naming
3. rode testes
4. verifique segurança
5. gere relatório"
```

Então:

> **Knowledge = o que sabemos.**

> **Skill = como fazemos.**

Essa distinção deixa a arquitetura muito melhor.

---

# 15. MCP também não seria o cérebro

MCP seria uma **interface de acesso**.

```text
                NIC CONTEXT PLATFORM

                        │

       ┌────────────────┼────────────────┐
       │                │                │
      MCP              API            Plugin
       │                │                │
       ▼                ▼                ▼
   Claude/CLI        Sistemas        ChatGPT/etc.
```

Inclusive o MCP vem ganhando recursos voltados ao ambiente corporativo; em junho de 2026, o projeto anunciou autorização gerenciada pela empresa para provisionar acesso a servidores MCP via provedor de identidade, justamente atacando o problema de controle centralizado de acesso. :chatgpt-content-reference{index="7"}

Isso reforça que **identidade e autorização** deveriam aparecer desde o início da arquitetura.

---

# 16. Eu criaria quatro métricas principais

Em vez de focar somente em token.

### Quality

```text
correto?
completo?
segue padrão?
passa testes?
```

### Effort

```text
tempo
correções
prompts
intervenções humanas
```

### Context

```text
documentos recuperados
precision
recall
context size
context relevance
```

### Economics

```text
input tokens
output tokens
custo
tempo economizado
```

Então vocês conseguem descobrir situações interessantes.

Por exemplo:

```text
SEM NIC CONTEXT

3.000 tokens
6 correções
22 minutos


COM NIC CONTEXT

7.000 tokens
1 correção
7 minutos
```

Nesse cenário gastar mais tokens foi **melhor economicamente**.

Por isso eu retiraria "reduzir tokens" como objetivo principal.

Colocaria:

> **maximizar valor por contexto utilizado.**

---

# 17. Eu deixaria inglês × português como experimento pequeno

Não eliminaria.

Mas seria algo como:

**EXP-003 — Language impact on prompt efficiency**

Testar:

```text
Português simples
Português estruturado
Inglês simples
Inglês estruturado
```

Mesmo modelo, temperatura/configuração, tarefa e contexto.

Medir:

```text
tokens
qualidade
tempo humano
erros
facilidade percebida
```

Aí vocês descobrem se existe diferença relevante **para a realidade da NIC**.

---

# 18. NotebookLM viraria benchmark

Não componente.

Vocês podem perguntar:

> "Será que precisamos construir isso?"

Testem a mesma documentação em:

**NotebookLM → ChatGPT/knowledge retrieval → RAG próprio → NIC Context.**

O resultado pode mostrar que uma ferramenta pronta resolve 70% do problema.

Isso também é uma conclusão válida para um CAP.

---

# 19. Criaria um experimento muito bom: "novo funcionário"

Esse eu acrescentaria com certeza.

Imaginem alguém entrando hoje na NIC.

Perguntem:

> Quanto conhecimento precisa adquirir para contribuir no Projeto X?

Depois criem:

```text
Novo colaborador
      ↓
NIC AI
      ↓
"Explique o Projeto X."
      ↓
arquitetura
decisões
padrões
glossário
problemas conhecidos
ambiente
primeiros passos
```

Depois:

> "Preciso implementar X."

O sistema recupera tudo necessário.

Isso cria um caso de uso forte para **onboarding + preservação de conhecimento**.

---

# 20. E tem outro caso muito forte: "já resolvemos isso?"

Eu colocaria como candidato sério para o primeiro MVP.

Usuário pergunta:

> "Estou recebendo esse erro no SAP."

NIC AI:

```text
Busca:

tickets
documentação
problemas anteriores
commits
ADRs
soluções
```

E responde:

> "Esse problema já ocorreu no Projeto X em julho. A causa foi Y. A solução utilizada foi Z."

Esse tipo de caso demonstra imediatamente o valor de conhecimento organizacional.

---

# A estrutura final que eu adotaria

Eu transformaria o CAP em **cinco fases**, e só a quarta envolveria construir bastante coisa.

```text
FASE 1
DISCOVERY
│
├─ entrevistas
├─ diário de IA
├─ shadowing
├─ inventário de ferramentas
├─ mapa de conhecimento
└─ mapa de dores

        ↓

FASE 2
OPPORTUNITY MAPPING
│
├─ classificar dores
├─ encontrar conhecimento repetido
├─ identificar knowledge gaps
├─ selecionar casos de uso
└─ definir baseline

        ↓

FASE 3
EXPERIMENTATION
│
├─ prompt
├─ contexto
├─ idioma
├─ ferramentas
├─ retrieval
└─ métricas

        ↓

FASE 4
NIC CONTEXT MVP
│
├─ Knowledge Base
├─ Context Router
├─ Retrieval
├─ Context Package
├─ Skills
├─ permissões
├─ proveniência
└─ feedback

        ↓

FASE 5
VALIDATION
│
├─ A/B tests
├─ qualidade
├─ tempo
├─ tokens
├─ custo
├─ correções
└─ satisfação
```

E só depois:

```text
FUTURE

├─ branches de contexto
├─ knowledge graph
├─ integração SAP profunda
├─ agentes
├─ automação
├─ fine-tuning
└─ modelo especializado
```

## A tese que eu tentaria provar

Eu mudaria a narrativa do projeto para algo assim:

> **O problema do uso corporativo de IA não é somente ensinar colaboradores a escrever prompts melhores. É garantir que a IA certa receba o conhecimento certo, no momento certo, para a pessoa certa e com o menor contexto necessário.**

Isso está muito próximo da direção atual da indústria: a Anthropic fala explicitamente em selecionar contexto de alto sinal; o Gartner está tratando uma camada empresarial de contexto como infraestrutura para sistemas de IA; Google destaca que recuperação relevante e avaliação são fundamentais; e a pesquisa da Microsoft de 2026 aponta para empresas capturando e compartilhando aprendizados como parte de sistemas organizacionais de IA. :chatgpt-content-reference{index="8"}

Eu, portanto, **não começaria pelo Obsidian nem pelo MCP agora**. O próximo entregável que faria com vocês seria um **Discovery Kit do CAP**: roteiro de entrevista + formulário/diário de uso de IA + taxonomia de dores + matriz de oportunidades + planilha de métricas + critérios para escolher os 2–3 primeiros casos de uso. Depois de coletar isso na NIC por uma ou duas semanas, a arquitetura v1 deixa de ser uma hipótese nossa e passa a nascer dos problemas reais encontrados.