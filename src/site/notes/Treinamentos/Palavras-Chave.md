---
{"dg-publish":true,"permalink":"/treinamentos/palavras-chave/"}
---

A descrição de cada característica é ainda mais definida por uma série de Palavras-chave. As Palavras-chave são uma forma abreviada de explicar como as características positivas e negativas interagem com o sistema de combate, utilizando um conjunto consistente de regras. Inicialmente, os movimentos possuem as palavras-chave do modelo genérico de Movimento Especial, adicionar Características Positivas ou Negativas pode alterá-las (por exemplo, trocar Ofensivo por Utilitário), adicionar novas (por exemplo, adicionar Resposta Defensiva) ou remover algumas (por exemplo, perder Atordoamento devido a Característica Arremesso). Cada uma das diferentes Palavras-chave é classificada por tipo. Como regra geral, um Movimento Especial Ofensivo deve ter exatamente uma Palavra-chave relacionada a Alcance e Movimento, além de pelo menos uma Palavra-chave relacionada a Dano para ser definido corretamente. Movimentos Especiais Utilitários precisam apenas de uma Palavra-chave de Movimento para serem definidos corretamente.

Além dessas palavras-chave necessárias, outras palavras-chave podem estar presentes para definir melhor alguns aspectos específicos de uma ação. As palavras-chave relacionadas à Duração e ao Efeito Posterior definem efeitos específicos em vez do movimento como um todo, portanto, elas não se afetam ou se sobrepõem (por exemplo, o mesmo movimento pode ter um efeito que seja Sempre e Condição e outro que seja Ao Acertar e Turnos ao mesmo tempo, sem que nenhuma dessas palavras-chave afete a outra). Nem todas as Características terão Palavras-chave em sua entrada. Se uma entrada de Característica não tiver uma palavra-chave para uma categoria especifica, ela permanecerá inalterada em relação ao modelo genérico de Movimento Especial. Palavras-chave também são usadas para identificar ou rotular movimentos. Por exemplo, uma regra pode se referir a um movimento Ofensivo Móvel, que incluiria todos os movimentos que possuem essas duas palavras-chave (sejam eles Movimentos de Comando, Movimentos Especiais ou Super Movimentos)
## Tipos de Palavra-Chave

