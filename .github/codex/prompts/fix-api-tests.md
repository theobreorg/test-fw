The "API Tests" GitHub Actions workflow failed.

You have access to:
- Full workflow logs under: failed-run-logs/
- Allure report / results under: failed-run-artifacts/unzipped/
- The repository checkout at the failing SHA
- A local OpenAPI spec at: specs/openapi.json
- An MCP server named: reqres_openapi

Start by reading `codex-context/failure-summary.txt`. Only open other logs/artifacts if the summary is insufficient to identify the failing test(s) and root cause.

Task:
1) Identify the failing API test(s) and root cause using logs + Allure artifacts.
2) Use the MCP server ONLY for contract lookup:
   - inspect endpoints
   - inspect request parameters
   - inspect response schemas
   - inspect expected status codes
3) Do NOT use MCP for exploratory live API behavior unless absolutely necessary.
4) Fix ONLY test code / test-support code in this repository (do not change unrelated app code).
5) Prefer minimal changes. Do not disable tests or reduce coverage to "make it green".
6) Prefer contract-aligned fixes over brittle assertion changes.
7) After changes, run:
   mvn -pl api-test-framework -am test
8) Summarize:
   - root cause
   - whether MCP contract lookup was used
   - files changed
   - why this fix is correct
   - test command output summary

Notes:
- This is Java + Maven API automation.
- Focus on broken assertions, outdated contract expectations, data setup, and contract mismatches.
