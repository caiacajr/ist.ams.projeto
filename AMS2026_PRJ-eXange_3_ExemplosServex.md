# AMS 2026/2027 | Projeto eXange – Exemplos Servex

## Ideias de exemplos ilustrativos de serviços SERVEX

**Documento complementar ao Universo do Discurso e ao Enunciado do Projeto**

Este documento é complementar ao Universo do Discurso (UoD) e ao Enunciado do Projeto eXange, e não os substitui nem os altera. O seu objetivo é ajudar as equipas a visualizar, antes de comprometerem a sua proposta, o espectro de serviços SERVEX que podem vir a conceber para o VP8, desde uma reutilização quase direta da lógica do SAV até um serviço rico e fortemente diferenciado.

São apresentados cinco exemplos fictícios e independentes entre si, ordenados por grau de complexidade crescente. Cada exemplo é descrito de forma objetiva, através de uma persona principal, de eventuais Outros atores, de um conjunto de user stories e da sua relação com o XSYS. Os comentários, a análise e a comparação entre exemplos, incluindo o respetivo nível de desafio, surgem apenas na secção final do documento.

> **Importante:** estes exemplos não constituem soluções de referência e não garantem, por si só, qualquer nível de classificação. Não devem ser copiados tal e qual; podem ser adaptados, desde que a adaptação resulte num serviço em que o valor acrescentado face ao exemplo que a inspirou seja claramente evidente.

---

## Sobre os conceitos de “persona” e “user story”

Uma **persona** é uma representação semi-fictícia, mas verosímil, de um tipo de utilizador, construída a partir de um perfil realista (nome, papel, contexto, objetivos) que humaniza as necessidades de um segmento de utilizadores e ajuda a fundamentar decisões de conceção. Uma persona não é um indivíduo real, é um instrumento de trabalho que torna concretas as necessidades de um grupo de utilizadores com objetivos e comportamentos semelhantes.

Cada exemplo identifica uma **persona principal**, descrita com mais detalhe, e, quando aplicável, um ou mais **Outros atores**: outros papéis que também intervêm no serviço, mas que não são o foco principal da proposta. Uma persona ou ator secundário pode representar tanto uma pessoa individual como um papel desempenhado por uma equipa ou organização.

Uma **user story** é uma descrição curta e estruturada de uma necessidade funcional, escrita na perspetiva de uma persona ou de um ator secundário, seguindo a forma “Como \<persona ou ator\>, quero \<ação\>, para que \<benefício\>”. Cada user story liga uma necessidade concreta a quem a sente, tornando explícito o valor que essa necessidade traz. Neste documento, todo o interveniente que surge numa user story como “Como X” corresponde à persona principal ou a um outro ator explicitamente identificado nesse exemplo.

---

## Exemplo 1: EscolaKit

O EscolaKit é um serviço criado por uma Câmara Municipal, em conjunto com escolas parceiras, para fazer chegar kits escolares (material e livros) a famílias sinalizadas pelas escolas como carenciadas. As escolas parceiras, previamente autorizadas pela Câmara Municipal, preparam os kits e depositam-nos, como Encomendas de Serviço, na Xstation mais próxima da família destinatária. O encarregado de educação levanta o kit na mesma Xstation, identificando-se com um código que lhe foi fornecido pela escola.

**Persona principal:** Mariana, técnica de ação social da Câmara Municipal, responsável por autorizar escolas parceiras e acompanhar o processo.

### Outros atores

- Funcionário de uma escola parceira: prepara os kits e deposita-os na Xstation.
- Encarregado de educação: levanta o kit na Xstation, identificando-se com o código fornecido pela escola.

### User stories

- Como técnica de ação social da Câmara Municipal, quero registar as escolas parceiras autorizadas a usar o EscolaKit, para que só entidades validadas possam depositar ou levantar kits.
- Como funcionário de uma escola parceira, quero depositar na Xstation mais próxima um kit escolar destinado a uma família sinalizada, para que a família o possa levantar sem se deslocar à escola.
- Como encarregado de educação, quero levantar na Xstation o kit escolar reservado para o meu educando, apresentando o código que me foi indicado pela escola, para que a entrega seja simples e discreta.
- Como técnica de ação social da Câmara Municipal, quero confirmar quando cada kit foi depositado e levantado, para que eu possa acompanhar se chegou à família certa.

### Relação com o XSYS