**Tipo:** Isso define se um movimento é um ataque e se é necessário calcular o dano contra o oponente. Nesta categoria, ambas as palavras-chave são mutuamente exclusivas. Como o modelo genérico de Movimento Especial possui a palavra-chave Ofensivo, presume-se que seja um ataque, a menos que uma Característica com a palavra-chave Utilitário esteja presente, neste caso, o movimento não é mais definido como um ataque.
### Ofensivo
Você precisa realizar os cálculos para atingir o oponente que esteja ao seu alcance.
### Utilitário
Você não precisa realizar nenhum cálculo para usar o movimento, apenas ter Pontos de Técnica suficiente para usá-lo. Quando um movimento adquire a palavra-chave Utilitário, ele perde todas as palavras-chave nas categorias Dano e Alcance, e a palavra-chave Ofensiva é removida. Tal movimento não pode ter Características com as Palavras-chave de Efeito Posterior "Ao Acertar" ou "Ao Errar", portanto, a Palavra-chave "Sempre" é adicionada a todas as Características com a Palavra-chave "Utilitário" que definem um efeito extra para o movimento.
### Dano
Esta categoria é exclusiva e obrigatória para Movimentos Ofensivos. Os efeitos básicos de um golpe no oponente são definidos por estas palavras-chave. Esta categoria é especial, pois um Movimento pode ter mais de uma palavra-chave desta categoria. Todos os Movimentos Ofensivos que atingem um oponente causam Atordoamento por Impacto, independentemente das palavras-chave presentes. 
#### Normal
O dano do ataque reduz o atributo resistência do oponente. Este golpe pode derrotar um oponente se a resistência dele chegar ao máximo negativo.
#### Mental
O dano do ataque reduz o atributo mente do oponente. Este golpe pode derrotar um oponente se a mente dele chegar ao máximo negativo.
#### Espiritual
O dano do ataque reduz o atributo espirito do oponente. Este golpe pode derrotar um oponente se o espirito dele chegar ao máximo negativo.
#### Atordoante
O dano do ataque é comparado com o Limiar de Atordoamento do oponente para determinar se o defensor está atordoado.
#### Empurrão
Se o ataque acertar, o defensor é empurrado para trás 1 de distância
#### Derrubada
Se o ataque acertar, o defensor é derrubado no chão
#### Sem Dano
O Movimento não causa Dano nem Atordoamento ao oponente. A presença desta palavra-chave significa que as palavras-chave Normal e Atordoamento são removidas. O inverso também é verdade: se as palavras-chave Normal e Atordoamento não estiverem presentes, a palavra-chave Sem Dano pode ser assumida.
### Alcance
Esta categoria é exclusiva e obrigatória para Movimentos Ofensivos. Ela Abrange os alcances efetivos nos quais o movimento pode afetar um oponente.
#### Padrão
Isso significa que pode atingir alvos do Alcance 0 ao Alcance 2.
#### Toque
Isso significa que pode atingir apenas os alvos no Alcance 0.
#### Estendido
Isso significa que pode atingir alvos do Alcance 0 ao Alcance 3.
#### Longo
Isso significa que pode atingir alvos do Alcance 0 ao Alcance 4.
#### Fixo
Isso significa que pode atingir alvos em um Alcance especifico diferente de 0.
### Movimentação
Todos os movimentos devem ter uma e apenas uma palavra-chave desta categoria. Isso indica a movimentação permitida pela jogada, tanto antes quanto depois do seu efeito. Esta categoria inclui:
#### Normal
O lutador pode se mover 0 ou 1 de distância para frente ou para trás antes de usar seu movimento.
#### Móvel
O lutador pode se mover 0, 1 ou 2 de distância antes de atacar (para Movimentos Ofensivos) ou 0, 1, 2 ou 3 de distância antes de usar o movimento (para Movimentos utilitários). Não há movimentação após o movimento no mesmo turno. Um lutador não pode se mover 3 de distância se isso o levar a distância 0 de qualquer oponente.
#### Longo
O lutador pode se mover 1, 2 ou 3 de distância antes de usar o movimento, e não há movimentação após o movimento no mesmo turno.
#### Toque
O lutador pode se mover 0 ou 1 de distância antes de usar o movimento, mas mover-se 1 de alcance custa 1 ação extra. Não há movimentação após o movimento no mesmo turno.
#### Pós-Movimentação
O lutador não pode se mover antes de usar o movimento e pode então escolher se mover 0, 1 ou 2 de distância posteriormente no mesmo turno (para Movimentos Ofensivos) ou 0, 1, 2 ou 3 de distância posteriormente no mesmo turno (para Movimentos Utilitários). Um lutador não pode se mover 3 de distância se isso o levar ao alcance 0 de qualquer oponente.
#### Passagem
O lutador pode se mover 1 de distância antes de usar o movimento e, em seguida, 1 de distância depois de usá-lo.
#### Sem Movimento
O lutador não pode se mover antes ou depois de usar o movimento no mesmo turno em que o movimento é usado.
### Defesa
Esta categoria determina se a Característica tem algum efeito sobre as capacidades defensivas do atacante.
#### Bônus
O movimento oferece algum tipo de beneficio defensivo.
#### Resposta Defensiva
O movimento pode ser usado como uma [[Resposta Defensiva\|Resposta Defensiva]] em combate.
#### Passiva
O movimento pode ser usado como uma Resposta Defensiva Passiva em combate, ignorando assim as limitações de alcance e permitindo que movimentos de utilidade sejam usados como [[Respostas Defensivas\|Respostas Defensivas]]. Esta palavra-chave só pode ser adicionada a Movimentos de [[Resposta Defensiva\|Resposta Defensiva]].
### Duração
Isso indica por quanto tempo os efeitos de uma Característica permanecem em vigor. Um movimento pode ter uma dessas palavras-chave para cada efeito individual.
#### Instantânea
Os efeitos ocorrem e são resolvidos no mesmo turno em que o movimento é usado
#### Contadores de Tempo
Os efeitos continuam a ocorrer até que um determinado período de tempo seja atingido.
#### Turnos
Os efeitos continuam a ocorrer até que um número específico de turnos do lutador seja concluído.
#### Ilimitado
Os efeitos continuam a ocorrer até o fim do combate.
#### Condição
Os efeitos continuam a ocorrer até que uma condição específica seja atingida.
### Modificadores
Essas palavras-chave aplicam um modificador global a um movimento e são relativamente incomuns. Uma vez adicionadas, essas palavras-chave não podem ser removidas e, uma vez que um movimento adquira uma palavra-chave específica dessa categoria, nenhuma outra Característica com a mesma palavra-chave poderá ser adquirido no mesmo movimento.
#### Execução Estendida
A mudança geralmente requer mais de uma ação para ser concluída.
#### Distanciação
A movimentação deste Movimento Ofensivo deve ser para longe do alvo do ataque, e deve haver apenas um alvo para o ataque (ou seja, não pode ser um ataque de área ou explosivo).
#### Aproximação
A movimentação deste Movimento Ofensivo deve ser para perto do alvo do ataque, e deve haver apenas um alvo para o ataque (ou seja, não pode ser um ataque de área ou explosivo)
#### Impulso
A movimentação deste movimento deve ser de pelo menos 2 de distância
### Efeito Posterior
Essas palavras-chave só se aplicam se houver outros efeitos além do dano que ocorram após o uso de um movimento. Alguns efeitos são aplicados Ao Acertar ou Ao Errar, estes se aplicam apenas a Movimentos Ofensivos. Outros efeitos são sempre aplicados, essa palavra-chave pode ser adicionada a qualquer tipo de movimento. Um movimento específico pode ter qualquer número de efeitos posteriores, e cada efeito deve ter a palavra-chave apropriada associada a ele.
#### Ao Acertar
Esse efeito é aplicado quando um Movimento Ofensivo atinge o oponente.
#### Ao Errar
Esse efeito é aplicado quando um Movimento Ofensivo erra o oponente, seja porque o oponente esquivou ou por o oponente estar fora do alcance. Alguns outros efeitos podem fazer um movimento errar com base em outros fatores. Esses efeitos também são ativados quando o movimento falha.
#### Ao Defender
Esse efeito é aplicado quando o Movimento é selecionado como uma Opção Defensiva contra um ataque que não acertou o alvo.
#### Sempre
Esse efeito se aplica sempre que esse movimento for usado e não for interrompido por um ataque de interrupção bem-sucedido.
### Combo
As palavras-chave desta categoria determinam como a Característica funciona em um Combo. Assim como na categoria Dano, um Movimento pode ter mais de uma palavra-chave de Combo ou nenhuma. Por padrão, não ter palavras-chave de Combo significa que não há limitação quanto ao local onde o movimento é inserido em um Combo, adicionar palavras-chave de Combo impõe limitações à forma como o movimento é usado em um Combo. Algumas palavras-chave podem modificar o funcionamento da Característica especifica em um Combo, nesse caso, o movimento como um todo não é afetado. Essas palavras-chave não serão listadas junto com outras palavras-chave. Em vez disso, elas são encontradas na entrada específica do Combo e uma Característica (conforme aplicável). As palavras-chaves incluem:
#### Iniciador
Um movimento com esta Característica só pode ser usada como o primeiro movimento em um combo.
#### Inicial
O efeito desta Característica só se aplica quando o movimento é realizado em primeiro lugar em um combo.
#### Terminal
Um movimento com esta Característica só pode ser usada no final de um combo.
#### Finalizador
O efeito desta Característica só se aplica quando o movimento é realizado em ultimo lugar em um combo.
#### Misto
Se um movimento com esta Característica ocorrer em qualquer lugar de um Combo, o modificador de Agilidade desta Característica específica se aplica a todo o Combo. Penalidades de Agilidade de outras Características no mesmo movimento (mesmo as Iniciais) também são aplicadas. Bônus de Agilidade de outras Características não são afetados.
#### Restrito
Um movimento com essa Característica só pode ser usada depois de outro movimento específico tiver sido usado.
#### Sem Combo
Um movimento com esta Característica não pode ser usado em um Combo. A presença desta Palavra-chave significa que todas as outras Palavras-chave desta categoria, exceto "Restrito", são removidas.
#### Básico
Este movimento não é considerado um Movimento Especial ao construir um Combo. Movimentos Ofensivos Normais e/ou de Atordoamento causam 1 de Dano (sem modificações) quando usados no meio ou no final de um Combo.