# CAP — Uso Estratégico e Compartilhado de Inteligência Artificial na NIC

## 1. Mudança de direcionamento do CAP

A proposta inicial do CAP estava focada em descobrir **qual seria a melhor forma de utilizar Inteligência Artificial** dentro da empresa.

A nova proposta é mudar o foco para uma questão mais prática:

**Como estamos utilizando Inteligência Artificial atualmente e como podemos tornar esse uso mais eficiente, econômico, contextualizado e compartilhado dentro da NIC?**

A ideia deixa de ser apenas estudar possibilidades de IA e passa a analisar o uso real da tecnologia na empresa, identificando problemas, boas práticas e oportunidades de melhoria.

---

## 2. Problema principal

Um dos principais problemas percebidos no uso de IA não está necessariamente na capacidade dos modelos, mas na **falta de contexto fornecido a eles**.

Muitas vezes, cada colaborador utiliza uma IA de maneira isolada. Com isso:

- conhecimentos descobertos por uma pessoa não chegam às outras;
- soluções para problemas já resolvidos precisam ser descobertas novamente;
- padrões de desenvolvimento precisam ser explicados repetidamente;
- informações sobre clientes ficam distribuídas em diferentes conversas;
- decisões tomadas anteriormente podem se perder;
- cada nova conversa com uma IA pode começar praticamente do zero.

A hipótese a ser explorada é:

> **Quanto mais contexto relevante e estruturado uma IA possui sobre a empresa, seus projetos, clientes, padrões e problemas anteriores, melhor tende a ser sua capacidade de auxiliar os colaboradores.**

---

## 3. Eficiência de prompts e consumo de tokens

Uma das linhas de estudo do CAP será analisar como a construção dos prompts influencia o consumo de tokens e a qualidade das respostas.

### Experimentos

Testar diferentes formas de escrever a mesma solicitação:

- prompts simples versus prompts detalhados;
- português versus inglês;
- prompts estruturados versus texto livre;
- contexto completo versus contexto mínimo;
- instruções reutilizáveis versus instruções repetidas em cada prompt.

O consumo poderá ser analisado utilizando ferramentas de tokenização da OpenAI ou ferramentas equivalentes.

O objetivo não deve ser simplesmente **usar menos tokens**, mas encontrar uma relação adequada entre:

**custo + quantidade de contexto + qualidade da resposta + facilidade de uso.**

### Inglês versus português

Prompts em inglês podem apresentar diferenças de tokenização e, dependendo do modelo e da tarefa, diferenças de comportamento.

Entretanto, existe também uma questão de usabilidade.

Obrigar colaboradores que não possuem domínio de inglês a escrever prompts em inglês pode tornar a utilização da IA menos acessível e aumentar a complexidade do processo.

Portanto, o CAP pode avaliar se a possível economia ou melhoria justifica essa dificuldade.

---

## 4. Comparação entre interfaces

Outra análise proposta é verificar o consumo e a eficiência da IA dependendo da interface utilizada.

Exemplos:

- aplicação Desktop;
- aplicação Web;
- CLI;
- APIs;
- agentes.

A hipótese levantada é que determinadas interfaces podem enviar mais contexto automaticamente, aumentando o consumo de tokens.

O objetivo será medir isso de forma controlada antes de estabelecer uma conclusão.

---

## 5. Contexto como parte da engenharia de IA

Uma das principais linhas do projeto será estudar **engenharia de contexto**, e não somente engenharia de prompt.

Um prompt pode ser muito bem escrito, mas produzir resultados ruins caso o modelo não tenha informações suficientes sobre:

- a NIC;
- o projeto;
- o cliente;
- decisões anteriores;
- arquitetura utilizada;
- padrões de código;
- problemas já encontrados;
- soluções adotadas;
- documentação;
- regras de negócio.

Isso leva à ideia de criar uma infraestrutura capaz de disponibilizar esse conhecimento para diferentes ferramentas de IA.

---

## 6. "Cérebro compartilhado" da NIC

Uma das propostas centrais do CAP é estudar a criação de uma espécie de **cérebro compartilhado de IA da NIC**.

Em vez de cada colaborador possuir uma IA completamente isolada, seria criada uma camada compartilhada de conhecimento.

