# Diagramas de classes e entidade-relacionamento

Situação: modelagem proposta, alinhada à arquitetura. O registro com foto está implementado; as demais classes estão em desenvolvimento ou planejadas.

## 1. Diagrama de classes

### API
| Classe | Responsabilidade |
|---|---|
| OcorrenciaController | Recebe registros, valida imagem e localização e devolve estado e identificação preliminar. |
| Pipeline | Orquestra análise por IA, persistência, triagem e validação. |

### Serviços
| Classe | Responsabilidade | Requisitos |
|---|---|---|
| ServicoIA | Analisa a imagem e retorna identificação preliminar com confiança. | RF03 |
| ServicoGeo | Associa e valida localização; apoia mapas. | RF02 |
| ServicoTriagem | Gerencia estados e pareceres da vigilância. | RF04, RF06 |
| ServicoValidacao | Registra validação/correção por especialistas. | RF04 |
| ServicoPainel | Agrega dados para o painel de gestão. | RF05 |

### Modelo
Estruturas persistidas: `Ocorrencia`, `IdentificacaoIA`, `Localizacao`, `Triagem`, `Validacao`, `Usuario` (perfil) e enumerações `EstadoOcorrencia`, `PerfilUsuario`.

**Relações principais:**
- `Ocorrencia` possui uma `IdentificacaoIA`, uma `Localizacao`, pode ter `Triagem` e `Validacao`.
- `Usuario` tem `PerfilUsuario` e participa de `Triagem`/`Validacao`.

## 2. Diagrama entidade-relacionamento

| Entidade | Descrição | Usada por |
|---|---|---|
| OCORRENCIA | Registro com imagem, localização e estado. | Registro, triagem, painel |
| IDENTIFICACAO_IA | Rótulo preliminar e confiança. | ServicoIA |
| LOCALIZACAO | Coordenadas/endereço associado. | ServicoGeo, mapas |
| TRIAGEM | Parecer e estado atribuídos pela vigilância. | ServicoTriagem |
| VALIDACAO | Resultado da validação por especialista. | ServicoValidacao |
| USUARIO | Perfil de acesso (cidadão, vigilância, especialista, gestão). | Todos |

**Relacionamentos:**
- OCORRENCIA 1 : 1 IDENTIFICACAO_IA
- OCORRENCIA 1 : 1 LOCALIZACAO
- OCORRENCIA 1 : N TRIAGEM
- OCORRENCIA 1 : N VALIDACAO
- USUARIO 1 : N TRIAGEM / VALIDACAO
