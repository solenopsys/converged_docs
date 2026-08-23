## Implantação

O Converged atende a vários cenários de instalação: de uma pequena oficina a uma implantação de produção na infraestrutura da empresa. A plataforma base roda sobre **k3s**, uma distribuição leve de Kubernetes adequada para dispositivos edge, servidores locais e ambientes cloud.

Há dois perfis principais:

- **Mono** — UI, Runtime, microserviços, storage e cache são empacotados de forma compacta. Esse modo serve para desenvolvimento, protótipos, demonstrações e instalações pequenas em que a simplicidade de partida é mais importante.
- **Multi** — UI, grupos de Runtime, grupos de microserviços por domínio, storage e cache são separados. Esse é o perfil padrão de produção quando são necessários isolamento, escala e controle mais preciso de carga.

Os dois perfis usam o mesmo código. O que muda é a topologia dos contêineres e a configuração. Uma empresa pode começar com uma instalação compacta e depois mover o mesmo sistema para uma infraestrutura mais séria sem reescrever o produto.

Em cenários self-hosted, o cliente controla instalação, rede, backups, atualizações e localização física dos dados. Isso atende empresas com requisitos internos de segurança ou desejo de manter a produção totalmente do seu lado. A entrega cloud remove o trabalho operacional: a plataforma é implantada e atualizada pela equipe do serviço, enquanto o cliente recebe um ambiente pronto.

Também é possível uma opção híbrida: dados sensíveis e equipamentos ficam localmente, enquanto a nuvem é usada para atualizações, acesso externo, coordenação de equipes distribuídas ou funções específicas de IA. O princípio importante é não prender o cliente a um único modelo de entrega.
