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