- Usa a Xstation-safe para guardar o kit até ser levantado, e a Xstation-pick para o seu levantamento.
- Não propõe configurações nem extensões ao XSYS.
- Não dispõe de estrutura operacional própria: o transporte do kit até à Xstation é feito pela própria escola parceira.

---

## Exemplo 2: BiblioTroca

O BiblioTroca é um serviço de uma rede de bibliotecas municipais que permite a um leitor reservar, numa biblioteca da rede diferente da sua biblioteca habitual, um livro disponível apenas nessa biblioteca, com uma data-limite para levantamento. O bibliotecário da biblioteca onde o livro se encontra deposita-o, como Encomenda de Serviço, na Xstation indicada pelo leitor no momento da reserva. O leitor levanta o livro nessa Xstation antes da data-limite, identificando-se com o número da reserva; se o prazo expirar sem levantamento, o livro é recolhido e a reserva é cancelada.

**Persona principal:** Rui, bibliotecário da Biblioteca Municipal Norte, responsável por depositar os livros reservados por leitores de outras bibliotecas da rede.

### Outros atores

- Leitor: reserva o livro noutra biblioteca da rede e levanta-o na Xstation escolhida.
- Responsável da rede de bibliotecas: acompanha as reservas expiradas e concluídas.

### User stories

- Como leitor, quero reservar um livro disponível noutra biblioteca da rede, indicando a Xstation onde pretendo levantá-lo e uma data-limite, para que o livro me seja disponibilizado sem me deslocar à biblioteca onde se encontra.
- Como bibliotecário da biblioteca onde o livro se encontra, quero depositar o livro reservado na Xstation indicada pelo leitor, para que fique disponível para levantamento.
- Como leitor, quero ser notificado quando o livro reservado estiver disponível na Xstation, para que o vá levantar dentro do prazo.
- Como responsável da rede de bibliotecas, quero saber quando uma reserva expira sem levantamento, para que o livro seja recolhido e a reserva encerrada.

### Relação com o XSYS

- Usa a Xstation-safe e a Xstation-pick como local de depósito e de levantamento do livro.
- Introduz um conceito de domínio próprio, a Reserva de Troca, com estados como “reservado”, “disponível para levantamento”, “concluído” e “expirado”.
- Pode ser considerado um cenário em que se definem regras para o BiblioTroca para obras raras ou de acesso restrito.
- Não dispõe de estrutura operacional própria: o transporte do livro até à Xstation é assegurado pela biblioteca de origem, através dos meios habituais de circulação entre bibliotecas da rede.

---

## Exemplo 3: CicloPack

O CicloPack é um serviço de subscrição para pequenos vendedores online que pretendem reduzir o custo e o impacto ambiental da sua embalagem, através da utilização de PACK reutilizáveis nas suas expedições. O vendedor subscritor deposita a encomenda de um cliente, acondicionada numa PACK, como Encomenda de Serviço, na Xstation do seu ponto habitual de expedição. O cliente final levanta a Encomenda de Serviço na Xstation que escolheu no momento da compra e, quando pretende devolver a PACK vazia para reutilização, entrega-a em qualquer Xstation através da Xstation-pack, tal como qualquer utilizador do XSYS. O CicloPack acompanha essas devoluções, na medida da informação que lhe seja disponibilizada pela Xmiddle, e atribui um desconto ao vendedor sempre que a devolução ocorre dentro do prazo definido.

**Persona principal:** Filipa, dona de uma loja online de artesanato, subscritora do CicloPack.

### Outros atores

- Cliente de uma loja aderente ao CicloPack: levanta a encomenda na Xstation escolhida e devolve a PACK vazia depois de a esvaziar.
- Gestor do CicloPack: define, por jurisdição, os incentivos aplicáveis à devolução de PACK.

### User stories

- Como vendedora online subscritora do CicloPack, quero depositar a encomenda de um cliente, acondicionada numa PACK reutilizável, como Encomenda de Serviço na Xstation do meu ponto de expedição, para que o cliente a possa levantar.
- Como cliente de uma loja aderente ao CicloPack, quero levantar a minha encomenda na Xstation que escolhi no momento da compra, para que a receba sem necessidade de entrega ao domicílio.
- Como cliente de uma loja aderente ao CicloPack, quero devolver a PACK vazia numa Xstation próxima depois de a esvaziar, para que volte a ser reutilizada e a vendedora seja incentivada.
- Como vendedora online subscritora, quero consultar as devoluções de PACK associadas às minhas Encomendas de Serviço, para que eu calcule os descontos a que tenho direito.
- Como gestor do CicloPack, quero definir os incentivos aplicáveis à devolução de PACK, para que o serviço cumpra as regras locais de apoio à economia circular.

