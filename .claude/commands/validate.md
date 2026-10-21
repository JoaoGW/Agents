# Validação do monorepo

Leia `docs/VALIDACAO.md` e as regras de `.claude/rules/testing.md`.

1. Inspecione o diff e identifique as camadas afetadas.
2. Use `bash scripts/test.sh unit` para regras, tipos, lint e testes das duas camadas.
3. Use `bash scripts/test.sh ui` para regressões de interface com API simulada.
4. Use `bash scripts/test.sh e2e` para PostgreSQL descartável, migrations, API real, Next e navegador.
5. Solicite revisão isolada a `code-reviewer`, `security-auditor`, `test-reviewer` e `documentation-reviewer` conforme o escopo. Revisores não implementam correções.
6. Corrija os problemas confirmados e repita somente as verificações afetadas.
7. Informe comandos, resultados e limitações reais. Não faça commit/push/deploy sem autorização explícita.

Não use dados reais, `.env` pessoal, testes ignorados ou sleeps arbitrários para obter um resultado verde.
