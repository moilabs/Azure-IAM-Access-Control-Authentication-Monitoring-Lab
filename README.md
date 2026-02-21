graph LR
    subgraph "Identity (Microsoft Entra ID)"
    A[HR-Team] --> |Reader| D
    B[IT-Team] --> |Contributor| D
    C[Finance-Team] --> |Reader| D
    end

    subgraph "Security Layer"
    D{MFA Enforcement}
    D --> |Security Defaults| E[Access Granted]
    D --> |Invalid Auth| F[Log: Failure]
    end

    subgraph "Azure Resources"
    E --> G[(Azure Subscription)]
    end

    subgraph "Monitoring & Audit"
    G --> H[Sign-in Logs]
    F --> H
    end

    style D fill:#f96,stroke:#333,stroke-width:4px
    style G fill:#0078d4,stroke:#fff,color:#fff
    style H fill:#fff,stroke:#333,stroke-dasharray: 5 5
