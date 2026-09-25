> [!IMPORTANT]
> Esta proposta de SERVEX está aberta a alterações, melhorias e extensões. 

# Resgata

O Resgata liga supermercados a organizações sociais e cozinhas comunitárias para distribuir alimentos não vendidos que continuam aptos para consumo e não exigem refrigeração. Cruza lotes disponíveis com necessidades dos destinatários, coordena o transporte e levantamento através de Xstations e acompanha prazos, recolhas e redistribuições, reduzindo o desperdício alimentar.

## Persona Principal

Ana, coordenadora de uma cozinha comunitária, precisa de receber alimentos adequados às refeições planeadas, em quantidades e prazos úteis.

## Outros Atores

- Responsável de supermercado, que disponibiliza e verifica os alimentos;
- Coordenador do Resgata, que gere atribuições e incidentes;
- Operador logístico interno, que trata do transporte dos cabazes e levantamento das PACKs vazias;
- Organizações sociais e cozinhas comunitárias destinatárias.

## User Stories

- Como Ana, coordenadora de uma cozinha comunitária, quero indicar os alimentos, quantidades e prazo de que preciso, para que possa planear as refeições.
- Como responsável de supermercado, quero disponibilizar um lote não vendido, com quantidades e prazo de distribuição, para que seja aproveitado enquanto está apto para consumo.
- Como coordenador do Resgata, quero propor uma atribuição entre um lote e um pedido compatível, para que a doação tenha um destino adequado.
- Como Ana, coordenadora de uma cozinha comunitária, quero confirmar a atribuição e a possibilidade de recolha, para que apenas receba alimentos que consigo utilizar.
- Como operador logístico interno, quero conhecer a origem, a Xstation de destino e o prazo de entrega, para que transporte e deposite o cabaz a tempo.
- Como colaborador da organização destinatária, quero ser avisado da disponibilidade e levantar o cabaz na Xstation indicada, para que chegue à cozinha dentro do prazo.
- Como coordenador do Resgata, quero gerir cancelamentos e recolhas falhadas, para que possa reatribuir o cabaz enquanto a sua distribuição for viável.

## Relação com XSYS

- O Resgata usa Xstation-counter para receção dos cabazes, Xstation-safe para guarda temporária e Xstation-pick para levantamento, através de um operador logístico interno.
- Cada cabaz em PACK é acompanhado como Encomenda de Serviço.
- Todas as interações com a Xstation são mediadas pela Xmiddle: consulta de estações autorizadas, reserva exclusiva durante a utilização, comandos autorizados e eventos permitidos de depósito e levantamento. Propomos libertar a estação após cada interação concluída, mantendo apenas a ocupação do compartimento durante a guarda.
- Os supermercados verificam a aptidão dos alimentos e preparam os cabazes; parceiros do Resgata asseguram o transporte, sem usar Xoperation-team, reservada ao SAV.
- O Resgata gere lotes, pedidos, atribuições, prazos e confirmações dos destinatários.
- A classificação da Xstation não substitui a verificação alimentar.
- As PACK vazias são geridas pelo operador logístico interno.
- A operação respeita as autorizações e Xlex aplicáveis; critérios de atribuição e prazos internos pertencem ao SERVEX.
- Não propomos extensões nesta fase: aceitamos apenas alimentos adequados à guarda e transporte sem refrigeração e cabazes compatíveis com a capacidade das estações.