# Arquitetura e dados

Situação: arquitetura proposta. O registro com foto está implementado; os demais componentes estão em desenvolvimento ou planejados.

## 1. Visão geral

O Vetor Alerta será composto por um aplicativo (mobile), uma API de aplicação, um serviço de IA para análise de imagens, um banco de dados em nuvem e uma camada de mapas/visualização.

~~~mermaid
flowchart LR
    U[Cidadão] --> F[Aplicativo Mobile]
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
~~~

## 2. Componentes

### 2.1 Aplicativo

Tela de registro (foto + localização), acompanhamento de ocorrências, telas de triagem/validação e painel de gestão para acesso dos diferentes perfis.

### 2.2 API

Ponto de entrada para registro de ocorrência, consulta de estado, triagem/validação e consultas do painel. Validação de tipo e tamanho da imagem e da localização.

### 2.3 Serviço de IA

Análise de imagens e identificação preliminar de vetores. Deve retornar resultado com nível de confiança e aviso de que não substitui validação especializada. (Tecnologia/modelo: a definir.)

### 2.4 Geolocalização e mapas

Associação da ocorrência a um local e exibição geográfica das ocorrências e áreas de atenção.

### 2.5 Banco de dados em nuvem

Armazenamento dos registros (imagem, localização, estado, histórico) e dados de apoio à triagem e ao painel.

### 2.6 Triagem e acompanhamento

Fluxo de análise e reavaliação pelas equipes responsáveis, com mudança de estado e parecer.

### 2.7 Painel de gestão e análise

Visualização de padrões e áreas de atenção para apoio à gestão pública.

## 3. Modelo de dados

Estruturas principais (proposta):

~~~mermaid
classDiagram
    class Ocorrencia {
        +id
        +imagem
        +localizacao
        +estado
        +criada_em
    }
    class IdentificacaoIA {
        +rotulo
        +confianca
        +preliminar
    }
    class Triagem {
        +responsavel
        +parecer
        +estado
    }
    class Validacao {
        +especialista
        +resultado
    }
    Ocorrencia --> IdentificacaoIA
    Ocorrencia --> Triagem
    Ocorrencia --> Validacao
~~~

As estruturas acima existem para persistência dos registros. Detalhamento completo em modelagem.md.

## 4. Decisões técnicas

Decisão | Justificativa
---|---
Desenvolvimento Mobile | O aplicativo é focado no uso em campo (celular) por cidadãos e agentes de vigilância.
Banco de dados em nuvem | Necessário para persistir ocorrências e permitir triagem e painel.
IA como identificação preliminar | Não substitui especialistas; apoia a triagem.
Geolocalização obrigatória? (a definir) | Melhora o mapeamento, mas não deve impedir o registro.
Controle de acesso por perfil | Cidadão, vigilância, especialista e gestão têm permissões distintas.
Transparência sobre a IA | O usuário deve saber que a identificação é preliminar.
