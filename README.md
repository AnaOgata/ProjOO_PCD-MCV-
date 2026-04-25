CONTEXTUALIZAÇÃO — INVERSÃO DE CONTROLE IoC E PADRÃO OBSERVER

Sem IoC, cada objeto que precisa de informação puxa os dados de quem os possui: o observador chama a PCD, pergunta o valor e decide o que fazer. O problema é que, com N observadores, cada um precisa saber quando perguntar — o que exige polling, timers ou acoplamento direto ao ciclo de vida da PCD.

Com IoC, a lógica se inverte: a PCD empurra a informação para quem se cadastrou.

Os três papéis centrais do padrão neste sistema:

SUJEITO:
- Guarda o estado que interessa aos observadores.
- Mantém uma lista de IObservadorPCD.
- Chama o callback dos observadores quando o estado muda.
- Papel exercido por PCD

OBSERVADOR:
- Implementa a interface IObservadorPCD.
- Declara o método callback que o Sujeito irá invocar.
- Papéis exercidos por Universidade, AlertaClimatico

CALLBACK:
-É o método Medicao Alterada Evento Medicao.
- Chamado automaticamente pela PCD — nunca pelo observador.
- Recebe todos os dados necessários via objeto de evento push.
