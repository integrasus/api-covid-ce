# api-covid-ce 
Este repositório trata da disponibilização da api pública do IntegraSUS sobre dados relacionados ao boletim epidemiológico covid-19 do estado do Ceará.

#### API Aberta CasosCoronavirus - (https://indicadores.integrasus.saude.ce.gov.br/indicadores/indicadores-coronavirus/coronavirus-ceara)
###### GET  https://indicadores.integrasus.saude.ce.gov.br/api/casos-coronavirus?dataInicio=2020-01-01&dataFim=2020-04-01
###### *Params: dataInicio, dataFim
###### *Data Inicio e Data Fim correspondem a data da notificação do exame

#### Gerar Arquivo CSV:
###### GET  http://download-integrasus.saude.ce.gov.br/download

#### 1 Dicionário de dados (Versão 1.0.0)
#### 1.0.1 Este dicionário descreve os campos da base dados e seus tipos
- ##### COLUNAS - Descrição - Tipo
-  bairroPaciente - Bairro de residência do paciente - Textual
-  classificacaoEstadoSivep - Resultado do exame - Categórico
-  codigoMunicipioPaciente - Código do município fornecido pelo IBGE - Numérico
-  codigoPaciente - Código identificador do paciente - Numérico
-  comorbidadeAsmaSivep - Indicador de asma - Categórico
-  comorbidadeCardiovascularSivep - Indicador de problemas cardiovas- culares - Categórico
-  comorbidadeDiabetesSivep - Indicador de diabetes - Categórico
-  comorbidadeHematologiaSivep - Indicador de hematologia - Categórico
-  comorbidadeImunodeficienciaSivep - Indicador de Imunodeficiência - Categórico
-  comorbidadeNeurologiaSivep - Indicador de morbidade neurológica - Categórico
-  comorbidadeObesidadeSivep - Indicador de obesidade - Categórico
-  comorbidadePneumopatiaSivep - Indicador de pneumonia - Categórico
-  comorbidadePuerperaSivep - Indicador de morbidade puerperal (parto precoce) - Categórico
-  comorbidadeRenalSivep - Indicador de morbidade renal - Categórico
-  comorbidadeSindromeDownSivep - indicador de síndrome de Down - Categórico
-  comorbidadeHiv - indicador de HIV - Categórico
-  comorbidadeNeoplasias - indicador de neoplasias - Categórico
-  tipoTesteExame - Tipo de exame realizado (Teste rápido, RT PCR, ELISA, Quimioluminescência, Eletroquimioluminescência)
-  racaCorPaciente - Raça/Cor do paciente
-  dataNotificacaoObito - Data na qual o óbito foi notificado
-  cnesNotificacaoEsus - Código do Cadastro Nacional de Estabelecimentos de Saúde no qual o caso foi notificado no sistema E-SUS
-  municipioNotificacaoEsus - Município que notificou o caso no E-SUS
-  dataEntradaUtisSvep - Data de entrada na UTI - Data
-  dataEvolucaoCasoSivep - Data do diagnóstico de evolução - Data
-  dataInicioSintomas - Data de início dos sintomas - Data
-  dataInternacaoSivep - Data de internação do paciente - Data
-  dataNotificacao - Data de notificação do exame - Data
-  dataObito - Data do óbito - Data
-  dataResultadoExame - Data do resultado do exame - Data
-  dataSaidaUtisSvep - Data de saída da UTI - Data
-  dataSolicitacaoExame - Data de solicitação de exame - Data
-  estadoPaciente - Estado de residência do paciente - Categórico
-  evolucaoCasoSivep - Diagnótico de evolução do caso (Cura ou óbito) - Categórico
-  idSivep - Identificador do paciente no Sistema de Vigilância da Saúde - Numérico
-  idadePaciente - Idade do paciente em anos - Numérico
-  municipioPaciente - Município de residência do paciente - Textual
-  obitoConfirmado - Confirmação de óbito - Booleano
-  paisPaciente - País de residência do paciente - Categórico
-  resultadoFinalExame - Resultado do exame final - Categórico
-  sexoPaciente - Sexo do paciente - Categórico

#### 1.1 Indicadores
#### 1.1.1 Suspeitos
Selecione como suspeitos pacientes com codigoPaciente único em que, resultadoFinalExame
seja ‘em análise’ ou resultadoFinalExame seja nulo, e, estadoPaciente = ’CE’ ou
estadoPaciente seja nulo.

#### 1.1.2 Confirmados
Selecione como caso confirmado os pacientes com codigoPaciente único em que,
estadoPaciente = ’CE’ ou estadoPaciente seja nulo, e, dataInicioSintomas seja menor ou igual a
data selecionada. Em seguida, agrupe por resultadoFinalExame. Caso o campo
dataInicioSintomas esteja nulo, o campo dataColetaExame deve ser usado e caso a
dataColetaExame seja nulo deverá ser considerado a dataResultadoExame.

#### 1.1.3 Óbitos
Selecione como número de óbitos os pacientes com codPaciente distintos em que a coluna
obitoConfirmado seja verdadeira.

#### 1.1.4 Número de exames
Faça os agrupamentos dos valores nomePaciente, resultadoFinalExame, *dia e
laboratorioExame, onde resultadoFinalExame não seja vazio, após o agrupamento faça a
contagem das linhas em que o dia seja menor que o dia selecionado e em que o dia não esteja
vazio.
*Para o dia é considerado a dataSolicitacaoExame, caso a dataSolicitacao do exame esteja
vazia é considerada a dataResultadoExame

