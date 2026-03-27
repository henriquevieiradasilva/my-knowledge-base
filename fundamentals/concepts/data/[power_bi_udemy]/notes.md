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

STAR SCHEMA E SNOW FLAKE

    Star schema
        - o modelo mais utilizado na MODELAGEM DIMENSIONAL
        - ajuda no suporte a tomada de decisão
        - melhora a performance dos sistemas voltados para consulta

        formato de estrela
            tabela fato no meio e tabela dimensoes rodeando a tabela fato

        criar uma projeção/modelagem da base de dados para os sistemas de apoio a decisão
        
        dimensão data
            date - data
            integer - dia
            integer - mes
            integer - ano
            char - dia_da_semana
            char - bimestre
            char - trimestre
            char - semestre
            char - indicador feriado
            char - indicador fim de semana 

        Fato serve de ligação entre as dimensões
        Dimensões se ligam unicamente a fato

        dimensoes exemplos
            tempo
            produto
            geografia
            canal de negocio
            linha de produto
            linha de canal de vendas
        

    Snow Flake
        - também feito para suportar tomada de decisão
        - economiza espaço em disco  
  
        formato de floco de neve
            tabela fato no meio, tabela dimensões em volta e subtabelas em volta da tabela dimensao
                uma vai ligando a outra

        tabela fato não é a unica tabela de ligacao
        ligação entre dimensões pode levar a pior performance

    Fato = o que aconteceu
    Dimensão = ajuda a explicar o fato


PASSOS PARA MODELAGEM DIMENSIONAL

    objetivo principal -> levantar e representar as necessidades de análise e de informações em determinado contexto

    passos
        1) o que estamos avaliando? 
            --> definir no modelo os fatos ou metricas, valor numerico
        2) como serão avaliados ou analisados?
            --> definir no modelo as dimensões relacionadas as metricas/fatos
        3) qual o nível mais baixo de detalhe das informações? 
           --> qual nível de granularidade das informações em cada dimensão
                    drill down --> aprofunda a análise para ver detalhes,
                    drill up --> agrega dados para visualizar um resumo mais ampla

        4) como se espera agrupar ou sumariar as informações?
            --> qual hierarquia de agrupamento das informações será utilizado em cada dimensão





# MODELAGEM NO POWER QUERY, INGESTÃO E TRANSFORMAÇÃO DE DADOS

APRESENTAÇÃO DO POWER QUERY
        
        para acessar power query no power Bi
            -> [transformar dados]
        não tem [ctrl] + [Z] no power query, é tudo por etapas aplicadas
            -> para excluir algo feito/voltar algo é só excluir a última etapa feita, ou excluir quantas etapas forem necessárias


IMPORTAÇÃO ARQUIVO CSV E QUALIDADE DOS DADOS

        quando escolhe uma fonte de dados 
            o power bi ja faz tudo automatico, mas pode haver falhas e assim sendo necessario escolher manualmente:
                - na origem do arquivo onde colocamos o tipo que é digitado é recomendavel colocar
                    [65001: Unicode (UTF-8)]
                        Assim pega todos os caracteres, acentos e etc, mas se necessário vai trocando até sumir com os caracteres não encontrados
                - no delimitador é oq será usado de referencia para separar os dados, colunas e etc no arquivo
                    [Vírgula]
                        geralmente usa-se virgula mas é possivel personalizar isso também
                - na detecção de tipo de dados é possivel fazer uma projeção com algumas linhas de exemplo ou com arquivo completo
                    [Com base nas primeiras 200 linhas]
                        é melhor pq é mais otimizado, se for um dataset gigantesco pode demorar muito, mas vai muito da necessidade

        SEMPRE TRANSFORMAR OS DADOS ANTES DE CARREGAR

        automaticamente ele já coloca o tipo de dado que é
            mas é possível trocar clicando no [icone] ao lado do nome da coluna, na esquerda 
                e assim selecionando o tipo que deseja                

        para ver qualidade dos dados e outras informações gerais
            a linha verde padrão mostra se há algum dado com erro na coluna ou então mostra se tem vazio/nulo
                para personalizar e abrir ainda mais informações
                -> [exibição]
                    -> [qualidade da coluna] -> Vai explicar melhor a faixa padrão em baixo da coluna
                    -> [distribuição da coluna] -> Explica ainda mais sobre a faixa, dando os registros também 
                    -> [perfil da coluna] -> Detalhamento completo com as informações sobre a qualidade coluna, tambem minimo maximo
                        --> por padrão criase o perfil da coluna com base ns 1000 primeiras linhas, mas é possível trocar isso e colocar para usar de referencia o conjunto todo, a opção fica na barra na barra mais em baixo do powerbi
                            [Criação de perfil de coluuna com base em todo o conjunto de dados]