Esse cérebro poderia armazenar e organizar:

- contexto institucional;
- projetos;
- clientes;
- tecnologias utilizadas;
- padrões de desenvolvimento;
- padrões específicos de cada cliente;
- decisões arquiteturais;
- problemas encontrados;
- soluções utilizadas;
- boas práticas;
- documentação;
- aprendizados;
- ideias;
- procedimentos internos.

A IA utilizada pelo colaborador poderia consultar esse conhecimento quando necessário.

---

## 7. Um cérebro, diferentes ferramentas

A ideia não precisa depender de uma única interface ou modelo.

O objetivo seria construir uma arquitetura na qual diferentes ferramentas possam acessar uma **fonte compartilhada de conhecimento**.

Por exemplo:

**Colaborador → IA utilizada → Plugin/Skill/MCP → Contexto compartilhado da NIC**

Assim, diferentes colaboradores poderiam utilizar ferramentas diferentes enquanto continuam acessando a mesma base institucional.

Isso também reduz a dependência de uma única interface de IA.

---

## 8. Obsidian como base experimental de conhecimento

O Obsidian pode ser estudado como uma das possibilidades para centralizar o conhecimento.

Ele poderia organizar informações utilizando arquivos Markdown e relacionamentos entre documentos.

Exemplo:

```text
NIC Knowledge
│
├── Empresa
│   ├── processos
│   ├── padrões
│   └── infraestrutura
│
├── Clientes
│   ├── Cliente A
│   │   ├── contexto
│   │   ├── padrões
│   │   └── decisões
│   └── Cliente B
│
├── Projetos
│   ├── Projeto X
│   └── Projeto Y
│
├── Problemas
│   ├── problema-001.md
│   └── problema-002.md
│
├── Soluções
│
└── Aprendizados
```

Plugins, Skills ou MCPs poderiam permitir que diferentes agentes consultassem esse conhecimento.

O Obsidian, entretanto, seria uma possibilidade de implementação e não necessariamente uma dependência definitiva da arquitetura.

---

## 9. Plugins e Skills compartilhados

Outra linha importante será estudar a criação de **plugins e skills internos reutilizáveis por toda a NIC**.

Em vez de cada pessoa ensinar repetidamente à IA como determinada tarefa deve ser executada, esse comportamento poderia ser encapsulado.

Exemplos:

- Skill de desenvolvimento;
- Skill de documentação;
- Skill de revisão de código;
- Skill de padrões SAP;
- Skill de criação de testes;
- Skill de análise de requisitos;
- Skill específica para determinado cliente.

Isso permitiria transformar conhecimento individual em capacidade reutilizável pela organização.

---

## 10. Aplicação em SAP

Uma linha específica do CAP será investigar como essa arquitetura poderia ser aplicada aos projetos SAP.

A IA poderia receber contexto sobre:

- padrões ABAP;
- convenções utilizadas pela NIC;
- padrões específicos do cliente;
- documentação funcional;
- documentação técnica;
- regras de negócio;
- erros conhecidos;
- soluções anteriores;
- integrações existentes.

Assim, em vez de simplesmente solicitar:

> "Crie esse código ABAP."

A IA poderia trabalhar sabendo previamente **como aquele cliente e aquele projeto esperam que o código seja desenvolvido**.

---

## 11. Temperatura e comportamento dos modelos

Também poderá ser estudada a influência de parâmetros dos modelos, como **temperatura**, quando disponíveis.

O objetivo será analisar como diferentes configurações se comportam em tarefas como:

- programação;
- documentação;
- brainstorming;
- análise;
- resolução de problemas;
- geração de alternativas.

Isso permitirá avaliar quando é interessante buscar respostas mais determinísticas ou maior diversidade de soluções.

---

## 12. Experimentos com tarefas simples

Antes de testar a arquitetura em problemas grandes, serão realizados experimentos controlados com tarefas simples.

Uma mesma tarefa poderá ser executada utilizando diferentes estratégias de prompt e contexto.

Exemplo:

**Tarefa → Estratégia A → Resultado A**

**Tarefa → Estratégia B → Resultado B**

**Tarefa → Estratégia C → Resultado C**

