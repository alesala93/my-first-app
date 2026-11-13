# Feature Specifications

Dieser Ordner enthält die Feature Specs des Projekts. Die Übersicht mit dem Status aller Features steht in [INDEX.md](INDEX.md).

## Namensschema

`PROJ-X-feature-name.md`, zum Beispiel `PROJ-1-user-authentication.md`. Eine Datei beschreibt genau ein Feature.

## Aufbau einer Spec

Die Vorlage liegt in `.claude/skills/write-spec/template.md`. Eine Spec wächst mit dem Workflow:

| Abschnitt | Geschrieben von |
|-----------|-----------------|
| User Stories, Out of Scope, Acceptance Criteria (Angenommen/Wenn/Dann), Edge Cases, Open Questions, Product Decisions | `/write-spec`, später `/refine` |
| Tech Design, Technical Decisions | `/architecture` |
| Implementation Notes | `/frontend`, `/backend` |
| QA Test Results | `/qa` |
| Deployment | `/deploy` |

## Status

Der Status steht im Kopf der Spec und in [INDEX.md](INDEX.md). Beide müssen übereinstimmen:

Roadmap → Planned → Architected → In Progress → In Review → Approved → Deployed

Was die Stufen bedeuten, steht in der Legende von [INDEX.md](INDEX.md).

Details der Umsetzung stehen in den Git-Commits: `git log --grep="PROJ-1"` zeigt alle Änderungen zu einem Feature.
