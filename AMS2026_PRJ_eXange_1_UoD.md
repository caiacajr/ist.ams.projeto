# Iniciativa eXange

## Exploração Competitiva Aberta para uma Arquitetura de referência

**AMS 2026/2027 | Projeto eXange - Universo do Discurso e Enunciado do Projeto**

---

## Índice

1. Objetivo e conceitos principais ........................................................ 2  
   1.1 Cenário do XSYS ..................................................................... 2  
   1.2 Objetivos da arquitetura de referência ................................. 2  
   1.3 Entidades principais ............................................................. 2  
   1.4 Objeto, Encomenda e Encomenda de Serviço ....................... 2  
   1.5 Eventos e comandos ............................................................. 2  

2. Máquinas Xstation .......................................................................... 2  
   2.1 Xstation-safe – guarda de Encomendas ................................ 3  
   2.2 Xstation-pick – levantamento de Encomendas ..................... 3  
   2.3 Xstation-pack – disponibilização de PACK vazias ................. 3  
   2.4 Xstation-counter – receção e classificação de objetos ......... 3  
   2.5 Xstation-mng – gestão e controlo ......................................... 3  

3. Plataforma lógica Xmiddle .............................................................. 3  
   3.1 Xmiddle-core ......................................................................... 3  
   3.2 Xmiddle-lex ........................................................................... 3  
   3.3 Xmiddle-smart ...................................................................... 4  

4. Estrutura operacional Xoperation ................................................... 4  
   4.1 Criação de uma missão ......................................................... 4  
   4.2 Realização de uma missão por uma Xoperation-team ......... 4  

5. Serviços SERVEX e referência SAV ................................................. 5  
   5.1 SERVEX – os serviços que usam o XSYS ............................... 5  
   5.2 SAV – um SERVEX de referência ........................................... 5  

6. Abertura do UoD e âmbito ............................................................. 6  
   6.1 Notas de âmbito ................................................................... 6  
   6.2 Referências de enquadramento ........................................... 6  

**Anexo – Dicionário de designações, siglas e conceitos do XSYS** ..... 7  
A. Entidades, sistemas e conceitos do domínio ............................... 7  
B. Conceitos das máquinas Xstation .................................................. 7  
C. Conceitos da plataforma Xmiddle ................................................. 8  
D. Estrutura operacional e planos ..................................................... 8  
E. Serviço de referência SAV ............................................................. 8  
F. Organizações, normas e referências externas ............................... 8  

---

## 1 Objetivo e conceitos principais

A UNECE (Comissão Económica das Nações Unidas para a Europa) pretende promover a conceção da iniciativa internacional eXange, para suportar a troca de Encomendas através de embalagens normalizadas e reutilizáveis.

Esta iniciativa deverá corporizar-se no sistema XSYS, para o qual se pretende desenvolver uma arquitetura de referência aberta.

O XSYS é por isso o âmbito do presente cenário e desafio, cuja arquitetura de referência deve representar o conjunto mínimo de conceitos, responsabilidades, interfaces e comportamentos que todas as realizações devem respeitar.

### 1.1 Cenário do XSYS

O XSYS é concebido como um sistema composto por máquinas físicas Xstation, plataformas lógicas Xmiddle, e por uma estrutura operacional Xoperation, tudo isso com o objetivo de servir serviços externos SERVEX.

O XSYS deve obedecer a um modelo conceptual comum e permitir a participação de SERVEX da responsabilidade de entidades distintas, com interesses comerciais, públicos ou sociais.

As máquinas Xstation são detidas e geridas por donos OWNER que as instalam em localizações por si determinadas. Os eventos ocorridos numa Xstation são comunicados a uma Xmiddle. Cada Xmiddle disponibiliza informação autorizada a serviços SERVEX e pode retransmitir para as Xstation comandos produzidos por esses serviços. Os utilizadores USER podem recorrer às Xstation para obter ou devolver embalagens PACK vazias, ou para depositar ou levantar Encomendas acondicionadas em PACK. A gestão das embalagens PACK vazias é da responsabilidade do XSYS, e a gestão das Encomendas é da responsabilidade dos SERVEX.

### 1.2 Objetivos da arquitetura de referência

Pretende-se definir uma arquitetura de referência aberta para a realização do XSYS. Essa referência deverá funcionar como uma base comum de raciocínio, integração e conformidade, considerando:

- permitir a interoperabilidade entre cada Xmiddle e múltiplas Xstation e múltiplos SERVEX;
- permitir as ações da Xoperation;
- permitir o registo de novos SERVEX sem exigir, por omissão, alterações à arquitetura de referência;
- permitir que cada jurisdição LEX estabeleça regras aplicáveis às Xstation e aos SERVEX que operem no seu território;
- tornar relacionáveis e auditáveis os eventos, comandos, decisões e intervenções operacionais relevantes;
- limitar barreiras de entrada, não só permitindo que diferentes entidades desenvolvam máquinas, serviços ou componentes compatíveis, mas facilitando isso através da clareza da especificação;
- distinguir elementos obrigatórios da especificação, elementos configuráveis, e extensões específicas de um SERVEX.

### 1.3 Entidades principais

A letra X é utilizada como prefixo convencional das designações próprias do sistema XSYS. Não constitui uma sigla, não tem expansão autónoma e não identifica uma entidade.

A lista seguinte pretende identificar as entidades principais do âmbito do XSYS:

- **UNECE** – A entidade responsável pela governação e gestão global do XSYS e pelo registo e autorização dos SERVEX.
- **Xstation** – O tipo de máquina física onde os utilizadores obtêm ou devolvem PACK e depositam ou levantam Encomendas.
- **Xmiddle** – Plataforma lógica que mantém registos, intermedeia comunicações e aplica regras.
- **Xoperation** – A estrutura operacional que assegura as missões necessárias ao funcionamento do XSYS.
- **SERVEX** – Um tipo de sistema externo que interage com o XSYS para prestar serviços a clientes próprios.
- **LEX** – Uma entidade jurisdicional aplicável ao local onde uma Xstation se encontra instalada.
- **USER** – Uma entidade que utiliza uma Xstation como cliente ou trabalhador de um SERVEX.
- **PACK** – Tipo de embalagem normalizada e reutilizável, que o XSYS reconhece.

### 1.4 Objeto, Encomenda e Encomenda de Serviço

Os objetos que uma Xstation pode reconhecer e manipular podem ser tipificados em três conceitos:

- **Objeto** – Algo ainda não identificado colocado na plataforma Xstation-counter de uma Xstation.
- **PACK** – Um objeto que a Xstation reconhece como uma embalagem PACK legítima; se não tiver conteúdo não será certamente uma Encomenda.
- **Encomenda** – Um PACK que a Xstation reconhece como tendo algum tipo de conteúdo.
- **Encomenda de Serviço** – Uma Encomenda acompanhada por um SERVEX.

### 1.5 Eventos e comandos

Um evento representa a ocorrência de um facto relevante numa Xstation, na Xmiddle, num SERVEX ou numa operação da Xoperation. Um comando representa uma instrução autorizada que pode produzir uma alteração num elemento do sistema.

Os eventos e comandos entre SERVEX e Xstation são intermediados pela Xmiddle e sujeitos às regras aplicáveis. Por isso um SERVEX não comunica diretamente com uma Xstation.

---

## 2 Máquinas Xstation

Cada Xstation é instalada num local físico pertencente a uma jurisdição LEX, e é registada numa única Xmiddle pelo seu OWNER.

Cada Xstation tem vários sensores e uma unidade digital de aquisição de dados Xstation-DAQ que recebe as leituras de todos esses sensores.

A Xmiddle pode ordenar à Xstation que execute operações, cuja execução física é responsabilidade dos componentes locais da Xstation. As operações de transporte interno de um PACK são realizadas pelo mecanismo interno Xstation-robot.

### 2.1 Xstation-safe – guarda de Encomendas

Cada Xstation tem um módulo Xstation-safe com compartimentos adequados para armazenar as PACK aceites como Encomenda. A quantidade de compartimentos disponíveis é definida pelo OWNER da Xstation.

### 2.2 Xstation-pick – levantamento de Encomendas

Cada Xstation tem uma plataforma Xstation-pick, de acesso livre aos utilizadores, onde são colocados os PACK para levantamento pelos USER.

### 2.3 Xstation-pack – disponibilização de PACK vazias

Cada Xstation tem um módulo Xstation-pack com capacidades máximas próprias, definidas pelo OWNER, em número de PACK vazias a disponibilizar aos USER e em número de PACK vazias guardadas internamente para eventual futura reutilização.

