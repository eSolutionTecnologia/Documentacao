# Cadastro de evento para buscar dados do Portal (data de checkin/checkout/reserva etc)

## Evento
**Nome**: Relatório faturamento - buscar nf e hospede do portal

**Descrição**: Busca NF, hóspede e data da reserva do portal

**Status**: Ativo

**Prioridade**: 0


### Local
**Local**: Invoke

**Tipo**: Depois

**QualifiedName**: esAccessCenterDTO.Financeiro.Functions.Relatorios.RenegociacaoFaturamento.RelRenegociacaoFaturamentoFunctions,esAccessCenterDTO

**Method**: GetReportPorCodigo

### Invoke
**QualifiedName**: esAccessCenterPortalDTO.Financeiro.Functions.Relatorios.FunctionsPtlRelRenegociacaoFaturamento,esAccessCenterPortalDTO

**Method**: GetReportAfter
