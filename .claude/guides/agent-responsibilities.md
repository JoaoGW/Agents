# Responsabilidades dos agentes

Use este guia ao distribuir trabalho ou escolher uma revisão. Uma tarefa pequena pode ser executada e revisada pelo agente principal; não crie agentes apenas para cumprir um processo.

| Papel | Responsabilidade | Limite |
| --- | --- | --- |
| Agente principal | Entender o pedido, definir o escopo, implementar ou integrar as mudanças e entregar o resultado ao usuário. | Continua responsável por conferir a entrega e as evidências, mesmo quando delega. |
| Implementador, quando houver delegação | Alterar somente os arquivos e comportamentos atribuídos; verificar a mudança e informar o que ficou pendente. | Não ampliar o escopo, decidir requisitos de produto ausentes ou editar arquivos atribuídos a outro agente. |
| [code-reviewer](../agents/code-reviewer.md) | Identificar falhas de comportamento, regressões e incompatibilidades no escopo recebido. | Apenas revisão; não implementar a correção. |
| [security-auditor](../agents/security-auditor.md) | Examinar os limites de segurança afetados e apontar riscos sustentados por evidências. | Apenas revisão; não acessar segredos, executar código ou contatar serviços. |
| [test-reviewer](../agents/test-reviewer.md) | Conferir a cobertura relevante e distinguir testes executados, simulados e ausentes. | Apenas revisão; não executar testes nem alterar arquivos. |
| [documentation-reviewer](../agents/documentation-reviewer.md) | Conferir instruções, referências e contratos contra o que existe no projeto. | Apenas revisão; não alterar documentos ou executar comandos. |

## Ao delegar

- Delegue somente quando permitido pelas instruções e autorizações vigentes. Este guia não autoriza criar agentes ou ampliar permissões por si só.
- Informe o resultado esperado, os arquivos ou limites de atuação, as restrições aplicáveis e a verificação necessária. Compartilhe somente o contexto relevante.
- Evite dois agentes editando o mesmo arquivo ao mesmo tempo. Quando houver dependência, conclua a primeira entrega antes de iniciar a seguinte.
- Se não houver recurso ou autorização para delegação, o agente principal faz a análise necessária e informa que foi uma revisão própria.

## Ao devolver e integrar

O responsável pela tarefa informa o que mudou ou foi encontrado, os arquivos envolvidos, os comandos realmente executados com seus resultados e qualquer pendência. Revisores incluem arquivo/linha, evidência, impacto e correção mínima para cada achado confirmado.

O agente principal confere a entrega contra o pedido e as evidências, integra somente mudanças pertinentes e resolve falhas atribuíveis à alteração. Não aceite um resumo de sucesso que contradiga os resultados apresentados. Aplique os [critérios de conclusão](completion-criteria.md) antes de responder ao usuário.
