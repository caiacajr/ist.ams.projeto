Como ClienteX, no **workshop 2**, eu não esperaria ainda uma versão final e fechada do VP2. Mas gostaria de ver uma proposta suficientemente clara para discutir a **estrutura do XSYS**, as suas **dependências principais** e a forma como a arquitetura permite **extensão sem confundir o XSYS com cada SERVEX**.

Em forma de perguntas, eu olharia para o VP2 assim:

1. **Âmbito e fronteiras do XSYS**
   1. **O que está claramente dentro do XSYS?**  
   — Xstation, Xmiddle e Xoperation aparecem como partes do sistema, com responsabilidades distintas?
   2. **O que está fora do XSYS, mas depende dele ou interage com ele?**  
   — SERVEX, LEX, OWNER, USER e UNECE estão representados sem serem indevidamente absorvidos pelo XSYS?
   3. **A fronteira entre XSYS e SERVEX está clara?**  
   — O vosso modelo evita sugerir que o XSYS gere o negócio interno de cada SERVEX?

2. **Estrutura principal da arquitetura**
   1. **Quais são os blocos estruturais mínimos que qualquer realização do XSYS deve respeitar?**  
   — Vejo Xmiddle, Xstation e Xoperation como capacidades/componentes essenciais?

   2. **A Xmiddle está decomposta de forma coerente?**  
   — Estão distinguidos, pelo menos ao nível relevante, Xmiddle-core, Xmiddle-lex e Xmiddle-smart?

   3. **A Xstation aparece como máquina física com módulos próprios, ou como uma “caixa genérica” demasiado vaga?**  
   — Não preciso de detalhe técnico excessivo, mas preciso de perceber que capacidades estruturais ela oferece ao XSYS.

3. **Dependências entre entidades**
   1. **Quem depende de quem para operar?**  
   — Por exemplo: uma Xstation está registada numa única Xmiddle; um SERVEX pode estar registado em várias Xmiddle; o SERVEX não comunica diretamente com a Xstation.

   2. **A Xmiddle aparece como intermediária obrigatória entre SERVEX e Xstation?**  
   — Isto é importante para eu confiar que eventos, comandos, reservas e regras aplicáveis ficam controlados e registados.

   3. **A dependência da LEX está bem tratada?**  
   — Fica claro que uma Xstation e um SERVEX só podem operar quando existam autorizações/regras Xlex válidas aplicáveis?

   4. **A relação com OWNER está clara?**  
   — Quem detém, instala e regista a Xstation não deve ser confundido com quem presta o serviço SERVEX.

4. **Reserva, disponibilidade e controlo indireto**
   1. **Como a estrutura suporta a reserva exclusiva de uma Xstation por um SERVEX?**

   2. **Que dependências existem quando a Xstation está indisponível, em manutenção ou sem autorização LEX válida?**

   3. **Fica claro que o SERVEX controla a Xstation apenas indiretamente, através da Xmiddle e dentro das autorizações concedidas?**

5. **Extensibilidade da arquitetura**
   1. **Como é que um novo SERVEX pode ser acrescentado sem alterar a arquitetura de referência por defeito?**

   2. **Que partes da arquitetura são obrigatórias, que partes são configuráveis e que partes seriam extensões?**

   3. **Se um SERVEX precisar de algo novo, onde é que essa extensão impacta?**  
   — Xmiddle? Xstation? Xoperation? LEX? Interfaces? Eventos? Comandos?

   4. **Uma realização do XSYS que não implemente uma extensão continua conforme à referência base?**  
   — Esta distinção é importante para evitar que uma necessidade específica de um SERVEX vire requisito universal.

6. **Múltiplas Xmiddle e interoperabilidade**
   1. **O modelo mostra que um SERVEX pode estar registado em várias Xmiddle?**

   2. **Fica claro que as Xmiddle não se coordenam entre si por causa desse SERVEX?**

   3. **Se houver coordenação entre várias Xmiddle, está claro que essa responsabilidade é interna do SERVEX, e não do XSYS?**

7. **Xoperation e limites de uso por SERVEX**
   1. **A Xoperation aparece como capacidade do XSYS, com equipas, bases, veículos e missões?**

   2. **Está claro que as missões resultam de Xoperation-plan criados pela Xmiddle-smart?**

   3. **Está claro que o SAV tem uma relação especial com Xoperation, mas que outros SERVEX não devem assumir automaticamente o uso das Xoperation-team?**

8. **Riscos e consequências visíveis**
   1. **O que acontece estruturalmente se a Xmiddle estiver indisponível?**

   2. **O que acontece se uma regra LEX impedir uma operação?**

   3. **O que acontece se uma Xstation deixar de estar disponível durante uma utilização planeada?**

   4. **Quem fica responsável por falhas de negócio do SERVEX e quem fica responsável por falhas da infraestrutura XSYS?**

9.  **Coerência com os outros viewpoints**
    1.  **O VP2 usa os mesmos nomes e fronteiras que o VP1, VP4, VP6, VP7 e VP8?**

    2.  **As dependências estruturais do VP2 explicam depois os casos de utilização da Xmiddle e os cenários do SAV?**

    3.  **O vosso futuro SERVEX respeita a estrutura mostrada no VP2, ou exige extensões que ainda não estão assumidas?**

10. **O que eu gostaria de ver concretamente no workshop 2**
    1.  **Um diagrama preliminar legível da estrutura do XSYS.**

    2.  **Uma separação clara entre XSYS, SAV e outros SERVEX.**

    3.  **Uma primeira identificação de dependências críticas: Xmiddle, Xstation, LEX, OWNER, Xoperation e SERVEX.**

    4.  **Uma primeira distinção entre:**
        - o que é obrigatório na arquitetura de referência;
        - o que é configuração;
        - o que poderá ser extensão.

    5.  **Uma lista curta de dúvidas ainda abertas.**  
    — Prefiro ver dúvidas assumidas do que pressupostos escondidos.

    6. **Uma ou duas consequências de negócio bem explicadas.**  
    — Por exemplo: “se não houver Xlex válido, o SERVEX não pode usar a Xstation”; ou “se o SERVEX estiver em várias Xmiddle, a coordenação entre elas é responsabilidade do SERVEX”.

Em resumo: no VP2 eu gostaria de ganhar confiança de que vocês entenderam a **estrutura de referência do XSYS** e que não estão a transformar necessidades específicas do SAV ou do vosso SERVEX em obrigações universais da arquitetura.