Os resultados poderão ser comparados considerando:

- quantidade de tokens;
- tempo;
- qualidade;
- quantidade de correções necessárias;
- aderência aos requisitos;
- facilidade de utilização pelo colaborador.

---

## 13. Uso do NotebookLM

O NotebookLM pode ser estudado como ferramenta complementar para trabalhar com grandes conjuntos de documentação.

Possíveis usos:

- estudar documentação;
- compreender projetos;
- gerar resumos;
- criar planos de ação;
- criar planos de implementação;
- relacionar documentos;
- preparar colaboradores para atuar em determinado projeto.

Ele pode fazer parte do estudo comparativo, sem necessariamente ser o núcleo da solução.

---

## 14. Branches de contexto e raciocínio

Outra ideia é experimentar um conceito semelhante a **branches de contexto**.

Durante uma interação longa com IA, o usuário pode seguir determinado caminho e perceber posteriormente que aquela abordagem não era adequada.

Seria interessante permitir algo semelhante ao Git:

```text
Contexto principal
       │
       ├── abordagem A
       │       └── tentativa A1
       │
       └── abordagem B
               └── tentativa B1
```

O usuário poderia experimentar diferentes abordagens sem destruir ou contaminar o contexto original.

Também seria possível retornar a determinado ponto da conversa e continuar por outro caminho.

---

## 15. Modelo especializado no contexto da NIC

Uma possibilidade futura seria estudar uma IA especializada no contexto da empresa.

Entretanto, antes de partir diretamente para treinamento ou fine-tuning de um modelo, o CAP deverá avaliar alternativas como:

- prompts;
- system prompts;
- Skills;
- Plugins;
- MCP;
- RAG;
- bases vetoriais;
- memória compartilhada;
- documentação estruturada.

Somente depois seria possível avaliar se existe necessidade real de treinamento ou fine-tuning.

O objetivo seria chegar a um sistema que compreenda:

**NIC + cliente + projeto + padrões + histórico + documentação + conhecimento acumulado.**

---

# Visão geral da proposta

O CAP pode ser resumido em quatro grandes pilares:

### 1. Eficiência

Entender como prompts, idiomas, interfaces e quantidade de contexto influenciam tokens, custo e qualidade.

### 2. Contexto

Investigar quanto a disponibilidade de contexto melhora o desempenho da IA nas tarefas reais da empresa.

### 3. Compartilhamento

Transformar conhecimentos individuais em conhecimento reutilizável por outros colaboradores através de uma base compartilhada, Plugins, Skills ou MCPs.

### 4. Padronização

Permitir que a IA compreenda os padrões da NIC e dos clientes, reduzindo retrabalho e aumentando a consistência das entregas.

---

# Pergunta central do CAP

**Como a NIC pode estruturar e compartilhar contexto, conhecimento e padrões internos para tornar o uso de Inteligência Artificial mais eficiente, consistente e reutilizável entre seus colaboradores?**

Essa pergunta permite investigar prompts, tokens, contexto, Skills, Plugins, MCP, Obsidian, NotebookLM, SAP e modelos especializados sem transformar o CAP em vários projetos desconectados.

---

# Possível resultado final

O resultado do CAP não precisa ser apenas uma apresentação teórica.

Pode ser desenvolvido um **MVP de uma arquitetura de conhecimento compartilhado para IA dentro da NIC**.

```text
                   NIC AI
                     │
              Context Router
                     │
        ┌────────────┼────────────┐
        │            │            │
     Empresa      Cliente      Projeto
        │            │            │
        └────────────┼────────────┘
                     │
              Knowledge Base
                     │
        ┌────────────┼────────────┐
        │            │            │
      Skills       MCPs        Plugins
        │            │            │
        └────────────┼────────────┘
                     │
               Ferramentas IA
```

Um colaborador poderia iniciar uma tarefa e a IA receber automaticamente somente o contexto necessário para aquele cliente, projeto ou tipo de atividade.

Com isso, o CAP deixa de estudar apenas **"como escrever prompts melhores"** e passa a investigar algo mais amplo:

**como transformar o conhecimento acumulado da NIC em contexto reutilizável por Inteligência Artificial.**