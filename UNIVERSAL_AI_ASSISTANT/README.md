# UNIVERSAL_AI_ASSISTANT

Core architecture and project-context isolation.

Project contexts are separate sources and are loaded only when needed.

Flow: isolation → locate needed context → load only relevant data → work → save result.

AssistantDiscoverySkill is a separate data source and is not automatically merged with UNIVERSAL_AI_ASSISTANT data.