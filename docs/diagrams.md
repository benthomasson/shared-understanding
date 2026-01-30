# Shared Understanding Framework: Workflow Diagrams

This document contains mermaid diagrams illustrating the shared understanding framework workflow, data flow, and architecture.

## Complete Workflow Overview

```mermaid
graph TB
    A[Jira Issue] --> B[Pre-Meeting Context Import]
    B --> C[Team Meeting with AI Transcript]
    C --> D[Post-Meeting AI Dialogue]
    D --> E[Validation & Error Correction]
    E --> F[Multi-Platform Search]
    F --> G[Visual Analysis]
    G --> H[Entry Creation]
    H --> I[Living Document Updates]
    I --> J[Google Docs Sharing]
    J --> K[Organizational Feedback]
    K --> L[Git Repository Commit]
    L --> M{Multiple Cycles?}
    M -->|Yes| N[Compound Understanding]
    M -->|No| O[Breakthrough Solution]
    N --> B
    
    subgraph "Tools Used"
        P[jirahhh]
        Q[Google Meet/Gemini]
        R[gcmd]
        S[slacker]
        T[claude-projects]
        U[new_entry script]
    end
    
    B -.-> P
    C -.-> Q
    D -.-> R
    F -.-> S
    H -.-> T
    H -.-> U
```

## Information Sources and Synthesis

```mermaid
graph LR
    subgraph "Input Sources"
        A[Jira Issues]
        B[Meeting Transcripts]
        C[Slack Conversations]
        D[Google Docs]
        E[Screenshots/Diagrams]
        F[Previous Entries]
    end
    
    subgraph "AI Processing"
        G[Context Import]
        H[Transcript Analysis]
        I[Search Synthesis]
        J[Visual Analysis]
        K[Pattern Recognition]
        L[Validation Dialogue]
    end
    
    subgraph "Output Artifacts"
        M[Chronological Entries]
        N[Living Documents]
        O[Architectural Plans]
        P[Code Examples]
        Q[Shared Google Docs]
    end
    
    A --> G
    B --> H
    C --> I
    D --> I
    E --> J
    F --> K
    
    G --> L
    H --> L
    I --> L
    J --> L
    K --> L
    
    L --> M
    L --> N
    L --> O
    L --> P
    N --> Q
```

## Git Repository Structure and Collaboration

```mermaid
graph TB
    subgraph "Git Repository"
        A[shared-understanding/]
        B[entries/YYYY/MM/DD/]
        C[docs/]
        D[skills/]
        E[new_entry script]
    end
    
    subgraph "Collaboration Workflows"
        F[Fork Repository]
        G[Clone for Team]
        H[Create Entries]
        I[Commit Understanding]
        J[Push to Remote]
        K[Pull Request]
        L[Merge Insights]
    end
    
    subgraph "Distribution"
        M[Team A Fork]
        N[Team B Fork]
        O[Organization Fork]
        P[Individual Clones]
    end
    
    A --> F
    F --> G
    G --> H
    H --> I
    I --> J
    J --> K
    K --> L
    L --> A
    
    F --> M
    F --> N
    F --> O
    G --> P
```

## Cognitive Enhancement Flow

```mermaid
graph TD
    subgraph "Human Limitations"
        A[Short-term Memory]
        B[System 1 Thinking]
        C[Familiarity Bias]
        D[Information Silos]
    end
    
    subgraph "AI Limitations"
        E[Context Window Limits]
        F[Temporal Confusion]
        G[Probabilistic Drift]
        H[Session Isolation]
    end
    
    subgraph "Framework Solutions"
        I[External Memory]
        J[Chronological Structure]
        K[Structured Templates]
        L[Cross-Platform Search]
        M[Validation Dialogue]
        N[Git Version Control]
    end
    
    subgraph "Enhanced Capabilities"
        O[System 2 Thinking]
        P[Temporal Understanding]
        Q[Persistent Memory]
        R[Pattern Recognition]
        S[Knowledge Discovery]
        T[Collaborative Intelligence]
    end
    
    A --> I
    B --> M
    C --> M
    D --> L
    
    E --> I
    F --> J
    G --> K
    H --> N
    
    I --> Q
    J --> P
    K --> O
    L --> S
    M --> R
    N --> T
```

## Multi-Cycle Compound Understanding

```mermaid
graph LR
    subgraph "Cycle 1"
        A1[Initial Problem]
        B1[Meeting 1]
        C1[Search 1]
        D1[Entry 1]
        E1[Understanding v1]
    end
    
    subgraph "Cycle 2"
        A2[Refined Problem]
        B2[Meeting 2]
        C2[Search 2]
        D2[Entry 2]
        E2[Understanding v2]
    end
    
    subgraph "Cycle 3"
        A3[Evolved Problem]
        B3[Meeting 3]
        C3[Search 3]
        D3[Entry 3]
        E3[Understanding v3]
    end
    
    subgraph "Breakthrough"
        F[Emergent Solution]
        G[Less Work]
        H[Better Technical]
        I[Easier for Users]
    end
    
    A1 --> B1 --> C1 --> D1 --> E1
    E1 --> A2
    A2 --> B2 --> C2 --> D2 --> E2
    E2 --> A3
    A3 --> B3 --> C3 --> D3 --> E3
    E3 --> F
    F --> G
    F --> H
    F --> I
    
    E1 -.-> C2
    E2 -.-> C3
    D1 -.-> D2
    D2 -.-> D3
```

