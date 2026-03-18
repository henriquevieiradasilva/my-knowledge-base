# INTRODUÇÃO

1 -> IMPORTAR DADOS -> power query, transformando os dados

2 -> CRIAR RELACIONAMENTOS -> power pivot, fato e dimensão, otimizar o modelo

3 -> FÓRMULAS DAX -> medidas e formulas personalizadas, formulas, operadores e outros

4 -> DASHBOARDS -> power view, visualização dos dados, gráficos, funções 

5 -> POWER BI SERVICE ->  publicar e compartilhar os relatorios, gerir as fontes dos dados

6 -> DIVERSOS -> storytelling, simuladores, aulas extras


PREPARAR OS DADOS -> Power Query

MODELAR OS DADOS -> Power Pivot

VISUALIZAR OS DADOS -> Power View

ANALISAR OS DADOS -> Dax

IMPLANTAR E MANTER RESULTADOS -> Power BI Service


no power bi
    configurações
        
        globais
            configurações regionais
                sepadores do dax
                    [x] Usar separadores do DAX localizados: os separadores de lista e de decimais são definidos pelas configurações de localidade do windows

        arquivo atual
            redução de consulta
                [x] adicione um unico botão aplicar ao painel de filtros para aplicar as alterações de uma vez

O que é o power BI
    conjunto de serviços e ferramentas para analise de negócios que fornece insights para tomada de decisões rápidas e informadas
    nasceu do excel, composto por power view, power query, power model/pivot, virou uma só, lançado em 2015

Power BI Desktop é só o começo do processo, ferramenta de desenvolvimento
    Depois vem para o Serviço do Power BI
        Depois pode ser usado no Mobile
    
Power BI Service fica hospedada na nuvem azure e é um Saas
    versão pro ou premium conseguem usar ela

PBI PRO permite compartilhar de maneira privada, desde que receptor esteja usando tbm pro

PBI PREMIUM ao inves de licença é por capacidade, uso
    Permite PBI Report Server
        Permite em um servidor local
PBI Embedded 
    white label, vender como produto

PBI MOBILE
    coonsumir, visualizar 

PBI Gateway
    faz a vpn entre a fonte dos dados e a sua maquina, para aumentar segurança e automatizar

PBI MarketPlace
    baixar temas, visuais e etc, loja de recursos


Power BI
    Surgiu do Excel e é composto por 3 elementos
        
        --> Power Query
                Edição, ingestão, modelagem, limpeza

        --> Power Pivot/Model
                criar modelos, relacionamentos, fatos e dimensões
                    snowflakes, starschema


        --> Power View
                criação dos dashboard, relatorios, graficos, interação com o usuario


        POWER QUERY (ELT) -> POWER PIVOT/MODEL(MODELA) -> POWER VIEW(APRESENTA)


# INTRODUÇÃO A BI

O que é BI

    Business Intelligence
        Ferramentas de apoio a decisão, visando a evolução da gestão, performance e oportunidades de negócio
        "Utilizar várias fontes de informação para definir estrategias de competitividade nos negócios (barbieri 2001)"
        Processos, tecnologias e ferramentas para 
            dados-> informação -> conhecimento -> planos de ações -> negocios lucrativos (loschin 2003)
        Conjnto de processos e metodologias implementadas por meio de ferramentas para obter informações importantes para tomada de decisão 

        Estratégia de negócio, atingir metas, identificar prioridades, achar potenciais, economizar tempo, mais analitico e menos operacional

        -> Identificar necessidade e regras de negocio
        -> Trabalhar com dados !!!!
        -> transformar em informações
        -> gerar conhecimento
        -> visualização de dados
        -> apoio a tomada de decisão (estratégias)
        -> apoio para atingir os objetivos (oportunidades)
    
    Foco do BI
        prover o acesso
        apresentação da informação
        objetivos estratégicos
        identificar oportunidades de negocio

    Faz uso
        armazem de dados - Data Warehouse
        Fontes diversas (databases, xlsx, txt, csv, etc)
        ferramentas analiticas e recursos graficos OLAP
        identificação automatizada de Padrões através de relacionamentos

    Top GARTNER, quadrante


