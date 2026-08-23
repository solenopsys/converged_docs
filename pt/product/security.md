## Segurança

O Converged parte do princípio de que dados de produção não devem ser jogados em um monte compartilhado. Pedidos, arquivos de clientes, parâmetros tecnológicos, pagamentos, mensagens e telemetria de equipamentos precisam ser separados por workspaces e zonas de responsabilidade.

Arquiteturalmente, isso é sustentado por isolamento de dados. Microserviços possuem seus stores, e workspaces podem ter diretórios, chaves, arquivos e limites de acesso separados. Isso simplifica exportação, migração self-hosted, backups e auditoria.

Direitos de acesso se aplicam não apenas a pessoas, mas também a agentes de IA. Se um modelo lança uma ação, lê dados ou chama um workflow, isso deve acontecer dentro do seu perfil de permissões. As ações são registradas, então é possível reconstruir quem ou qual agente iniciou um passo, quais dados foram afetados e como o cenário terminou.

Implantações self-hosted e private dão ao cliente controle total sobre a infraestrutura: rede, segredos, API keys, backups e localização física dos dados. O modo cloud é operacionalmente mais simples, mas não deve virar vendor lock-in: dados devem permanecer portáveis, e cenários devem continuar reproduzíveis em outra instalação.
