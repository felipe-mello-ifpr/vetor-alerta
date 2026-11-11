# Requisitos do Vetor Alerta

Situação: documento de planejamento. Parte das funcionalidades está implementada (registro com foto); as demais estão em desenvolvimento ou planejadas.

## 1. Visão geral e escopo

O Vetor Alerta é um aplicativo de vigilância colaborativa que usa Inteligência Artificial, geolocalização e dados para identificar e monitorar vetores e riscos à saúde pública.

**Dentro do escopo:**
- Registro de ocorrências com foto (implementado).
- Identificação preliminar por IA da imagem (em desenvolvimento).
- Associação da ocorrência a um local para mapeamento (em desenvolvimento).
- Triagem e validação por responsáveis e especialistas (planejada).
- Painel de gestão com padrões e áreas de atenção (planejado).

**Fora do escopo:**
- Substituir a validação por especialistas.
- Diagnóstico sanitário definitivo.
- Cadastro de usuários com dados sensíveis (mínimo necessário).

## 2. Público-alvo

Cidadãos, agentes de vigilância, especialistas e gestão pública.

## 3. Requisitos funcionais

| ID | Requisito | Prioridade | Estado |
|---|---|---|---|
| RF01 | O sistema deve permitir registrar uma ocorrência com imagem (foto ou seleção de arquivo). | Alta | Implementada |
| RF02 | O sistema deve permitir associar a ocorrência a uma localização (geolocalização/mapa). | Alta | Em desenvolvimento |
| RF03 | O sistema deve executar análise por IA da imagem para identificação preliminar do vetor ou animal. | Alta | Em desenvolvimento |
| RF04 | O sistema deve permitir triagem e reavaliação das ocorrências por responsáveis e especialistas. | Média | Planejada |
| RF05 | O sistema deve disponibilizar painel de gestão com padrões e áreas de atenção. | Média | Planejada |
| RF06 | O sistema deve acompanhar o histórico/estado da ocorrência (registrada, em análise, validada). | Média | Planejada |
| RF07 | O sistema deve explicar ao usuário que a identificação por IA é preliminar e não substitui validação especializada. | Alta | Planejada |

## 4. Requisitos não funcionais

| ID | Requisito |
|---|---|
| RNF01 | Privacidade (LGPD): coletar apenas dados necessários; imagens e localizações tratadas com finalidade de vigilância. |
| RNF02 | Desempenho: retorno da identificação preliminar por IA em tempo compatível com uso em campo (a definir). |
| RNF03 | Acessibilidade: interface seguindo WCAG 2.1 nível AA. |
| RNF04 | Responsividade: funcionar em celulares (app) e computadores. |
| RNF05 | Idioma: interface e mensagens em português. |
| RNF06 | Transparência: deixar claro que a IA é preliminar e não substitui especialistas. |
| RNF07 | Segurança: armazenamento em nuvem com controle de acesso por perfil. |

## 5. Histórias de usuário

- **HU01 — Registrar uma ocorrência:** Como cidadão, quero enviar uma foto e a localização de um possível vetor para contribuir com a vigilância.
- **HU02 — Acompanhar minha ocorrência:** Como cidadão, quero acompanhar o estado da ocorrência que registrei.
- **HU03 — Fazer triagem:** Como agente de vigilância, quero analisar e reavaliar ocorrências para direcionar ações.
- **HU04 — Validar identificações:** Como especialista, quero validar ou corrigir a identificação preliminar da IA.
- **HU05 — Planejar ações:** Como gestor público, quero visualizar padrões e áreas de atenção para planejar ações preventivas.

## 6. Critérios de aceitação

| História | Critério |
|---|---|
| HU01 | Dado um registro com imagem válida, o sistema confirma o envio e exibe identificação preliminar. |
| HU01 | Sem localização associada, o sistema permite registrar e sinaliza ausência de geolocalização. |
| HU02 | O cidadão vê o estado atualizado da ocorrência. |
| HU03 | O agente consegue alterar o estado da ocorrência e registrar parecer. |
| HU04 | O especialista consegue validar ou corrigir a identificação da IA. |
| HU05 | O painel exibe ocorrências agregadas por local e período. |