Cada PACK tem um identificador único e pode ser disponibilizada vazia a um USER através da plataforma Xstation-pick.

**NOTAS DE ÂMBITO:**

- De notar que uma PACK vazia recebida para reutilização não é imediatamente disponibilizada, tendo de ser recolhida (devendo ser depois higienizada e reacondicionada, ou ser considerada não reusável, o que por agora está fora do âmbito do problema).
- Cada PACK pode pertencer a um tipo (por exemplo: carta, caixa de cartão, caixa com isolamento térmico, caixa almofadada, etc.), mas por simplicidade isso deve ser considerado por agora fora do âmbito do problema.

### 2.4 Xstation-counter – receção e classificação de objetos

Cada Xstation tem uma plataforma Xstation-counter para receção de objetos que sejam colocados na Xstation-pick, que tem um sensor balança Xstation-WEIGHT e um sensor câmara robotizada hiperespectral Xstation-HYPER que faz automaticamente imagens a 360° de qualquer objeto na Xstation-counter.

Quando é detetado um objeto na Xstation-counter, a Xstation analisa os dados dos sensores e classifica o objeto como:

- objeto não aceite como PACK, que encaminha para a plataforma Xstation-pick;
- objeto aceite como PACK vazia, que encaminha para o compartimento respetivo da Xstation-pack;
- objeto aceite como PACK com conteúdo, podendo por isso ser uma Encomenda, ao que a Xmiddle deve responder com um comando para encaminhar para um compartimento Xstation-safe concreto (significando que há um SERVEX que reconheceu esse PACK como Encomenda de Serviço) ou para a plataforma Xstation-pick (significando que nenhum SERVEX a reconheceu como Encomenda de Serviço).

### 2.5 Xstation-mng – gestão e controlo

O módulo Xstation-mng inclui:

- uma unidade de alimentação ininterrupta Xstation-UPS, que permite que a Xstation encerre de forma controlada se a alimentação elétrica externa falhar;
- um interruptor local;
- uma unidade de processamento Xstation-PROC;
- a aplicação de controlo Xstation-SOFT, que recebe eventos da Xstation-DAQ e comandos da Xmiddle, e envia eventos para a Xmiddle e comandos internos para os equipamentos que controla;
- a aplicação de comunicação segura Xstation-COMM, que assegura a comunicação entre a Xstation e a Xmiddle.

---

## 3 Plataforma lógica Xmiddle

Uma Xmiddle intermedeia as comunicações entre as Xstation e os SERVEX registados nessa Xmiddle, mantendo informação sobre as entidades, eventos, comandos e mensagens relevantes.

Uma Xmiddle consiste nos componentes Xmiddle-core, Xmiddle-lex e Xmiddle-smart.

### 3.1 Xmiddle-core

O Xmiddle-core é o componente que:

- mantém o registo de cada Xstation, da sua localização, capacidades e estados;
- mantém o registo de cada SERVEX autorizado e dos respetivos eventos;
- mantém o registo de cada Xoperation, Xoperation-base, Xoperation-team, bem como do ciclo de vida de cada Xoperation-plan;
- gere o ciclo de vida de cada Xstation, em interação com o respetivo OWNER;
- regista todos os eventos, comandos e mensagens trocados através da Xmiddle;
- disponibiliza interfaces para comunicação com Xstation, SERVEX, Xoperation e restantes entidades autorizadas;
- disponibiliza para consulta a informação que possa ser legitimamente partilhada, respeitando as regras aplicáveis.

### 3.2 Xmiddle-lex

O Xmiddle-lex regista e aplica as regras definidas pelas entidades LEX. Cada LEX pode definir regras numa linguagem própria para o efeito, sendo essas regras mantidas no Xmiddle-core em objetos Xlex associados às respetivas entidades.

Cada objeto Xlex identifica o respetivo período de validade e aplica-se a uma ou mais Xstation, ou a um ou mais SERVEX, incluindo o SAV, ou uma combinação de Xstation e SERVEX.

Uma Xstation que não tenha qualquer objeto Xlex válido definido não pode ser utilizada por nenhum SERVEX.

Qualquer SERVEX que pretenda operar numa jurisdição, incluindo o SAV (ver adiante), deve solicitar autorização à respetiva LEX, indicando o período pretendido, só podendo operar nessa jurisdição enquanto existir um objeto Xlex válido que autorize essa operação.

