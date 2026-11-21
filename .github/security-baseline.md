# Repository security baseline

This repository uses OWASP CI/CD Security and Secrets Management guidance as a baseline. This is not an OWASP certification or a completed application security assessment.

## Contributors

- Keep credentials in an approved secret manager or protected deployment environment. Commit only placeholder configuration examples. Never commit staff/customer records, live exports, private keys or production backups.
- Install pre-commit (`pip install pre-commit`, then `pre-commit install`) and run `pre-commit run --all-files` before pushing. Hooks require local installation and are not enforced merely by committing their configuration.
- Review workflow changes before execution. Do not execute encoded/obfuscated scripts, download-and-run commands without integrity verification, or jobs that export all secrets/environment values.
- Give workflow jobs only the permissions they need. Pin actions to reviewed full commit SHAs. Use isolated, ephemeral runners and protected environments for production; do not give untrusted pull requests deployment secrets.
- Keep lockfiles, review dependency updates, and run the project's applicable dependency and application tests. A secret scan does not replace these checks.

## Maintainer settings to verify in GitHub

- Require MFA for account access; review collaborators, sessions, installed-app access, tokens and deploy keys periodically. Grant the minimum repository scope.
- Protect the default branch with pull-request reviews, code-owner review for workflow/security changes and required checks. Restrict force pushes and branch deletion. CODEOWNERS alone does not enforce reviews.
- Limit Actions to trusted actions/reusable workflows and default GITHUB_TOKEN to read-only. Require approval for production environments and untrusted contributions. Enable secret scanning/push protection where available.
- Keep audit and workflow records under an appropriate private retention policy. Never attach unredacted logs, credentials or production data to public issues.

## Suspected exposure

Preserve evidence privately, disable affected automation, identify accessible credentials and revoke/rotate genuine exposed credentials at the issuing provider. Review relevant access logs. Removing a file or making a repository private does not revoke a secret or erase its history. Coordinate any history rewrite after preservation and rotation. Do not rerun a suspicious historical workflow or release tag.

## Verification status

The repository includes a redacted secret-scanning workflow and security ownership rules. GitHub administrative settings, credential rotation, deployment configuration and application controls require separate verification; they are not asserted as enabled by this document. Historical secret findings must be triaged; do not add blanket ignore rules merely to make checks pass.

## References

- https://cheatsheetseries.owasp.org/cheatsheets/CI_CD_Security_Cheat_Sheet.html
- https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html
- https://owasp.org/www-project-application-security-verification-standard/