### Relação com o XSYS

- Usa a Xstation-safe/Xstation-pick para o depósito e levantamento das Encomendas de Serviço, e a Xstation-pack para a devolução das PACK vazias pelos clientes; essa devolução segue o funcionamento geral do XSYS e não é gerida pelo CicloPack.
- Consome, na medida do permitido, informação da Xmiddle sobre eventos de devolução de PACK relevantes para os seus subscritores.
- Possibilidade de definir regras por jurisdição para os incentivos de economia circular.
- Introduz conceitos de domínio próprios: Subscrição, Plano, Crédito/Desconto.
- Não dispõe de estrutura operacional própria.

---

## Exemplo 4: FarmaPerto

O FarmaPerto é um serviço criado por uma farmácia sediada num centro urbano para disponibilizar medicação prescrita a utentes residentes em zonas rurais remotas, onde existem Xstation mas não há farmácias nem outros serviços de saúde de proximidade, tipicamente disponíveis apenas em centros urbanos de maior dimensão. Depois de validar a receita, a farmácia prepara a Encomenda de Serviço e entrega-a a uma equipa de estafetas própria do FarmaPerto, que a transporta até à Xstation mais próxima da residência do utente e a deposita. O utente levanta a Encomenda de Serviço nessa Xstation dentro da janela horária combinada, identificando-se com o código associado à sua receita.

**Persona principal:** Dra. Beatriz, farmacêutica responsável pela farmácia urbana que presta o serviço FarmaPerto.

### Outros atores

- Estafeta da equipa própria do FarmaPerto: transporta a Encomenda de Serviço da farmácia urbana até à Xstation rural e deposita-a.
- Sr. Joaquim, utente de 78 anos residente numa aldeia sem farmácia, a 40 km do centro urbano mais próximo: levanta a medicação na Xstation da sua aldeia.
- Autoridade de saúde local: define os limites e as condições aplicáveis à entrega de medicamentos controlados.

### User stories

- Como farmacêutica responsável, quero criar uma Encomenda de Serviço associada a uma receita validada, para que só medicação prescrita seja entregue através do FarmaPerto.
- Como estafeta da equipa própria do FarmaPerto, quero saber a que Xstation rural devo entregar cada Encomenda de Serviço, para que a medicação chegue à localidade correta.
- Como utente residente numa zona rural sem farmácia, quero levantar a minha medicação na Xstation da minha aldeia dentro da janela horária combinada, para que não tenha de percorrer dezenas de quilómetros até ao centro urbano mais próximo.
- Como farmacêutica responsável, quero ser alertada se a temperatura registada no compartimento de uma Encomenda de Serviço com medicamento termolábil ultrapassar o limite definido, para que eu possa intervir antes da entrega.
- Como autoridade de saúde local, quero limitar as jurisdições e as condições em que o FarmaPerto pode entregar medicamentos controlados, para que sejam cumpridas as regras locais mesmo em zonas remotas.

### Relação com o XSYS

- Usa a Xstation-safe para o depósito e guarda da Encomenda de Serviço até ao seu levantamento pelo utente.
- Dispõe de estrutura operacional própria (uma equipa de estafetas que liga a farmácia urbana às Xstation rurais), uma vez que apenas o SAV pode utilizar as Xoperation-team.
- Envolve regras específicas para medicamentos controlados, com possível variação entre jurisdições de saúde.
- Propõe uma extensão de telemetria de temperatura associada ao compartimento de uma Encomenda de Serviço termolábil.

---

## Exemplo 5: TourFreight XServ

A TourFreight XServ é um serviço de logística para digressões de orquestras e companhias de teatro, que transporta instrumentos e equipamento frágil, sensível a condições de temperatura e humidade, entre salas de espetáculo em diferentes países, através da rede eXange. A equipa de logística própria da TourFreight XServ recolhe o instrumento junto da orquestra antes de cada troço da digressão, prepara-o como Encomenda de Serviço com os requisitos ambientais aplicáveis, e deposita-o na Xstation mais próxima da sala de espetáculo de origem. A mesma equipa, com veículos climatizados, desloca-se depois até à Xstation junto da sala de espetáculo seguinte, atravessando, quando aplicável, uma ou mais fronteiras, e entrega a Encomenda de Serviço à equipa técnica local da orquestra, que a levanta nessa Xstation antes do concerto.

