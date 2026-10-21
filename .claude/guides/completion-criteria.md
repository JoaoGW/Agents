# Critérios de conclusão

Antes de editar, traduza o pedido em um resultado observável. Para uma tarefa simples, uma frase basta. Use as [responsabilidades dos agentes](agent-responsibilities.md) quando houver distribuição de trabalho.

## Conferência antes da entrega

- **Pedido atendido:** o comportamento ou documento solicitado está entregue, incluindo os casos relevantes descritos pelo usuário.
- **Escopo preservado:** confira as alterações finais e confirme que não houve mudanças alheias ao pedido, perda de trabalho existente, dependências não aprovadas ou identidade de outro projeto.
- **Verificação adequada:** execute somente as verificações existentes e pertinentes à mudança. Confira os scripts e pré-requisitos antes de rodar comandos; não invente scripts ou resultados.
- **Evidência real:** diferencie verificações aprovadas, falhas, não executadas e não aplicáveis. Um build não prova uma interação no navegador; um teste com mocks não prova integração real.
- **Revisão proporcional:** releia o resultado e examine regressões prováveis. Use revisão especializada quando exigida ou útil; não exija todos os revisores para toda tarefa.
- **Referências atualizadas:** se criar ou mover instruções, comandos ou skills, atualize o mapa em CLAUDE.md e os indexadores ou chamadores afetados. Confira os novos caminhos.

Mudanças só em documentação ou configuração podem ser verificadas por leitura, consistência, referências e sintaxe aplicável; não exigem testes de aplicação sem uma razão concreta. Não repita verificações aprovadas sem novas mudanças ou dúvidas relevantes.

## Como informar o resultado

- **Concluído:** o resultado pedido e as verificações necessárias ao escopo foram atendidos. Uma revisão pode estar concluída mesmo quando encontra defeitos, desde que relate os achados e o alcance inspecionado.
- **Implementado, com validação parcial:** a mudança existe, mas uma verificação necessária não pôde ser executada. Informe o que foi comprovado, a limitação e como concluir a verificação; não declare aprovação total.
- **Pendente:** parte do pedido não foi implementada ou existe uma falha atribuível à mudança. Corrija o que estiver ao alcance antes de entregar; se depender do usuário ou do ambiente, identifique a dependência exata.

Relate falhas preexistentes sem apresentá-las como sucesso nem ampliar automaticamente a tarefa para corrigi-las. Não ignore testes, enfraqueça critérios ou execute ações não autorizadas para obter aprovação.

A resposta final deve dizer, de forma breve: o que foi entregue, por que a mudança atende ao pedido, o que foi verificado e o que permanece pendente, se houver. Não é necessário reproduzir este checklist inteiro.