O Xmiddle-lex identifica e aplica os objetos Xlex válidos sempre que um evento, comando ou operação esteja sujeito a regras, considerando em cada caso a Xstation e o SERVEX envolvidos.

A definição das técnicas utilizadas para expressar e registar as regras nos objetos Xlex está fora do âmbito da arquitetura de referência. Assume-se, contudo, que essas técnicas permitem expressar regras como proibir determinados tipos de conteúdo numa Encomenda, impedir um serviço de oferecer determinadas opções ou limitar a informação que lhe pode ser disponibilizada.

### 3.3 Xmiddle-smart

O Xmiddle-smart analisa a informação operacional mantida pela Xmiddle e pode produzir previsões ou planos. No cenário de referência, o Xmiddle-smart pode criar planos Xoperation-plan para missões de equipas operacionais Xoperation-team.

O Xmiddle-smart dispõe ainda de uma capacidade de twin que mantém, para cada Xstation, uma representação digital atualizada dos aspetos observáveis relevantes para a análise da sua condição e para a manutenção preventiva. Esta capacidade utiliza informação recebida da Xstation e pode suportar a inclusão de ações de manutenção em Xoperation-plan. A realização interna do Xmiddle-smart está fora do âmbito da arquitetura de referência, devendo este componente ser entendido como uma black-box.

O Xmiddle-smart deve ainda apoiar a execução automatizada de testes a qualquer Xstation registada na Xmiddle, simulando, de forma controlada, as interações que um SERVEX genérico teria com uma Xstation. Estes testes seguem um protocolo comum definido por cada OWNER para todas as suas Xstation; durante os testes não se aplicam regras Xlex.

---

## 4 Estrutura operacional Xoperation

O XSYS inclui equipas operacionais Xoperation-team. Cada equipa está associada a uma ou mais Xstation, possui uma base física num armazém Xoperation-base e utiliza um veículo próprio para executar as missões. O mesmo local Xoperation-base pode ser base de várias destas equipas operacionais.

Cada Xoperation-team é constituída por um coordenador, um motorista e um auxiliar. O veículo encontra-se normalmente estacionado no Xoperation-base e é conduzido pelo motorista.

A razão de ser de cada Xoperation-team é o XSYS. A mesma equipa participa também no SAV como ator operacional desse serviço, mas esta participação simultânea não integra o SAV no XSYS: os dois sistemas mantêm fronteiras próprias.

O coordenador utiliza um computador portátil com duas aplicações de interface com sistemas remotos:

- **Xoperation-app**, para interação com o sistema Xmiddle.
- **SAVapp**, para interação com o serviço SAV.

### 4.1 Criação de uma missão

Uma missão é atribuída a uma Xoperation-team, dirige-se a uma Xstation e é criada a partir de um Xoperation-plan. O plano contém uma ou mais ações de fornecimento de PACK vazias, recolha de PACK vazias ou manutenção preventiva, podendo combinar livremente ações desses três tipos. A missão pode incluir ainda um SERVplan compatível com o Xoperation-plan.

Cada Xoperation-plan é criado pelo Xmiddle-smart.

Quando é criado um Xoperation-plan, se os objetos Xlex aplicáveis à Xstation e ao SAV o permitirem, o SAV é informado da criação do plano. Em consequência, o SAV procura criar oportunisticamente um SERVplan compatível. Se isso for possível, a missão será executada com esses dois planos.

Entre os SERVEX, apenas o SAV pode utilizar as Xoperation-team. Qualquer outro SERVEX que necessite de capacidade operacional deve assegurá-la por meios próprios. No entanto, quando é criado um Xoperation-plan, todos os serviços (SAV ou não) aos quais os objetos Xlex aplicáveis o permitam, são informados desse plano (o pressuposto é que essa informação poderá ser utilizada por esses serviços para planear de forma otimizada o seu uso da máquina em causa).

### 4.2 Realização de uma missão por uma Xoperation-team

Depois de receber um novo Xoperation-plan, o coordenador:

- instrui o auxiliar, quando aplicável, sobre as PACK a carregar no veículo;
- verifica se existe um SERVplan e, caso este preveja a entrega de Encomendas de Serviço na Xstation, instrui o auxiliar sobre o que carregar no veículo;
- verifica o resultado da preparação e solicita correções quando necessário;
- autoriza o início da deslocação, que parte sempre do Xoperation-base da equipa;
- durante a deslocação, instrui o auxiliar sobre as operações a executar junto da Xstation;
- verifica o resultado das operações junto da Xstation e solicita correções quando necessário;
- autoriza o regresso ao Xoperation-base da equipa;
- chegados ao Xoperation-base da equipa, se existir um SERVplan e, caso este preveja a recolha de Encomendas de Serviço na Xstation, instrui o auxiliar sobre o que descarregar do veículo;
- termina a missão, submete os relatórios necessários através das aplicações utilizadas.

O motorista conduz o veículo e informa o coordenador sobre a chegada aos locais previstos.

Na Xstation, o auxiliar executa as operações físicas de carga e descarga de PACK vazias ou de Encomendas de Serviço, e executa, quando o coordenador o determina, testes às Xstation.

Se houver PACK a retirar da máquina ou a fornecer-lhe, ou um SERVplan a executar, o coordenador instrui o auxiliar sobre isso logo que a equipa chega à Xstation. De seguida, o auxiliar executa as ações respetivas e reporta a sua conclusão.

Depois de eventualmente instruir o auxiliar como referido atrás, se houver ações de manutenção, o coordenador executa consecutivamente essas ações. Quando o coordenador conclui as suas ações, logo que o auxiliar também tenha terminado as suas, o coordenador instrui o auxiliar para executar um teste à máquina com apoio automatizado do Xmiddle-smart, o que o auxiliar executa de imediato e comunica o resultado ao coordenador. Se o teste falhar, o coordenador determina e executa a repetição das ações de manutenção necessárias, seguindo-se novo teste.

---

## 5 Serviços SERVEX e referência SAV

Tecnicamente, um SERVEX é um sistema autónomo que deve ter pelo menos uma aplicação lógica que interage com o Xmiddle com o intuito de fazer uso dos eventos e capacidades disponibilizados pelo XSYS para objetivos e utilizadores próprios desse serviço. Conceptualmente, cada um desses serviços é, portanto, um utilizador do XSYS, com objetivos e tecnologia própria.

### 5.1 SERVEX – os serviços que usam o XSYS

Quando um SERVEX é registado numa Xmiddle, esta informa-o das Xstation nela registadas para as quais esteja autorizado. Mantém posteriormente essa informação atualizada, informando-o, na medida em que essa informação lhe possa ser disponibilizada, sempre que uma Xstation seja registada ou deixe de estar registada, ou entre ou saia do estado de manutenção.

Em cada momento, uma Xstation pode estar indisponível (por exemplo, por estar desligada ou em manutenção) ou disponível. Quando disponível, pode estar livre ou reservada em exclusivo por um SERVEX.

Para a utilizar, o SERVEX solicita a sua reserva à Xmiddle; a confirmação pode depender, nomeadamente, das regras LEX aplicáveis. Uma vez confirmada, a reserva mantém-se exclusiva até que o serviço liberte a estação ou seja terminada nos termos aplicáveis, designadamente por efeito de regras LEX. Durante esse período, o serviço pode controlar indiretamente o comportamento da estação, dentro das capacidades e autorizações que lhe sejam concedidas, e é informado dos eventos da máquina que lhe sejam devidos no contexto da reserva e cuja comunicação seja permitida. Os eventos, comandos e mensagens trocados através da Xmiddle ficam aí registados.

As circunstâncias ou os eventos próprios de um serviço que o levam a solicitar a reserva ou a libertação de uma estação são da exclusiva responsabilidade desse serviço. O XSYS é agnóstico quanto a essas motivações internas, que ficam fora do âmbito do seu contexto. Admite-se, em geral, que os utilizadores do SERVEX (tipicamente clientes ou funcionários) disponham de dispositivos móveis inteligentes através dos quais comuniquem ao serviço a intenção de utilizar uma Xstation, levando-o a solicitar a respetiva reserva e, posteriormente, a libertá-la.

Cada SERVEX pode encontrar-se, em cada momento, registado em qualquer número de Xmiddle, podendo utilizar, através de cada uma delas, as Xstation nela registadas e disponíveis para as quais esteja autorizado, nos termos dos objetos Xlex aplicáveis.

