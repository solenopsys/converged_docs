# sf-equipment

## Finalidade

O chão de fábrica como uma única área de trabalho: quais máquinas existem, em que estado cada uma está,
qual trabalho está executando, o que sua telemetria informa no momento, o que aconteceu com ela
e o que está agendado para ela em seguida.

## Estrutura

A superfície declara três visualizações `setOf` — máquinas, diário e agenda — que
o espaço de trabalho transforma nos botões permanentes desta aba, e uma visualização `objectOf`
para uma máquina. Abrir uma impressora, portanto, abre uma subaba *dentro* de equipamentos,
em vez de navegar para fora dele. Sem nada selecionado, a superfície
mostra sua própria tela, `EquipmentDashboardView`.

## Limite de responsabilidade

Lê e grava em `rp-equipment`. Lê `rp-orders` para o trabalho que uma máquina está
executando e `rp-telemetry` para seus parâmetros em tempo real — ambos diretamente do navegador,
que é onde uma composição de duas chamadas deve ocorrer; nenhum dos dois repositórios
conhece o outro.

O estado da máquina é gravado daqui porque, até que uma ponte de telemetria o informe,
o operador ao lado da máquina é sua única fonte de verdade.

## Dependências diretas do módulo

- `g-equipment`
- `g-orders`
- `g-telemetry`

## Associação à solução

- `production`

## Origem

`modules/surfaces/business/sf-equipment`
