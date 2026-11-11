# Arquitetura e dados

Situação: arquitetura proposta. O registro com foto está implementado; os demais componentes estão em desenvolvimento ou planejados.

## 1. Visão geral

O Vetor Alerta será composto por uma interface web, uma API de aplicação, um serviço de IA para análise de imagens, um banco de dados em nuvem e uma camada de mapas/visualização.

```mermaid
flowchart LR
    U[Cidadão] --> F[Interface web]
    V[Vigilância / Especialista] --> F
    G[Gestão pública] --> F
    F -- imagem + localização --> A[API]
    A --> IA[Serviço de IA<br/>identificação preliminar]
    A --> DB[(Banco de dados em nuvem)]
    A --> MAP[Mapas e visualização]
    IA -- identificação preliminar --> A
    A -- triagem e validação --> F
    DB --> PAINEL[Painel de gestão e análise]
    PAINEL --> F