Um SERVEX que seja registado em várias Xmiddle interage separadamente com cada uma delas. As Xmiddle não comunicam nem se coordenam por causa desses registos. Cabe ao SERVEX manter a informação própria necessária para distinguir as Xmiddle em que está registado e as Xstation que pode utilizar através de cada uma. Qualquer agregação de informação ou coordenação de operações que o SERVEX pretenda realizar entre diferentes Xmiddle é da sua responsabilidade interna e não constitui uma responsabilidade do XSYS.

### 5.2 SAV – um SERVEX de referência

O SAV é um SERVEX, cuja especificação constitui um anexo à arquitetura de referência do XSYS, não sendo parte do mesmo. Serve como exemplo de utilização da referência, sem limitar os objetivos ou os modelos de outros SERVEX.

O SAV é um serviço para apoiar organizações humanitárias, organizações sem fins lucrativos ou entidades do sistema das Nações Unidas. A UNECE mantém no SAV a lista de organizações autorizadas a usar este serviço e as Xstation que cada organização pode utilizar.

O SAV é um sistema que inclui:

- **SAVcore** – aplicação lógica responsável pela gestão das operações do serviço;
- **SAVsmart** – aplicação lógica responsável por prever períodos de subutilização das Xstation, que é acessível aos utilizadores com o objetivo de facilitar a tomada de decisão a esses utilizadores;
- **SAVuser** – aplicação lógica para dispositivos móveis utilizada pelas organizações registadas para comunicar com o SAV;
- **SAVapp** – aplicação lógica para dispositivos móveis utilizada pelos coordenadores das Xoperation-team;
- **SAVtransfer** – um processo que assegura a transferência de Encomendas de Serviço entre as Xoperation-base.

Os utilizadores deste serviço podem levantar ou entregar PACK vazias, bem como levantar ou entregar Encomendas de Serviço.

---

## 6 Abertura do UoD e âmbito

Este UoD não especifica todos os detalhes possíveis ou necessários. As entidades proponentes devem ter consciência dessa abertura, pretendendo-se que tenham o cuidado de identificar falhas ou ambiguidades, e que formulem pressupostos e apresentem a justificação de decisões de modelação.

As omissões, ambiguidades ou alternativas relevantes devem ser:

- identificadas;
- transformadas em questões em aberto, quando devam ser esclarecidas;
- tratadas através de pressupostos explícitos, quando seja necessário avançar;
- resolvidas através de decisões arquiteturais justificadas.

Um pressuposto ou decisão não pode contradizer silenciosamente uma regra explícita do UoD. Quando uma entidade proponente considere que uma alteração é realmente necessária, deve identificar a divergência, justificar a proposta e analisar as suas consequências.

### 6.1 Notas de âmbito

Estão fora do âmbito da arquitetura de referência do XSYS:

- a definição dos vários tipos concretos de PACK e das respetivas características físicas;
- a produção, higienização, reparação ou reciclagem das PACK;
- a seleção das tecnologias concretas de comunicação;
- a especificação detalhada dos mecanismos criptográficos ou de cibersegurança;
- os algoritmos internos de análise hiperespectral, previsão, otimização ou planeamento;
- o tratamento exaustivo de avarias, acidentes, indisponibilidades ou erros humanos nas missões;
- a especificação detalhada para a representação das regras LEX está fora do âmbito; interessa por agora apenas representar para essas regras a sua origem, período de validade, aplicabilidade e, se necessário, os seus efeitos relevantes, representando-as como conceitos black-box;
- o risco de colocação em algum Xstation-counter de algum objeto que não possa ser processado fisicamente pela Xstation;
- a análise da Xoperation-app, que deve ser entendida como interface black-box;
- Eventuais modelos de negócio ou aspetos relacionados relativos a qualquer OWNER ou SERVEX, ou exploração comercial de Xmiddle (o pressuposto é que os donos de máquinas, de serviços, e de soluções Xmiddle possam fazer contratos privados entre si visando a otimização dos seus negócios, mas isso está fora do âmbito do XSYS).

Estão fora do âmbito da análise do SAV:

- A análise do componente SAVsmart, que deve ser entendido como black-box;
- As aplicações SAVuser e SAVapp para dispositivos móveis, que devem ser entendidas como interfaces black-box.

As fronteiras de confiança, dependências críticas e consequências da indisponibilidade podem, contudo, ser representadas quando sejam necessárias para compreender a arquitetura de referência.

