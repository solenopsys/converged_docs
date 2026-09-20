# sf-reviews

## Propósito

O sistema de avaliações como uma área de trabalho única: o que os clientes disseram sobre o trabalho,
qual parte disso está no site, o que a loja respondeu e até onde as solicitações estão chegando — quantos links foram enviados, quantos foram abertos e quantos retornaram.

## Estrutura

A superfície declara duas visualizações `setOf` — avaliações e os convites que as solicitaram — que o espaço de trabalho transforma nos botões permanentes desta aba, e uma visualização `objectOf` para uma avaliação. Fila de moderação, mural de publicadas e pilha de rejeitadas são predefinições na tabela de avaliações, não três tipos: são uma única lista lida de três maneiras. Abrir uma avaliação, portanto, abre uma subaba *dentro* de avaliações em vez de navegar para fora dela. Quando nada está selecionado, a superfície mostra sua própria tela, `ReviewsDashboardView`.

## Limite de responsabilidade

Lê e grava em `rp-reviews`. Lê `rp-orders` para o trabalho ao qual uma avaliação se refere —
diretamente do navegador, que é onde uma composição de duas chamadas pertence; nenhum dos repositórios conhece o outro.

O envio não é feito daqui. `wf-order-review-request` cria e envia o link pessoal e `wf-order-review-followup` faz o acompanhamento, porque acessar um pedido e uma avaliação em um único processo é exatamente para isso que serve um workflow. "Solicitar uma avaliação" nesta superfície cria o link e deixa o envio para esse fluxo, para que continue havendo um único remetente e um único histórico.

## Controle de avaliações

O formulário público mostra as plataformas externas para todos. O limite da loja altera a *ênfase* — um cliente satisfeito recebe primeiro as plataformas, enquanto um insatisfeito recebe primeiro a opção de falar com a loja — e nunca a disponibilidade dos links, porque mostrar o caminho para uma avaliação pública apenas a clientes satisfeitos é algo que o Google e várias outras plataformas proíbem. O cartão indica para qual lado o formulário se inclinou em uma determinada avaliação; ele não bloqueia nada.

## Dependências diretas do módulo

- `g-reviews`
- `g-orders`

## Participação na solução

- `production`

## Fonte

`modules/surfaces/business/sf-reviews`