**Persona principal:** Elena, gestora de logística da digressão da TourFreight XServ.

### Outros atores

- Maestro Henrique, diretor artístico: acompanha a chegada segura dos instrumentos e aciona planos de contingência quando necessário.
- Equipa de logística própria da TourFreight XServ: deposita e transporta os instrumentos entre Xstation de diferentes países.
- Equipa técnica local da orquestra: levanta os instrumentos na Xstation junto à sala de espetáculo de destino.
- Inspetor Costa, autoridade aduaneira de uma das jurisdições atravessadas: verifica a conformidade antes da saída de jurisdição.

### User stories

- Como gestora de logística da digressão, quero criar uma Encomenda de Serviço para um instrumento frágil com requisitos de humidade e temperatura, para que a sua condição seja acompanhada ao longo de toda a viagem entre países.
- Como equipa de logística própria da TourFreight XServ, quero depositar o instrumento na Xstation junto à sala de espetáculo de origem, para que fique protegido até ao início do transporte.
- Como equipa de logística própria da TourFreight XServ, quero coordenar veículos climatizados entre Xstation em diferentes países, uma vez que não posso utilizar as Xoperation-team, para que cada troço do transporte mantenha as condições exigidas.
- Como equipa técnica local da orquestra, quero levantar o instrumento na Xstation junto à sala de espetáculo de destino antes do concerto, para que a digressão não seja comprometida por atrasos.
- Como gestora de logística, quero solicitar à Xmiddle uma extensão de telemetria de humidade nas Xstation utilizadas pela TourFreight XServ, para que qualquer desvio ambiental seja detetado e registado ao longo da cadeia de custódia.
- Como gestora de logística, quero definir regras específicas por país sobre a exportação temporária de bens culturais, para que cada fronteira atravessada cumpra os requisitos legais aplicáveis.
- Como inspetor aduaneiro, quero consultar no TourFreight XServ o histórico de eventos e desvios de uma Encomenda de Serviço antes de autorizar a sua saída de jurisdição, para que a conformidade seja verificada sem atrasar desnecessariamente a digressão.
- Como gestora de logística, quero delegar a validação aduaneira e o seguro de transporte a um SERVEX especializado, tratado como caixa preta, para que a TourFreight XServ se concentre na logística climatizada e na cadeia de custódia.

### Relação com o XSYS

- Dispõe de estrutura operacional própria e especializada (veículos climatizados), coordenando múltiplas Xstation em diferentes jurisdições; não pode utilizar as Xoperation-team, reservadas ao SAV.
- Propõe uma extensão de telemetria de humidade nas Xstation utilizadas.
- Integra outro SERVEX (seguro/desalfandegamento), tratado como caixa preta.
- Introduz um modelo de domínio próprio: lote de digressão, cadeia de custódia, desvio ambiental.

---

## Comentários sobre os exemplos

As notas seguintes não fazem parte da descrição de cada serviço; sistematizam, para cada exemplo, o que ele ilustra no contexto do projeto, incluindo o seu nível de desafio relativo:

1. **EscolaKit:** representa o polo mais simples do espectro. É uma proposta válida e segura, mas oferece pouco espaço para demonstrar decisões arquitetónicas próprias: não há configuração, extensão ou estrutura operacional que a distinga do SAV. Uma equipa que parta de uma ideia deste tipo deve procurar acrescentar, pelo menos, um elemento de diferenciação genuína antes de a adotar como proposta final.

2. **BiblioTroca:** mostra que uma diferenciação pequena, mas genuína, aqui um conceito de domínio com ciclo de vida próprio, já é suficiente para elevar ligeiramente a proposta acima de uma cópia direta do SAV, sem exigir estrutura operacional própria nem regras jurisdicionais relevantes.

3. **CicloPack:** ilustra um erro comum a evitar: confundir a gestão de PACK vazias (responsabilidade do XSYS, através da Xstation-pack) com o negócio de um SERVEX. Um serviço como o CicloPack é interessante precisamente porque constrói valor de negócio (subscrições, incentivos, relatórios) sobre uma capacidade que já existe, sem tentar substituir ou duplicar essa capacidade.

4. **FarmaPerto:** mostra como a exigência de estrutura operacional própria e de regras jurisdicionais reais aumenta claramente a complexidade da proposta, sem se tornar um caso extremo. O contexto rural reforça a proposta de valor do serviço, uma vez que a Xstation passa a ser o único ponto de acesso a medicação prescrita, e é também um bom exemplo da diferença entre propor regras específicas e propor uma extensão (um novo tipo de evento), que deve ser sempre explicitamente justificada.