Os cenários de outros SERVEX além do SAV não são fornecidos pelo UoD. Por essa razão, a especificação XSYS deve impor apenas as restrições estritamente necessárias e devidamente justificadas.

### 6.2 Referências de enquadramento

Estas referências servem apenas para enquadramento, não sendo exigida às entidades proponentes a especificação dos tipos de encomendas ou embalagens:

- UNECE – United Nations Economic Commission for Europe: https://unece.org
- ISO 21067-1:2016 – Packaging – Vocabulary – Part 1: General terms: https://www.iso.org/standard/66955.html
- ISO/TC 122 – Packaging: https://www.iso.org/committee/52040.html

---

## Anexo – Dicionário de designações, siglas e conceitos do XSYS

Este dicionário reúne as designações convencionais, identificadores e siglas utilizados no UoD. Algumas designações, como por exemplo Xstation-pack ou Xstation-mng, funcionam como nomes próprios de componentes; não se lhes atribui uma expansão que não esteja explicitamente definida no UoD.

### A. Entidades, sistemas e conceitos do domínio

| Designação          | Definição |
|---------------------|-----------|
| **Comando**         | Instrução autorizada que pode produzir uma alteração num elemento do XSYS. Os comandos entre um SERVEX e uma Xstation são intermediados pela Xmiddle. |
| **Configuração**    | Escolha de valores, regras ou políticas previstas pelo XSYS, sem alteração das suas responsabilidades ou interfaces essenciais. |
| **Evento**          | Representação da ocorrência de um facto relevante numa Xstation, na Xmiddle, num SERVEX ou numa operação da Xoperation. |
| **Extensão**        | Nova capacidade ou interface, não pertencente à referência, acrescentada para suportar um SERVEX ou uma regra LEX. Deve ser explicitamente identificada e analisada quanto ao seu impacto. |
| **LEX**             | Entidade jurisdicional aplicável ao local onde uma Xstation se encontra instalada. Pode estabelecer regras aplicáveis às Xstation, aos SERVEX, aos utilizadores, aos objetos ou às operações realizadas na sua jurisdição. |
| **Objeto**          | Qualquer elemento colocado na plataforma do módulo Xstation-counter para ser analisado pela Xstation. |
| **PACK**            | Embalagem de transporte reutilizável, pertencente a um tipo normalizado ou a normalizar. Pode estar vazia ou, quando contém conteúdo aceite, constituir uma Encomenda. |
| **OWNER**           | Entidade que detém e gere uma ou mais Xstation, decide a sua instalação em localizações determinadas e interage com a Xmiddle para o registo, configuração e gestão do respetivo ciclo de vida. |
| **USER**            | Pessoa ou organização que utiliza uma Xstation no âmbito de um SERVEX. USER é uma designação genérica, não uma sigla. |
| **Encomenda**       | PACK com conteúdo que uma Xstation classificou como aceitável para processamento. |
| **Encomenda de Serviço** | Encomenda acompanhada por um SERVEX. |
| **SERVEX**          | Sistema autónomo que utiliza eventos e capacidades disponibilizados pelo XSYS para prestar um serviço com valor acrescentado com objetivos, regras, tecnologia, processos, dados e utilizadores próprios. SERVEX é uma designação genérica para esse conceito de serviços, não uma sigla. |
| **Xoperation-base** | Armazém que serve de base física a uma ou mais Xoperation-team. Nele são estacionados os veículos e podem ser guardadas embalagens ou encomendas necessárias às missões. |
| **UNECE**           | Entidade responsável pela governação global da iniciativa eXange. |
| **eXange**          | Nome da iniciativa descrita no UoD. |
| **Xmiddle**         | Plataforma lógica do XSYS que mantém registos, intermedeia comunicações e aplica regras. |
| **Xstation**        | Máquina física através da qual os USER obtêm ou devolvem embalagens e depositam ou levantam encomendas. |
| **Xoperation**      | Estrutura operacional responsável pelas missões necessárias ao funcionamento do XSYS. |
| **XSYS**            | Sistema sociotécnico que realiza os objetivos da iniciativa eXange. |
| **Xlex**            | Objeto mantido pelo Xmiddle-core que representa regras definidas por uma entidade LEX, o respetivo período de validade e as Xstation ou SERVEX a que se aplicam. |

### B. Conceitos das máquinas Xstation

