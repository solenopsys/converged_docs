## Processos

O principal problema de uma oficina em crescimento raramente é a falta de mais um botão. Com mais frequência, os processos vivem na cabeça das pessoas: quem deve responder ao cliente, quando calcular o preço, quem verifica o arquivo, quando iniciar a produção, quem avisar em caso de atraso e o que fazer depois do envio.

No Converged, essas cadeias são descritas como workflows. Um processo típico pode ir da solicitação à estimativa, aprovação, fila, produção, controle de qualidade, pagamento, entrega e notificações. O usuário normalmente não constrói um grafo do zero: os cenários prontos vêm com as soluções, e a configuração se resume a regras, papéis, prazos, integrações e notificações.

Tecnicamente, a execução é movida para a camada Runtime. Ela executa workflows, tarefas cron, passos de integração e lógica de negócio permanecendo stateless: os dados persistentes ficam nos microserviços, e o Runtime responde pela execução das cadeias. Assim a lógica de negócio não se espalha por dezenas de serviços e existe um lugar claro onde vivem as regras do processo.

Para implantações complexas, os workflows podem ser estendidos. Um desenvolvedor descreve cenários como classes TypeScript tipadas, e agentes de IA podem lançar ações permitidas dentro desses cenários. Mas para um usuário comum, o objetivo é outro: não construir um editor, mas ativar um processo pronto e obter um resultado gerenciado.
