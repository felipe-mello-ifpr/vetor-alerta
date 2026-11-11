# Casos de uso do Vetor Alerta

Situação: documento de planejamento. O registro com foto está implementado; os demais casos estão em desenvolvimento ou planejados.

O diagrama abaixo descreve as interações entre os atores e o Vetor Alerta, com base nos requisitos de requisitos.md.

Código-fonte do diagrama (PlantUML): diagramas/casos-de-uso.puml. Versão em imagem: [PN](documentos/diagramas/image.png)G.

## Atores

Ator | Descrição
---|---
Cidadão | Registra e acompanha ocorrências.
Vigilância | Faz triagem, acompanhamento e análise.
Especialista | Valida e analisa identificações.
Gestão pública | Usa os dados para planejar e direcionar ações.

## Casos de uso principais

ID | Caso de uso | Ator | Descrição | Requisitos
---|---|---|---|---
UC01 | Registrar ocorrência com foto | Cidadão | Envia imagem do vetor ou animal. | RF01
UC02 | Associar localização | Cidadão | Associa a ocorrência a um local para mapeamento. | RF02
UC03 | Obter identificação preliminar por IA | Cidadão | Recebe identificação preliminar da imagem. | RF03, RNF06
UC04 | Acompanhar ocorrência | Cidadão | Consulta o estado e o histórico da ocorrência. | RF06
UC05 | Triar e reavaliar ocorrência | Vigilância | Analisa e reavalia ocorrências. | RF04
UC06 | Validar identificação | Especialista | Valida ou corrige a identificação da IA. | RF04
UC07 | Visualizar painel de gestão | Gestão pública | Consulta padrões e áreas de atenção. | RF05

## Casos de uso incluídos e estendidos

Caso de uso | Relação | Descrição | Requisitos
---|---|---|---
Analisar imagem com IA | include | Executa a identificação preliminar da imagem. | RF03
Aplicar OCR/visão computacional | extend | Tratamento adicional quando a imagem exigir (a definir). | RF03
Persistir ocorrência | include | Armazena imagem, localização e estado em banco em nuvem. | RNF07
Notificar estado | extend | Avisa o cidadão sobre mudança de estado (a definir). | RF06

## Fluxo principal (UC01 a UC03)

1. O cidadão registra a ocorrência com foto (UC01).
2. O cidadão associa a localização (UC02).
3. O sistema executa a análise por IA e devolve identificação preliminar (UC03).
4. O sistema informa que a identificação é preliminar (RNF06).

## Fluxos alternativos

- Imagem inválida ou ausente: o sistema exibe mensagem clara e não prossegue.
- Localização não informada: a ocorrência é registrada e sinalizada sem geolocalização.
- IA indisponível: o sistema registra a ocorrência e marca "análise pendente".