PROMOVENDO CABEÇALHOS E ALTERANDO FONTES DE DADOS

    power query roda atras dos panos a linguagem M
        para codar manualmente usando essa linguagem:
            -> [EXIBIÇÃO] 
                -> [EDITOR AVANÇADO]    
            ou
            -> [PÁGINA INICIAL]
                -> [EDITOR AVANÇADO]
        
        barra de fórmulas seria o mini terminal que também tem no excel, se não estiver visivel ainda:
            -> [EXIBIÇÃO]
                -> [(X) BARRA DE FÓRMULAS]
        
        configuração de consulta são todas as etapas feitas em ordem que aparece em um menu na direira, se não estiver visivel ainda(aqui da pra ver versões diferentes antes e depois das transformações):
            -> [EXIBIÇÃO]
                -> [CONFIG. CONSULTA]   
                            por padrão ja acontece automaticamente quando importa uma ordem: 1 -> carrega da fonte, 2 -> da nome certo aos cabeçalhos/nomes das colunas, 3 -> Determina o tipo certo usado em cada coluna

        para achar a fonte ou mudar o caminho da fonte caso tenha mudado, só ir em 
            -> [PÁGINA INICIAL]
                -> [CONFIGURAÇÕES DA FONTE DE DADOS]
                    -> [ALTERAR FONTE]
                        -> ai é só colocar o caminho certo e boa

        caso o power BI não tenha pego automaticamente os nomes das colunas e o tipo delas, só usar
            -> [PÁGINA INICIAL]
                -> [USAR A PRIMEIRA LINHA COMO CABEÇALHO]
                        automaticamente ele já coloca os nomes e os tipos, usando a fonte de referência


COLUNAS EXEMPLOS E SUBSTITUÇÃO DE VALORES

    quando precisamos juntar conteudo de duas colunas, como por exemplo nome e sobrenome para nome completo
        JEITO 1:
            -> [SELECIONA AS COLUNAS USANDO CTRL]
                -> [ADICIONAR COLUNA]
                    -> [COLUNA DE EXEMPLOS]
                        -> [DA SELEÇÃO]
                            -> [ESCREVER NA NOVA COLUNA O "NOME" + " " + "SOBRENOME" ]
                                    power BI vai captar automaticamente que você quer juntar as colunas e vai fazer o mesmo para as demais
                                        -> BOTÃO DIREITO NA COLUNA
                                            -> [RENOMEAR]


        JEITO 2: 
            -> [ADICIONAR COLUNA]
                -> [COLUNA PERSONALIZADA]
                    -> COLOCA O NOVO NOME DA COLUNA
                        -> SELECIONA AS COLUNAS DISPONÍVEIS
                            -> COMO VAMOS CONCATENAR, USA-SE O &
                                -> TAMBÉM COLOCAMOS O ESPAÇO USANDO " "
                                       no final teremos algo como "= [PrimeiroNome]&" "&[UltimoNome]"


    quer trocar os valores de uma coluna, como por exemplo trocar do ingles para ptbr
        -> [BOTÃO DIREITO DO MOUSE]
            -> [SUBSTITUIR VALORES]
                    ai é só colocar o valor que vai ser substituido e com oq deve substituir


