## O registro de módulos

O registro não é um documento separado nem um banco de dados. Ele é a própria árvore de fontes.

```text
modules/
├── microservices/<domain>/ms-<name>    um domínio de dados e sua API
├── surfaces/<domain>/sf-<name>   uma tela montada em tempo de execução
├── workflows/wf-<name>                 um processo para o runtime DAG
├── types/<domain>/                     contratos NRPC
└── solutions/                          quais módulos são distribuídos juntos
```

Um módulo existe porque seu diretório existe. Ele pertence a um domínio porque está na pasta desse domínio. Ele pertence a uma solução porque `solutions/solutions.json` o nomeia. Não há um quarto lugar onde nada disso precise ser repetido — por isso a página do ecossistema no site é produzida percorrendo a árvore, em vez de editar uma lista.

A finalidade de um módulo é obtida de seu `README.md`: o primeiro parágrafo sob `## Purpose` (para superfícies, `## UI Purpose`) e o parágrafo sob o título do limite de responsabilidade. Esses dois parágrafos são o contrato do módulo em linguagem simples, e todo módulo deve fornecê-los.

Uma camada de produto sobre a base — `club`, por exemplo — é organizada da mesma forma e pode omitir o nível de domínio: seus módulos ficam diretamente em `modules/microservices/ms-<name>`. A compilação entende ambos os formatos.
