---
title: "Extras do dia: Deixando dinâmico"
date: "2024-05-05"
tags:
  - dev
  - extra
---

Eu não ia fazer mais nada hoje mas acabei entrando de cabeça no problema de plotagem de gráficos e como mapear
as solicitações para que seja fácil fazer os gráficos da forma correta.

Como de costume, encontrei um probleminha chato:
1. Solicitações têm latências individuais;
2. Não encapsulamos solicitação;
3. Preciso somar latência a cada solicitação toda vez que uma solicitação é concluída.

Já que estou mexendo com lista e não uma tabela de solicitações com ID, sua tupla trilha-setor e sua latência,
acabo me lascando pra mexer nisso do jeito que eu envisiono ser o certo.

Comecei refatorando a lista de tuplas para um Dicionário de tupla-latência, mas quando haviam solicitações à *mesma trilha-setor*,
começamos a adicionar tempo de latência que não é daquela solicitação.

![Amostra pequena](/documentacao-so/amostra_pequena.png)
![Amostra grande](/documentacao-so/amostra_grande.png)

Assim, quando aumentamos o número de solicitações, as consultas rápidas que costumávamos ter desaparecem completamente!

Pra sanar esse problema, acho que simplesmente criando uma classe solicitação com Id, solicitação e latência resolva,
ou talvez minha cabeça ainda está pensando no projeto de psoft e essa solução vai ser ruim.