EXTRAÇÃO E DIVISÃO DE COLUNAS

    dica: na prática deve usar o menor numero de etapas possivel, alcançar o necessário com o menor que conseguir

    quando a gente precisa dividir o conteudo de uma coluna
        -> [TRANSFORMAR]
            -> [DIVIDIR COLUNA]
                -> [POR DELIMITADOR]
                    -> COLOCA O DELIMITADOR CORRETO
                        -> [CADA OCORRENCIA DO DELIMITADOR]
                                resultado final serão duas colunas separadas, cada um com conteudo anterior e posterior ao delimitador
        
        outro jeito de fazer isso é 
            -> [TRANSFORMAR]
                -> [EXTRAIR]
                        assim ele não cria uma nova coluna, mas edita a que foi feito o processo

    da para fazer algumas transformações padrões também, como deixar tudo maiusculo ou minusculo, só usar
        -> [BOTÃO DIREITO DO MOUSE NA COLUNA]
            -> [TRANSFORMAR]
                -> [COLOCA OPÇÃO QUE PREFERIR]


EXTRAÇÃO DE ANO CAMPO DATA

    da para extrair detalhes na parte da coluna data, só precisa
        -> [BOTÃO DIREITO DO MOUSE]
            -> [TRANFORMAR]
                    ai é só escolher se quer o ano, mes, dia, trimestre, semestre e outros


IMPORTAR DADOS DO EXCEL, PIVOT E COMPLETAR DADOS

    como importar dados de um excel e limpar essa importação para vir corretamente
        aqui explicou sobre como transformar colunas em linhas e da pra fazer vice e versa alem de limpar as linhas em branco

    remover linhas vazias
        -> [PÁGINA INICIAL]
            -> [REMOVER LINHAS]
                -> [REMOVER LINHAS VAZIAS]
                        dá pra remover outros tipos também, só prestar atenção no contexto


PIVOT DE DADOS DE 200 ANOS DE HISTÓRIA

    exemplo com arquivo pivor

        seleciona a coluna
            -> [SHIFT]
                -> [END]
                        vai selecionar todas as colunas a partir da escolhida até o final na direitra
                        
                        o mesmo funcionaria usando o [HOME], mas ai faz o inverso, pega todas as anteriores

    transformar coluna em linha o powerbi já tira os nulos automaticamente

    importamos o AnimatedBarChartRace de visuals
    
    para importar visuais
        -> [VISUALIZAÇÕES]
            -> [...]
                -> [IMPORTAR UM VISUAL DE UM ARQUIVO] 

    para achar mais visuais 
        -> [VISUALIZAÇÕES]
            -> [...]
                -> [OBTER MAIS VISUAIS] 

        tudo que a gente vai usar no visual dos dashboards, fica mostrando ali no [CAMPOS]

    como usar o AnimatedBarChartRace
        é uma barra com histórico que vai aumentando gradativamente como se fosse uma corrida
            é só arrastar os campos em CAMPOS nas caixas em VISUALIZAÇÕES -> ADICIONAR DADOS NO SEU VISUAL
            Name -> País, nome do registro
            Value -> PIB, os valores usados de referencia para classificar
            Period -> Ano, tempo que sera usado de referencia

                para ajustar a quantidade de "corredores", velocidade e outros, só ir em 
                    -> [VISUALIZAÇÕES]
                        -> [FORMATAR SEU VISUAL]
                            -> [VISUAL]
                                -> [WISHYOULISATION SETTINGS]

                                    top N --> quantidade de colunas
                                    duration --> duração para cada registro no tempo em milisegundos
                                        e algumas outras personalizações 
    
MESCLAR CONSULTAS DE DIVERSAS TABELAS

    quando precisa juntar varios arquivos, o famoso merge
        para juntar e fazer de duas tabelas uma só 
        -> [PÁGINA INICIAL]
            -> [ACRESCENTAR CONSULTAS]
                -> [ACRESCENTAR CONSULTAS COMO NOVA]
                        ai só escolher as tabelas, se serão duas ou mais e juntar, vai ficar na ordem que colocar

    da pra "esconder" as tabelas que não serão usadas, ou seja, para não aparecer como opção lá no dashboards
        -> [BOTÃO DIREITO DO MOUSE]
            -> [( ) HABILITAR CARGA]
                    desabilitando essa opção, não vai aparecer la no CAMPOS
                    
    para entender melhor como o modelo que estamos utilizando funciona, como estão ligadas as tabelas e etc, só precisa:
        -> [EXIBIÇÃO]
            -> [DEPENDÊNCIAS DE CONSULTAS]
                    clicando nas tabelas/arquivos dá pra ver os caminhos de onde eles surgem
    
    se precisar, da pra atualizar manualmente os dados dos arquivos, só precisa
        -> [PÁGINA INICIAL]
            -> [ATUALIZAR VISUALIZAÇÃO]
                -> [ATUALIZAR TUDO]

                        no power BI dá pra fazer essa atualização também, só precisa clicar em 
                            -> [PÁGINA INICIAL]
                                -> [ATUALIZAR]