Ciclo da informação
    -> Dados(bruto, planilhas, banco de dados, internet) 
            -> Informação (gráficos, relatorios, infograficos, DASHBOARDS)
                    -> Conhecimento (conhecer, compreender, fatos)

    TUDO QUE SE MEDE PODE SER REPRESENTADO POR UM GRÁFICO
    CONTRA FATOS NÃO HÁ ARGUMENTOS

ETL
    Extract -> Transform -> Load
        Extrair -> Transformar -> Carregar
            Transformação para atender as necessidades de negócio
    fontes -> power query e outros -> datawarehouse(lakehouse) -> OLAP, data marts, reporting
    data source onpremises -> Power BI -> Data visualization
        PowerBI gateway faz a ponte doq está no desktop para o serviço na nuvem do power bi
        Stream Analitics -> real time, manda pro banco salvar mas já manda pro power bi
        HDInsight -> para bigdata, processamento massivo de grande volume de dados
        Maachine learn -> para bigdata
        Data factory -> substitui o integrated service

    1) EXTRAÇÃO 
        Coleta de dados de diversas fontes
    2) LIMPEZA, AJUSTES E PADRONIZAÇÃO (TRANSFORMAÇÃO)
        Ajustar os dados, diversas fontes diferentes, ou então não vem limpos, deixar pronto para unico repositorio
    3) ENTREGA OU CAARGA DOS DADOS
        Estruturar esses dados em camadas de apresentação, criar o modelo, depende das necessidades da empresa, que será consumido
    4) GERENCIAMENTO
        Auxiliar a gerir, extração, tarefas, planos de backup, segurança, automatização, 

    REQUISITOS PARA ETL
        - Negocio: Ter bem claro e documentado os requisitos do negócio
        - Viabilidade ds dados: Se os dados existem, se estão estruturados, se tem qualidade, se vale a pena, se da para fazer o processo de transformação
        - Latencia dos dados: Tempo máximo para disponibilização dos dados através doo sistema de BI, em quanto tempo precisa ser atualizado, todo dia, toda hora, toda semana, 
        -  Politicas de compliance e segurança: Quem pode ter acesso em que, quais as politicas de segurança, seguir as regras da empresa
  
DW E DM

    Datawarehouse
        -> fonte que alimenta a ferramenta de visualização
        -> repositório de dados coletados de diversas fontes que tem como proposito gerar informações para nivel gerencial, fonte para tomada de decisão
            nivel tatico da empresa

        criar uma visão unica e centralizada dos dados

        são organizados sendo orientados a assuntos e não por aplicação

        FONTE DE DADOS -> ETL -> DATA WAREHOUSE -> DATAVIZ
        OLTP -> STAGING AREA -> OLAP -> VISUALIZAÇÃO

    Data marts
        -> modelo relativo a uma área específica para análise de negócio
            podem ser independentes ou derivados
                Separar as informações por área de negócio, por assunto, volume de dados enorme

FATO E DIMENSÃO

    tabelas fato
        -> valores detalhados das medidas ou fatos
            o que aconteceu (venda, compra, contratação)
                em uma tabela fato CADA MEDIDA CONTEM UMA COLUNA

    tabelas dimensoes
        -> nome específico de cada membro, é um atributo
        
    boas praticas
        -> trocar nome do produto em código, numeros inteiros, melhora espaço e performance (cria uma dimensao só para o nome)
        -> trocar mes ou qualquer data para numero

        tabela de fatos 
            armazena métricas quantitativas e eventos transacionais (valores numéricos como valor de venda, quantidade), crescendo verticalmente ao longo do tempo.
            
        tabela de dimensões 
            armazena atributos descritivos e contextuais (qualitativos, como nome do produto, cliente, data), fornecendo o contexto para a análise. 



        
