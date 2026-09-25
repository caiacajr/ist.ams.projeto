<!-- Proposta de solução: Logistica interna de entregas -->

# Table of contents
- [Table of contents](#table-of-contents)
- [Proposta de solução: Logistica interna de entregas](#proposta-de-solução-logistica-interna-de-entregas)
  - [VISÃO GERAL](#visão-geral)
  - [1ª ETAPA](#1ª-etapa)
  - [2ª ETAPA](#2ª-etapa)
  - [3ª ETAPA](#3ª-etapa)
  - [Questoes sobre a proposta de solução](#questoes-sobre-a-proposta-de-solução)
    - [1: o destinatário diz uma lista de alimentos que necessita e se o supermercado tiver algo disso para disponibilizar pronto?](#1-o-destinatário-diz-uma-lista-de-alimentos-que-necessita-e-se-o-supermercado-tiver-algo-disso-para-disponibilizar-pronto)
    - [2: depois em termos daquilo de retornar as packs vazias depois de levantamento](#2-depois-em-termos-daquilo-de-retornar-as-packs-vazias-depois-de-levantamento)
    - [3: o destinatário tem que confirmar que recebeu senão cancela](#3-o-destinatário-tem-que-confirmar-que-recebeu-senão-cancela)
    - [4: se o alimento que está a espera do destinatario nao for recebido, mandar estes alimentos para outro(s) destinatario(s) que precisa(m)](#4-se-o-alimento-que-está-a-espera-do-destinatario-nao-for-recebido-mandar-estes-alimentos-para-outros-destinatarios-que-precisam)
    - [5: como o operador é interno, podiamos faze lo usar o sistema de pedidos e isso integrado no nosso servex](#5-como-o-operador-é-interno-podiamos-faze-lo-usar-o-sistema-de-pedidos-e-isso-integrado-no-nosso-servex)
    - [6: Quando um beneficiario vai fazer um novo pedido, ele pede oque ele quer, ou ele seleciona de uma lista dos alimentos disponiveis no centro de distribuição?](#6-quando-um-beneficiario-vai-fazer-um-novo-pedido-ele-pede-oque-ele-quer-ou-ele-seleciona-de-uma-lista-dos-alimentos-disponiveis-no-centro-de-distribuição)
  - [Avaliação geral e pontos positivos](#avaliação-geral-e-pontos-positivos)
  - [Revisão e pontos críticos a ser esclarecidos](#revisão-e-pontos-críticos-a-ser-esclarecidos)
    - [1: o supermercado não pode simplesmente “carregar alimentos” na Xstation](#1-o-supermercado-não-pode-simplesmente-carregar-alimentos-na-xstation)
    - [2: A Xstation provavelmente não fornece todos os dados alimentares](#2-a-xstation-provavelmente-não-fornece-todos-os-dados-alimentares)
    - [3: Atenção ao tipo de alimentos aceites](#3-atenção-ao-tipo-de-alimentos-aceites)
    - [4: A devolução de PACK vazias também passa pela XMiddle](#4-a-devolução-de-pack-vazias-também-passa-pela-xmiddle)
    - [5: Pedido do beneficiário: lista de necessidades ou lista de disponibilidade?](#5-pedido-do-beneficiário-lista-de-necessidades-ou-lista-de-disponibilidade)
  - [Questões em aberto](#questões-em-aberto)


# Proposta de solução: Logistica interna de entregas

## VISÃO GERAL

A logística de recolha, triagem, armazenamento temporário e entrega é gerida internamente pelo Resgata. O SERVEX inclui uma Distribuidora, ou centro de distribuição, responsável por consolidar os alimentos recebidos, catalogar lotes, preparar cabazes e apoiar o planeamento das missões logísticas internas.

O caminho que os alimentos vão levar terão três etapas:

1. **1ª Etapa:** Do provedor (supermercado) ao centro de distribuição
2. **2ª Etapa:** Recolha, catalogação e registo no centro de distribuição
3. **3ª Etapa:** Do centro de distribuição até aos beneficiarios (organizações sociais)

## 1ª ETAPA

O provedor (supermercado ou outra entidade que provém os alimentos) acondiciona os alimentos em PACK autorizadas e regista no Resgata os dados necessários. Depois deposita a PACK na Xstation indicada pela app. O Resgata reconhece essa PACK como Encomenda de Serviço através da Xmiddle.

Uma equipa logística interna do Resgata executa uma missão logística de recolha, planeada pelo próprio SERVEX, para levantar as Encomendas de Serviço depositadas em Xstations e transportá-las para a Distribuidora. Esta missão não é uma missão da Xoperation-team.

Estes alimentos são levados até um centro_de_distribuição/banco_de_alimentos (Distribuidora)

```text
Provedor
	|
	| deposita PACK na Xstation
	v
Xstation -- Xmiddle --> Encomenda de Serviço
										|
										| recolha pela Equipe1
										v
				  Distribuidora / Centro de distribuição
```

## 2ª ETAPA

Na Distribuidora ocorre um processo de receção, verificação e catalogação. Este processo usa dados declarados pelo provedor, dados operacionais recebidos do XSYS quando autorizados, e verificações próprias da equipa do Resgata.

Essa catalogação é importante por diversos motivos:

- Verifica o estado do alimento
- Durante uma missão de entrega, vamos priorizar levar alimentos com prazo de validade mais perto.
- Saber o tamanho também é importante para missões de entrega porque uma van/camião têm espaço limitado
- Entre outros...

A Distribuidora identifica alimentos não aptos e aciona o procedimento de descarte aplicável, respeitando regras legais, sanitárias e operacionais externas.

```text
Receção na Distribuidora
		  |
		  v
 Verificação e catalogação
		  |
		  +--> Apto --> Stock disponível para pedidos
		  |
		  +--> Não apto --> Descarte
```

## 3ª ETAPA

Uma organização social (beneficiário) abre a app "Resgata" e faz um novo pedido.

Por meio de uma missao, uma equipe (Equipe2) leva diversos pedidos até aos beneficiarios (mais especificamente em xstations perto dos beneficiarios).

Um beneficiario que está a espera de um pedido consegue acompanhar o estado deste pedido em tempo real, e quando este está disponível para levantamento o beneficiario consegue resgata-lo na respetiva xstation atraves de um codigo.

Caso o prazo de levantamento se esgotar ou o levantamento for cancelado pelo beneficiario, este pedido não poderá ser mais resgatado pelo beneficiário.

Este pedido será tratado pelo nosso sistema da mesma forma como alimentos doados o são. Ou seja, volta para etapa 1 e fica a espera da equipe1 resgatá-lo e leva-lo para a distribuidora.

Caso, neste interino, o alimento se torne inapto para consumo, ainda assim o pedido será tratado da mesma forma, e o alimento inapto será descartado pela distribuidora na etapa 2.

```text
Beneficiário faz pedido
	    |
	    v
Pedido preparado na Distribuidora
	    |
	    | missão da Equipe2
	    v
Xstation próxima do beneficiário
	    |
	    +--> Levantamento com código --> Pedido entregue
	    |
	    +--> Cancelamento ou prazo expirado
				 |
				 v
		  Regresso à Distribuidora
			  (Etapa 1 e 2)
```

## Questoes sobre a proposta de solução

### 1: o destinatário diz uma lista de alimentos que necessita e se o supermercado tiver algo disso para disponibilizar pronto?

Não exatamente.

A primeira parte da questão "destinatário diz uma lista de alimentos que precisa" ainda está em discussão, e posteriormente pode mudar para algo "destinatário escolhe alimentos disponíveis".

A segunda parte da questão "o supermecado vê esse pedido e disponibiliza os alimentos para isso" não é a forma proposta com a qual os provedores interagem com o sistema. Eles apenas disponibilizam alimentos que desejarem doar, sem considerar nenhum pedido específico de um beneficiário.

### 2: depois em termos daquilo de retornar as packs vazias depois de levantamento

Relembremos que utilizar de Xoperations para recolha de caixas vazias está fora do nosso poder.

Além disso, no universo de UoD, não somos obrigados a devolver as caixas vazias.

Entretanto, é possível que ao estabelecer uma política que incentiva a devolução destas packs se torne um ponto valorizado.

**Proposta de uma política para o incentivo de devoluções de packs vazias:**

- Quem têm as packs vazias no nosso sistema? R: Os beneficiários
- Uma solução simples então seria estabelecer qualquer incentivo para que os beneficiários retornem estas packs, sem precisar de uma equipe interna para o faze-lo.
- Podemos então estipular um prazo: As caixas utilizadas por um pedido, devem ser entregues em até duas semanas depois da recolha deste pedido.
- Caso contrário, este beneficiário estará bloqueado de fazer novos pedidos até normalizar a situação

### 3: o destinatário tem que confirmar que recebeu senão cancela

- O destinatário não precisa explicitamente ir na app e confirmar que recebeu o pedido. Como a recolha do pedido necessita de um código para levantamento, quando o nosso sistema (com ligação ao xmiddle) receber a informação de que aquele pedido foi recolhido na xstation, podemos deduzir que o destinatário "confirmou" que recebeu o pedido.
- Acerca do cancelamento, existem duas formas com que um pedido a espera de recolha possa ser cancelado:
	1. 1º o beneficiario que cancelou: Esta encomenda não estará mais disponivel para levantamento, e será tratado pelo nosso sistema da mesma forma como alimentos doados o são. Ou seja, volta para etapa 1 e fica a espera da equipe1 resgatá-lo e leva-lo para a distribuidora.
	2. 2º prazo de recolha estorou: A forma como tratamos este caso é o mesmo que o anterior.
- Repare que nenhuma comida deve estragar dentro do prazo de escolha por definição.

### 4: se o alimento que está a espera do destinatario nao for recebido, mandar estes alimentos para outro(s) destinatario(s) que precisa(m)

Exatamente. Existe na verdade uma etapa intermediaria, que seria levar estes alimentos de volta para a distribuidora.

### 5: como o operador é interno, podiamos faze lo usar o sistema de pedidos e isso integrado no nosso servex

Repare que eventualmente haverá uma equipe que calcula a logistica e as missões de entrega e recolha. Os operadores em si só precisam de saber quais xstations entregar/recolher alimentos

### 6: Quando um beneficiario vai fazer um novo pedido, ele pede oque ele quer, ou ele seleciona de uma lista dos alimentos disponiveis no centro de distribuição?

Esta pergunta ainda está em aberto, entretanto, como o nosso sistema modela um missão de caridade de alimentos, talvez faça mais sentido selecionar de uma lista de alimentos disponíveis, ou então uma mistura de ambos.

## Avaliação geral e pontos positivos

Esta primeira avaliação foi feita com auxilio da IA "DizAI":

1. A ideia de criar uma Distribuidora / Centro de Distribuição / Banco de Alimentos interno ao Resgata é coerente. Ela resolve alguns problemas que a proposta anterior deixava em aberto:
	 - permite consolidar alimentos de vários supermercados;
	 - permite verificar melhor o estado dos alimentos;
	 - permite preparar pedidos mais adequados às organizações sociais;
	 - permite priorizar alimentos por prazo de validade;
	 - permite gerir falhas de levantamento;
	 - permite separar a interação dos supermercados da interação dos beneficiários.
2. o centro de distribuição melhora a viabilidade

A existência da Distribuidora torna a proposta mais realista em alguns aspetos.

Na versão anterior, se um supermercado disponibilizasse alimentos e uma organização social não os levantasse a tempo, o sistema precisava rapidamente encontrar outro destinatário. Isso podia ser difícil.

Com o centro de distribuição, vocês ganham uma etapa intermédia onde podem:

- reagrupar alimentos;
- montar cabazes;
- verificar qualidade;
- decidir prioridades;
- preparar rotas;
- tratar cancelamentos;
- evitar que cada supermercado tenha de conhecer diretamente as necessidades dos beneficiários.

Portanto, a mudança é positiva.

> **IMPORTANTE:** No entanto, ela muda a natureza do Resgata: ele deixa de ser apenas um intermediário digital e passa a ser um SERVEX com operação física interna relevante.

## Revisão e pontos críticos a ser esclarecidos

A análise crítica abaixo também foi feita com auxilio da IA "DizAI".

### 1: o supermercado não pode simplesmente “carregar alimentos” na Xstation

**Problema:**

A Xstation não recebe genericamente “alimentos”. Ela recebe objetos, reconhece PACK, e uma PACK com conteúdo pode tornar-se uma Encomenda de Serviço se for reconhecida/acompanhada por um SERVEX.

**Solução:**

O provedor acondiciona os alimentos em PACK autorizadas e regista no Resgata os dados necessários. Depois deposita a PACK na Xstation indicada. O Resgata reconhece essa PACK como Encomenda de Serviço através da Xmiddle.

Ou seja, o objeto operacional do XSYS não é “alimento solto”, mas uma PACK com conteúdo, tratada como Encomenda de Serviço do Resgata.

### 2: A Xstation provavelmente não fornece todos os dados alimentares

**Problema:**

A Xstation tem sensores e pode reconhecer se algo é uma PACK, se está vazia ou se tem conteúdo. Mas não devem assumir que a Xstation sabe automaticamente que dentro da PACK há “arroz”, “feijão”, “massa”, “bolachas” ou que consegue determinar a validade alimentar.

**Solução:**

A catalogação usa dados declarados pelo provedor, dados físicos ou técnicos disponibilizados pelo XSYS quando autorizados, e verificação própria realizada pela Distribuidora.

Ou seja, a validade, categoria alimentar e aptidão para consumo devem ser responsabilidade do provedor e da Distribuidora Resgata, não da Xstation.

**Pergunta:**

Será que o provedor precisa ter essa responsabilidade se os alimentos serão tratados pela distribuidora de qualquer das formas?

### 3: Atenção ao tipo de alimentos aceites

**Problema:**

Com o centro de distribuição, os alimentos agora passam por mais etapas. Isto aumenta o tempo total de circulação.

**Solução:**

Manter a seguinte política de aceitação clara: O Resgata só aceita alimentos cujo prazo e condições de conservação sejam compatíveis com todo o ciclo previsto de recolha, triagem, armazenamento, entrega e levantamento. Caso contrário, o alimento ou não é aceito na Xstation ou é descartado pela Distribuidora.

### 4: A devolução de PACK vazias também passa pela XMiddle

A Xstation recebe o objeto aceite como PACK vazia, que encaminha para o compartimento respetivo da Xstation-pack;

**Problema:**

Quando o beneficiário devolve a PACK vazia, a interação ocorre via Xstation/Xmiddle, e o Resgata só deve receber os eventos ou informação que lhe forem autorizados. O enunciado não deixa claro se o Resgata tem acesso ao evento de devolução da PACK vazia, tornando inviável a implementação de uma política de incentivo à devolução de PACK vazias.

**Solução:** Aberto para discussões.

### 5: Pedido do beneficiário: lista de necessidades ou lista de disponibilidade?

**Problema:**

A estratégia de escolha entre uma lista de necessidades e uma lista de disponibilidade é uma decisão arquitetural relevante, porque afeta o processo, os dados, a experiência dos beneficiários e a lógica de atribuição.

**Solução:**

- **Alternativa A — beneficiário pede o que precisa**
	- **Vantagem:**
		- maior alinhamento com necessidades reais;
		- mais valor social;
		- melhor para cozinhas comunitárias que planeiam refeições.
	- **Desvantagem:**
		- pode gerar muitos pedidos impossíveis;
		- exige mais lógica de matching.

- **Alternativa B — beneficiário escolhe do stock disponível**
	- **Vantagem:**
		- mais simples;
		- evita prometer algo que não existe;
		- facilita a operação logística.
	- **Desvantagem:**
		- menos centrado nas necessidades reais;
		- pode favorecer quem entra primeiro na app;
		- pode dificultar planeamento de refeições.

- **Alternativa C — modelo misto**

## Questões em aberto

Segundo a análise da IA, existem algumas questões em aberto, que ao serem respondidas fortalecem a proposta de solução:

- O beneficiário declara necessidades, escolhe stock disponível ou usa um modelo misto?
- Quem fornece as PACK ao supermercado/provedor? o Provedor resgata as PACKs no Xstation ou o Resgata fornece as PACKs ao provedor de antemão?
- Quanto tempo uma PACK com alimentos pode ficar numa Xstation antes de recolha?
- Que critérios determinam se um alimento não levantado pode ser reintroduzido no fluxo?
- Como o Resgata trata beneficiários que não devolvem PACK?
- Que informação alimentar é declarada pelo provedor e que informação é verificada pela Distribuidora?
- Que eventos da Xmiddle são suficientes para confirmar depósito, levantamento e devolução?
- Como o Resgata age se a Xstation escolhida estiver indisponível, cheia ou não autorizada?