USANDO PARÂMETROS PARA DEFINIR CAMINHOS

    se der ruim e uma tabela perder o caminho da fonte, manualmente da para arrumar com:
        -> [CLICA NA TABELA]
            -> [CONFG. CONSULTA]
                -> [ETAPAS APLICADAS]
                    -> [FONTE]
                        -> TROCA O CAMINHO DA FONTE NA FÓRMULA NA [BARRA DE FÓRMULAS]
                        
    para otimizar esse processo utilizamos parametros
        -> [PÁGINA INICIAL]
            -> [GERENCIAR PARAMETROS]
                -> [NOVO PARAMETRO]
                    -> DA UM [NOME], DEFINA O [TIPO], COLOQUE [VALORES SUGERIDOS] E POR FIM COLOQUE O [VALOR ATUAL]
                            no nome coloque o nome do parametro e no valor atual coloca o caminho onde o arquivo se encontra

                                depois disso, vamos ter criado um parametro, que se comporta como se fosse uma variável que armazena algo, e vamos usa-la para referenciar o caminho, assim trocando uma unica vez nesse parametro, o resto se ajusta automaticamente
                                    -> [CLICA NA TABELA]
                                        -> [CONFG. CONSULTA]
                                            -> [ETAPAS APLICADAS]
                                                -> [FONTE]
                                                    -> NA FÓRMULA DENTRO DA [BARRA DE FÓRMULAS] TROCA TODO O CAMINHO PELO PARAMETRO E DEIXA SÓ O NOME DO ARQUIVO
                                                            o q antes era um ("caminho\caminho\arquivo") vai virar (caminho_dos_arquivos&"arquivo")
                                                                assim, se mudar só mudar o caminho dos arquivos e já muda tud automaticamente


IMPORTANDO ARQUIVOS DE PASTAS

    ao inves de importar arquivo por arquivo, da pra escolher uma pasta de primeira
        é importante que os arquivos tenham a mesma estrutura quando for utilizar por pasta, se n pode dar mais trabalho 
            -> [OBTER DADOS]
                ->  [PASTA]
                    -> COLOCA O CAMINHO ONDE ESTÃO OS ARQUIVOS
                        -> [COMBINAR]
                            -> [COMBINAR E TRANSFORMAR DADOS]
                                    assim o processo que fizemos manualmente ele faz tudo automatico e já cria um com todos pronto


CONSOLIDANDO INFORMAÇÕES DE MÚLTIPLAS FONTES (MESCLAR/APPEND)

    basicamente uma situação de append de colunas e merge de colunas
    
    para o merge, é só utilizar
    -> [PÁGINA INICIAL]
        -> [MESCLAR COLUNAS]
            -> CLICAR NAS COLUNAS QUE VÃO LINKAR UMA COM A OUTRA, OU SEJA, A QUE FOREM IDENTICAS PARA FAZER O JOIN, GERALMENTE ID
                -> [TIPO DE JUNÇÃO]
                        só escolher o tipo que quiser e dar um ok que vai fazer o join
                            -> [ICONE DE HALTERE]
                                -> SELECIONAR SOMENTE O [CÓDIGO] E DESABILITAR [( ) USE O NOME DA COLUNA ORIGINAL COMO PREFIXO]
                                        assim fará o merge corretamente e aparecerá somente o necessário