## Knowledge Discovery Architecture

```mermaid
graph TD
    subgraph "Discovery Phase"
        A[Meeting Transcript]
        B[AI Dialogue]
        C{Understanding Valid?}
        D[Error Correction]
        E[Search Initiation]
    end
    
    subgraph "Multi-Platform Search"
        F[Jira Historical Issues]
        G[Slack Conversations]
        H[Google Drive Docs]
        I[Previous Entries]
        J[Screenshot Analysis]
    end
    
    subgraph "Synthesis Engine"
        K[Pattern Detection]
        L[Context Correlation]
        M[Gap Identification]
        N[Insight Generation]
    end
    
    subgraph "Knowledge Output"
        O[Unknown Information Discovered]
        P[Historical Context Revealed]
        Q[Decision Rationale Found]
        R[New Connections Identified]
    end
    
    A --> B
    B --> C
    C -->|No| D
    C -->|Yes| E
    D --> B
    E --> F
    E --> G
    E --> H
    E --> I
    E --> J
    
    F --> K
    G --> L
    H --> M
    I --> N
    J --> K
    
    K --> O
    L --> P
    M --> Q
    N --> R
```

## Memory Persistence System

```mermaid
graph LR
    subgraph "Ephemeral AI"
        A[Claude Session 1]
        B[Claude Session 2]
        C[Claude Session 3]
        D[Memory Loss Between Sessions]
    end
    
    subgraph "Persistence Layer"
        E[Conversation Logs]
        F[claude-projects Tool]
        G[Markdown Conversion]
        H[Git Repository Storage]
    end
    
    subgraph "Persistent Knowledge"
        I[Searchable History]
        J[Context Restoration]
        K[Decision Evolution]
        L[Long-term Memory]
    end
    
    A --> E
    B --> E
    C --> E
    E --> F
    F --> G
    G --> H
    H --> I
    H --> J
    H --> K
    H --> L
    
    I -.-> A
    J -.-> B
    K -.-> C
    L -.-> A
    L -.-> B
    L -.-> C
```

## Tools Integration Ecosystem

```mermaid
graph TB
    subgraph "External Systems"
        A[Jira Issues]
        B[Google Meet/Drive]
        C[Slack Workspace]
        D[Git Repository]
    end
    
    subgraph "Integration Layer (uvx)"
        E[jirahhh CLI]
        F[gcmd CLI]
        G[slacker CLI]
        H[claude-projects]
    end
    
    subgraph "AI Processing"
        I[Claude Analysis]
        J[Visual Processing]
        K[Text Synthesis]
        L[Pattern Recognition]
    end
    
    subgraph "Framework Output"
        M[Structured Entries]
        N[Living Documents]
        O[Shared Understanding]
        P[Version History]
    end
    
    A --> E
    B --> F
    C --> G
    
    E --> I
    F --> I
    G --> I
    H --> I
    
    I --> K
    J --> K
    K --> L
    
    L --> M
    L --> N
    M --> O
    N --> O
    
    M --> D
    N --> D
    O --> P
    D --> P
```

## Organizational Scaling Pattern

```mermaid
graph TD
    subgraph "Individual Level"
        A[Personal Understanding]
        B[Meeting Notes]
        C[Individual Insights]
    end
    
    subgraph "Team Level"
        D[Team Shared Understanding]
        E[Collaborative Entries]
        F[Team Git Repository]
    end
    
    subgraph "Department Level"
        G[Department Knowledge]
        H[Cross-team Insights]
        I[Organizational Patterns]
    end
    
    subgraph "Organization Level"
        J[Organizational Intelligence]
        K[Company-wide Understanding]
        L[Strategic Insights]
    end
    
    A --> D
    B --> E
    C --> F
    
    D --> G
    E --> H
    F --> I
    
    G --> J
    H --> K
    I --> L
    
    subgraph "Sharing Mechanisms"
        M[Google Docs Export]
        N[Fork & Pull Request]
        O[Cross-repository Learning]
    end
    
    F --> M
    I --> N
    L --> O
```

---

## How to Use These Diagrams

### **For Presentations:**
Copy the mermaid code blocks and paste into tools like:
- Mermaid Live Editor (https://mermaid.live)
- GitHub/GitLab markdown rendering
- VS Code with mermaid preview extension
- Draw.io with mermaid plugin

### **For Documentation:**
These diagrams can be embedded in:
- README files
- Technical documentation
- Process guides
- Training materials

### **For Analysis:**
Use these diagrams to:
- Identify workflow bottlenecks
- Optimize information flow
- Plan tool integrations
- Design organizational rollout

---

*Note: These diagrams illustrate the shared understanding framework as implemented across multiple real-world projects. The visual analysis mentioned throughout includes AI's surprisingly good ability to understand screenshots and technical diagrams, extending the framework beyond text-only processing.*