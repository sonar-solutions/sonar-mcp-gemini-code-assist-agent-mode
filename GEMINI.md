# Project quality rules

This project uses SonarQube Cloud for code quality and security verification.

## Rules for code generation and modification

1. **Always verify code with SonarQube before marking a task as complete.** After generating or modifying code, run `sonar-scanner` in the project root to trigger analysis.

2. **If the quality gate fails, fix the issues.** Use the SonarQube MCP tools to retrieve the specific issues (`search_sonar_issues_in_projects`), understand the rules (`show_rule`), and fix the code accordingly.

3. **Treat low test coverage as a blocking issue.** If test coverage is below the quality gate threshold, add unit tests until it passes.

4. **Fix issues holistically.** When addressing quality gate failures, refactor the code as a whole rather than patching individual rules one at a time.

5. **Only consider a task complete when the quality gate passes.** Check the quality gate status using `get_project_quality_gate_status` after every scan. If it fails, iterate.

## Project details

- Scanner: `sonar-scanner` (run from project root)
- Quality gate results: check with MCP tool `get_project_quality_gate_status`
- Issue details: retrieve with MCP tool `search_sonar_issues_in_projects`
- Rule explanations: retrieve with MCP tool `show_rule`