| Designação          | Definição |
|---------------------|-----------|
| **Xstation-DAQ**    | Unidade digital de aquisição de dados que recebe as leituras de todos os sensores Xstation. |
| **Xstation-safe**   | Módulo da Xstation destinado ao armazenamento temporário de Encomendas. |
| **Xstation-pack**   | Módulo da Xstation para disponibilizar PACK vazias aos USER e a receber PACK vazias devolvidas para reutilização. |
| **Xstation-mng**    | Módulo de gestão e controlo da Xstation, incluindo outros componentes. |
| **Xstation-COMM**   | Aplicação da Xstation responsável pela comunicação e gestão segura da ligação entre a Xstation e a Xmiddle. |
| **Xstation-counter**| Módulo da Xstation destinado à receção, análise e classificação de objetos. |
| **Xstation-HYPER**  | Câmara hiperespectral utilizada pelo módulo Xstation-counter. |
| **Xstation-WEIGHT** | Balança integrada no módulo Xstation-counter para medir o peso dos objetos recebidos. |
| **Xstation-SOFT**   | Aplicação de controlo local da Xstation. |
| **Xstation-PROC**   | Unidade de processamento na qual são executadas as aplicações lógicas da Xstation. |
| **Xstation-UPS**    | Unidade de alimentação ininterrupta que permite o encerramento controlado da Xstation em caso de falha da alimentação elétrica externa. |
| **Xstation-pick**   | Plataforma da Xstation onde a mesma coloca objetos PACK para serem pegados pelos USER. |
| **Xstation-robot**  | Mecanismo interno de uma Xstation que move objetos PACK entre plataforma e compartimentos. |

### C. Conceitos da plataforma Xmiddle

| Designação          | Definição |
|---------------------|-----------|
| **Xmiddle-core**    | Componente central da Xmiddle. |
| **Xmiddle-lex**     | Componente da Xmiddle responsável pela aplicação das regras definidas pelas entidades LEX. |
| **Xmiddle-smart**   | Componente da Xmiddle que analisa informação operacional, mantém uma representação digital dos aspetos observáveis das Xstation, produz previsões ou Xoperation-plan e apoia testes automatizados às Xstation. |
| **Xoperation-app**  | Aplicação utilizada pelo coordenador de uma Xoperation-team para interagir com a Xmiddle. |

### D. Estrutura operacional e planos

| Designação          | Definição |
|---------------------|-----------|
| **Missão**          | Unidade de trabalho operacional atribuída a uma Xoperation-team para executar um ou mais planos compatíveis. |
| **Xoperation-plan** | Plano que contém uma ou mais ações de fornecimento de PACK vazias, recolha de PACK vazias ou manutenção preventiva, em qualquer combinação desses três casos. |
| **SERVplan**        | Plano produzido pelo SAV para qualquer combinação de ações de levantamento ou entrega de Encomendas de Serviço. |
| **Xoperation-team** | Equipa operacional responsável pela execução de missões. |

### E. Serviço de referência SAV

| Designação          | Definição |
|---------------------|-----------|
| **SAV**             | Serviço de referência do XSYS. A expansão literal da sigla não é definida no UoD. |
| **SAVcore**         | Componente do SAV responsável pela gestão das operações e da informação própria do serviço. |
| **SAVsmart**        | Componente do SAV que produz informação destinada a suportar decisões para otimizar o uso de cada Xstation. |
| **SAVapp**          | Aplicação do SAV utilizada pelos coordenadores das Xoperation-team. |
| **SAVuser**         | Aplicação do SAV disponível às organizações registadas para usufruírem do serviço SAV. |
| **SAVtransfer**     | Processo para a transferência de Encomendas de Serviço entre Xoperation-base. |

### F. Organizações, normas e referências externas

| Designação          | Definição |
|---------------------|-----------|
| **ISO**             | International Organization for Standardization. Organização internacional responsável pela elaboração de normas técnicas. |
| **ISO 21067-1**     | Norma de vocabulário sobre embalagem, utilizada como referência para o conceito de embalagem de transporte. |
| **ISO/TC 122**      | Comité Técnico 122 da ISO, responsável pela área de packaging. |
| **Nações Unidas**   | Organização internacional em cujo sistema se podem integrar algumas das entidades potencialmente utilizadoras do SAV. |
| **UNECE**           | United Nations Economic Commission for Europe – Comissão Económica das Nações Unidas para a Europa. Entidade promotora do cenário apresentado no UoD. |