TRANSFORMAÇÃO DE DADOS ESTRUTURA MISTA

    agora um exemplo igual ao outro com tabelas com estruturas diferentes, mas tudo em um mesmo arquivo 
        ou seja, varias tabelas na mesma tabela, tem varias maneiras de resolver isso, uma delas:
        -> [ADICIONAR COLUNAS]
            -> [COLUNA CONDICIONAL]
                -> SE [NOME DA PRIMEIRA COLUNA] [OPERADOR] [VALOR] [VALOR QUE DESEJA QUE SEJA] ENTÃO SAÍDA [SAÍDA QUE DESEJA]
                        criar para todos, basicamente a estratégia aqui é criar uma coluna que na linha que começar a coluna vai aparecer o nome e o restante fica null, algo como
                            
                            VENDAS
                            null
                            null
                            PRODUTOS
                            null
                            null 

                            logo apos vamos preencher expandindo para baixo para marcar todas as linhas daquela tabela

                            -> [TRANSFORMAR]
                                -> [PREENCHIMENTO]
                                    -> [PARA BAIXO]
                                            ficando algo como:

                                            VENDAS
                                            VENDAS
                                            VENDAS
                                            PRODUTOS
                                            PRODUTOS
                                            PRODUTOS

                                            logo após só criar referencias para essa tabela que tem todas as tabelas misturadas e na coluna condicional restringir somente ao que nos queremos

    caso uma data ou número venha com padrao errado
    -> [BOTAO ESQUERDO NO SIMBOLO DO TIPO DA COLUNA]
        -> [LOCALIDADE]
                ai só colocar data e personalizar para a região que deseja usar o padrão

# TRABALHANDO COM MODELO FATO E DIMENSÃO (STAR SCHEMA E SNOW FLAKE)

IMPORTANDO TABELAS FATO E DIMENSÃO

    power BI melhor funciona com modelo fato dimensão
        star schema o power BI funciona

    tabelão -> a partir de uma tabela unica ir para tabelas fato e dimensões

    aula só pra importar os arquivos

ORGANIZANDO FATO E DIMENSÃO

    aula organizando os arquivos
        uma boa prática é separar os fatos das dismensões, criando grupos na barra de CONSULTAS
            -> [CONSULTAS]
                -> [BOTÃO DIREITO DO MOUSE NO VAZIO]
                    -> [NOVO GRUPO]
                            ai só dar o nome e depois colocar os arquivos que pertence a esse grupo

    aquelas partes criadas automaticamente pelo power BI quando importa uma pasta não apareceram lá no CAMPOS no POWER BI


RELACIONAMENTO ENTRE TABELAS FATO E DIMENSÃO

    no power BI quando aparece o simbolo sigma (um E misturado com Z) na parte de [CAMPOS] 
        power BI interpretou que essas medidas são IMPLICITAS
            entendeu que são números, e quando utilizado mostrará a SOMA 

    de forma automatica o POWER BI já faz os relacionamentos
        para excluir isso que ele fez automaticamente
            -> [PÁGINA INICIAL]
                -> [GERENCIAR RELAÇÕES]
                    -> ASSINALAR TODOS E [EXCLUIR]

            uma vez que a gente tira tudo isso, toda coluna do tipo numero o POWER BI vai interpretar com o simbolo SIGMA, pois pensa que iremos somar e etc
                para resolver isso 
                    trocamos o tipo da coluna para texto
                        ou
                    fazemos o relacionamento das tabelas

    como fazer o relacionamento no POWER BI por meio do mapa mental no [EXIBIÇÃO DO MODELO]
        -> ARRASTAR A COLUNA QUE FOR CORRESPONDENTE, OU SEJA, QUE ESTEJA INTERLIGANDO AMBOS NA OUTRA COLUNA
                ai da pra mudar a CARDINALIDADE, a DIREÇÃO DO FILTRO CRUZADO  e também tornar ATIVO ou NÃO o relacionamento

    FATO NÃO LIGA COM FATO
        já dimensão pode ligar com dimensão
            e também fato pode se ligar com dimensão que se liga com fato


OTIMIZANDO O MODELO E CRIANDO SINÔNIMOS



CRIANDO COLUNA CALCULADA E ORGANIZAÇÃO DE COLUNAS/MEDIDAS POR PASTA