5. **TourFreight XServ:** representa o extremo superior do espectro apresentado neste documento. Não é o nível esperado de todas as propostas; pelo contrário, uma proposta sólida e bem justificada, algures entre os Exemplos 3 e 4, é normalmente suficiente. Serve para calibrar até onde a riqueza de uma proposta pode ir quando combina estrutura operacional própria, regras jurisdicionais reais, uma extensão bem justificada e integração com outro serviço.

6. **Sobre “regras”:** Atenção que sempre que são referidas regras, essas são específicas de cada SERVEX, a garantir por esse serviço, e não regras Xlex para aplicar pelo XSYS. Nenhum destes exemplos implica alguma configuração ou extensão à arquitetura de referência quanto a regras Xlex (isso não está vedado, mas desaconselha-se porque pode trazer um grau de complexidade muito elevado para este projeto).

---

## Tabela comparativa dos exemplos: nível de desafio face à matéria da UC

A tabela seguinte compara os cinco exemplos, por ordem crescente de complexidade (colunas), segundo dimensões diretamente relacionadas com os viewpoints e as linguagens de modelação da UC (linhas).

| Dimensão                  | 1. EscolaKit                                                                 | 2. BiblioTroca                                      | 3. CicloPack                                              | 4. FarmaPerto                                              | 5. TourFreight XServ                                      |
|---------------------------|------------------------------------------------------------------------------|-----------------------------------------------------|-----------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
| **Nível de desafio**      | Muito simples                                                                | Baixo                                               | Médio                                                     | Médio-alto                                                 | Alto                                                      |
| **Diferenciação face ao SAV** | Muito baixa: replica quase integralmente o SAV                             | Baixa: introduz a Reserva de Troca, com ciclo de vida próprio | Moderada: modelo de negócio de subscrição e incentivos   | Alta: negócio, operação e regulação próprios; contexto rural | Muito alta: caso elaborado e multi-jurisdição            |
| **Estrutura operacional própria** | Nenhuma (transporte assegurado pela escola parceira)                      | Nenhuma                                             | Nenhuma                                                   | Própria, simples (estafetas entre farmácia urbana e Xstation rurais) | Própria, especializada (frota climatizada, multi-país)   |
| **Regras específicas**    | Nenhuma                                                                      | Pontual (ex.: obras raras)                          | Moderadas (economia circular)                             | Moderadas a fortes (medicamentos controlados)              | Fortes, múltiplas jurisdições                             |
| **Configurações e extensões** | Nenhuma                                                                  | Nenhuma                                             | Nenhuma                                                   | Uma extensão justificável                                  | Extensão tecnológica justificada                          |
| **Vistas (VP8-x)**         | Possivelmente apenas VP8-0; UML de casos de utilização se necessário        | UML de domínio e máquina de estados                 | ArchiMate para o modelo global do serviço; BPMN para devolução e atribuição de incentivos; UML para subscrições, planos e créditos | ArchiMate para estrutura do serviço; BPMN para distribuição rural; UML para Encomenda de Serviço e telemetria | ArchiMate para arquitetura multi-organização; BPMN para transporte e validação aduaneira; UML para cadeia de custódia, desvios e componentes |
| **Interação com outro SERVEX** | Não aplicável                                                            | Não aplicável                                       | Não aplicável                                             | Não aplicável                                              | Sim, caixa preta (seguro/alfândega)                       |

---

## Como usar estes exemplos

- **Não copiar estes exemplos tal e qual:** são ilustrativos e destinam-se a calibrar a vossa própria proposta, não a substituí-la. Podem ser usados como ponto de partida para adaptação, desde que o resultado torne evidente o valor acrescentado face ao exemplo original.

- **Situar a ideia neste espectro:** se a proposta se aproximar do Exemplo 1, procurem identificar pelo menos um elemento de diferenciação genuína antes de a considerarem final.

- **Verificar sempre a coerência com o UoD:** qualquer configuração ou extensão proposta tem de ser explicitamente identificada, justificada e analisada quanto ao seu impacto.

- **Preferir uma proposta compreensível e coerente a uma proposta apenas mais complexa:** a riqueza de um serviço como o Exemplo 5 só tem valor se cada elemento acrescentado for compreendido e justificado pela equipa.