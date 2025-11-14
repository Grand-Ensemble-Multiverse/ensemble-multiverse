# 3. Agent-Based Architecture for NPCs, Locations, and Demiurge

## Context
We are designing a multiplayer RPG integrated with HumHub (Yii) and Evennia (Python). The game world requires dynamic, AI-driven interactions for:
- **Major NPCs** with unique personalities and memory.
- **Major Locations** with context-aware events.
- A **Demiurge Agent** to maintain global narrative consistency and trigger world-level events.

Traditional static scripting cannot scale for emergent storytelling and adaptive gameplay. We need an architecture that supports autonomous, intelligent agents.

## Decision
We will implement an **agent-based architecture** using:
- **LangChain** for orchestration and memory management.
- **LLMs** (Azure OpenAI GPT models) for dialogue and narrative generation.
- **Redis** for short-term memory and caching.
- **Vector Database** (e.g., Qdrant or Azure Cosmos DB with vector search) for long-term memory and semantic retrieval.
- **Event Bus** (Redis Streams or Azure Service Bus) for inter-agent communication.

### Agent Hierarchy:
- **Demiurge Agent**: Oversees global narrative, validates coherence, triggers major events.
- **NPC Agents**: Represents major characters, handles dialogue and behavior.
- **Location Agents**: Represents major locations, manages environmental context and local events.

### Integration:
- HumHub → Displays NPC interactions and location updates.
- Evennia → Handles game mechanics and triggers agent calls.
- AI Layer → Hosts agents and coordinates responses.

## Alternatives Considered
- **Static scripted NPCs**: Rejected due to lack of adaptability.
- **Single global AI model**: Rejected; lacks modularity and autonomy for individual entities.
- **Rust-based agents**: Rejected; Python ecosystem offers better AI/LLM integration.

## Consequences
- **Positive**:
  - Modular and scalable design.
  - Supports emergent storytelling and adaptive gameplay.
  - Easy integration with existing HumHub and Evennia architecture.
- **Negative**:
  - Increased complexity in orchestration and state management.
  - Requires robust monitoring and debugging tools for agent interactions.


