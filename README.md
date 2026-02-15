# DomainLang Patterns

Standard library of common DDD classifications and metadata keys for [DomainLang](https://domainlang.net).

## Install

```bash
dlang add domainlang/patterns@v1.0.0
```

## Usage

```dlang
import "domainlang/patterns"

BoundedContext Orders for Sales as Patterns.Strategic.CoreDomain {
    description: "Order lifecycle"

    metadata {
        Patterns.Meta.Status: "Production"
        Patterns.Meta.Language: "TypeScript"
    }
}
```

All classifications and metadata keys are exported from the package entry point — import once and use any namespace:

```dlang
import "domainlang/patterns"

BoundedContext Billing for Finance as Patterns.Strategic.SupportingDomain {
    metadata {
        Patterns.Meta.Language: "C#"
        Patterns.Meta.DeploymentTarget: "Kubernetes"
    }

    decisions {
        decision [Patterns.Governance.Architectural] CQRS: "Use CQRS for read/write separation"
    }
}
```

## Namespaces

### `Patterns.Strategic`

Domain classifications from Eric Evans' strategic design.

| Classification | Description |
| --- | --- |
| `CoreDomain` | The core differentiating capability of the business |
| `SupportingDomain` | Supports the core domain but is not a differentiator |
| `GenericSubdomain` | Well-understood, can be outsourced or bought off the shelf |

### `Patterns.Evolution`

Wardley Map evolution stages for classifying bounded context maturity.

| Classification | Description |
| --- | --- |
| `Genesis` | Novel and poorly understood, requires exploration |
| `CustomBuilt` | Better understood but still requires custom implementation |
| `Product` | Well-understood, increasingly standardized |
| `Commodity` | Highly standardized, utility-like |

### `Patterns.Archetypes`

Bounded context archetypes describing their primary architectural role.

| Classification | Description |
| --- | --- |
| `Execution` | Executes core business processes and workflows |
| `Engagement` | User-facing, focused on interaction and experience |
| `Analysis` | Analytics, reporting, and decision support |
| `Gateway` | Integration with external systems and services |
| `Infrastructure` | Shared technical infrastructure capabilities |
| `Compliance` | Enforces regulatory, legal, or policy requirements |

### `Patterns.Governance`

Decision classifications for tagging decisions, policies, and rules.

| Classification | Description |
| --- | --- |
| `Architectural` | System structure, boundaries, integration patterns |
| `Organizational` | Team structure, ownership, communication |
| `Technical` | Frameworks, libraries, coding standards |
| `Process` | Business processes, workflows, procedures |

### `Patterns.Meta`

Common metadata keys for annotating bounded contexts.

| Key | Suggested values |
| --- | --- |
| `Status` | Discovery, Development, Production, Sunset, Deprecated |
| `Language` | TypeScript, C#, Java, Go, Python, etc. |
| `Repository` | URL to source code repository |
| `Documentation` | URL to documentation |
| `SLA` | 99.9%, 99.99%, best-effort |
| `DeploymentTarget` | Kubernetes, Serverless, OnPremise, PaaS |
| `APIStyle` | REST, gRPC, GraphQL, Messaging, None |
| `DataStore` | PostgreSQL, MongoDB, EventStore, DynamoDB, etc. |
| `Criticality` | Critical, High, Medium, Low |

## Author

Created by Lars Baunwall ([@larsbaunwall](https://github.com/larsbaunwall))

## License

See [LICENSE](LICENSE).
