## Adicionando um módulo

As etapas são as mesmas para a plataforma base e para uma camada de produto.

1. **Crie o diretório** por convenção: `modules/microservices/<domain>/ms-<name>` para um serviço, `modules/surfaces/<domain>/sf-<name>` para uma tela, `modules/workflows/wf-<name>` para um processo.
2. **Declare o contrato** em `modules/types/<domain>/` e gere os clientes com `bun run gen`. O cliente aparece como um pacote `g-<name>`, utilizável no navegador, a partir de outro processo no barramento e de dentro de um fluxo de trabalho.
3. **Escreva o README** com uma seção `## Purpose` e uma seção sobre o limite de responsabilidade. O primeiro parágrafo de cada uma acaba no registro do site — escreva para um leitor, não para você mesmo.
4. **Adicione o módulo a uma solução** se ele não for distribuído sozinho: coloque seu nome curto em `modules/solutions/solutions.json` e declare suas dependências.
5. **Reconstrua a documentação**: `bun run build:doc` na raiz do repositório. O módulo aparecerá no registro, e os contadores da página do ecossistema serão recalculados automaticamente.

O que você não precisa fazer: editar listas de módulos nos dados do site, repetir a descrição na página inicial ou registrar o módulo em qualquer outro lugar. A geração ocorre em uma única direção — das fontes para os dados, nunca no sentido contrário. Tudo em `data/` é sobrescrito pela próxima compilação.

O que a revisão exige de um módulo: ele não acessa o armazenamento de outro módulo, não contorna o barramento com chamadas diretas, declara apenas as permissões que realmente utiliza e não amplia silenciosamente sua área de responsabilidade.
