# Documentação

## Introdução
<p>Um catálogo de dados é um conceito geral das clouds presentes nos mercados, existindo opções de terceiros ou nativas das próprias clouds. Entende-se que um catálogo de dados possibilita ao criador registrar e transparecer as caracteristicas de cada tabela criada, desde uma descrição geral até o detalhamento de metadados de ingestão, governancia de dados e existência de dados sensíveis.</p>

## Motivação
 <ul>
    <li>Forte crescimento no número de tabelas nas zonas raw e curated</li>
    <li>Necessidade de entendimento lógico sobre as tabelas já criadas.</li>
    <li>Baixa documentação histórica sobre as tabelas criadas por diferentes responsáveis.</li>
    <li>Necessidade de implantação de níveis de segurança para limitar a visualização de certos categorias dados sensíveis.</li>
    <li>Necessidade de adequação à determinadas práticas de lGPD.</li>
</ul>

## Objetivo

<p>Democratizar o acesso a informações importantes através de um catálogo de dados estuturado que viabilize a exploração, descoberta e colaboração adequados à LGDP. Iniciar as definições de papéis e responsabilidades com suas respectivas permissões.</p>

## Parâmetros de Sucesso
<ul>
    <li>Definição clara das zonas do data lake que receberão o catálago de dados.</li>
    <li>Implantação no catálago de e dados os metadados de ingestão e governância.</li>
    <li>Definição da ferramenta de front para visualização facilitada do catálago de dados.</li>
    <li>Definição dos grupos de personas e seus respectivos níveis de roles.</li>
    <li>Implementação via policy tags dos níveis de acesso aos dados.</li>
</ul>

## Infraestrutura
### <i>Definição</i>
  <ul>
    <li><b>Data Catalog -> </b> Ferramenta para compilar e visualizar os metadados(informações sobre os dados) gerados pelo processo de ETL ou descritos pelo próprio autor do conjunto de dados(e.g. tabelas em zonas raw ou curada).</li>
    <li><b>Tag -> </b> Entende-se por tag uma marcação de campos com tipos e objetivos previamente definidos. Em resumo, pode ser visto como o equivalente à um "carimbo" com campos pré-formatos cujo valores irão variar em cada conjunto de dados.</li>
    <li><b>Tag Template -> </b> Em resumo são modelos de estruturas de tags pré-definidas com objetivos distintos. Como ilustrução temos o modelo de governância cujo os campos têm o objetivo de registrar as caracteríticas de existência, controle e objetivo daquele conjunto de dados que estão sendo criado por determinado usuário, em contra partida o modelo de ingestão possui os metadados do processo de ETL(e.g. tempo de duração, numero de linhas ingeridas, status, etc). Cada modelo será detalhado no próximo tópico desta documentação.</li>
 </ul>

### Modelos de Tags
<u><i>Data Governance</i></u>
<br><u>Este templante será de inteira responsabilidade do dono do conjunto de dados. O preenchimento será realizado via arquivo yaml no repositório airflow-dags. </u> 
<ul>
    <br>
    <li>
        <b>business_owner (string) -> </b> Responsável pela criação do conjunto de dados
        <ul>
            <br>
            <li>Ex. Ronald Rander</li>
            </br>
        </ul>
    </li>
    <li>
        <b>data_classification (Enumerate) -> </b> Nível de classificação do conjunto de dados de negócio.
        <ul>
            <br>
            <li>interno</li>
            <li>sensivel</li>
            <li>confidencial</li>
            <br>
        </ul>
    </li>
    <li>
        <b>approved_by_governance (booleno) -> </b> Status de aprovação pela equipe de governância.
        <ul>
            <br>
            <li>True</li>
            <li>False</li>
            <br>
        </ul>
    </li>
    <li>
        <b>approved_by_governance_date (Datetime) -> </b>Data de aprovação pela equipe de governância.
        <ul>
            <br>
            <li>Ex. 01/01/2021</li>
            <br>
        </ul>
    </li>
    <li>
        <b>data_lifecyle (Enumerado) -> </b>Estágio de maturidade atual do conjunto de dados.
        <ul>
            <br>
            <li>teste</li>     
            <li>desenvolvimento</li>
            <li>homologacao</li>
            <li>producao</li>
            <li>outros</li>
            <br>
        </ul>
    </li>
    <li>
        <b>encrypted_data_asset (Booleano) -> </b> Status do nível de criptografia do conjunto de dados.
        <ul>
            <br>
            <li>True</li>
            <li>False</li>
            <br>
        </ul>
    </li>
    <li>
        <b>has_pii (Booleano) -> </b> Status da presença de identificadores pessoais sensíveis.
        <ul>
            <br>
            <li>True</li>
            <li>False</li>
            <br>
        </ul>
    </li>
    <li>
        <b>pii_type (Enumerado) -> </b> Tipo de identificador pessoal sensível.
        <ul>
            <br>
            <li>cartao_credito</li>
            <li>dados_bancarios</li>
            <li>email</li>
            <li>telefone</li>
            <li>endereco</li>
            <li>cpf</li>
            <li>cnpj</li>
            <li>outros</li>
            <br>
        </ul>
    </li>
    <li>
        <b>source_system (Enumerado) -> </b>Especificação da fonte  principal de origem do conjunto de dados. 
        <ul>
            <br>
            <li>firebase</li>     
            <li>braze</li>           
            <li>take_blip</li>
            <li>google_analytics</li>
            <li>amplitude</li>
            <li>adjust</li>
            <li>playstore</li>
            <li>prod_gateway</li>
            <li>db_vehicles</li>
            <li>db_license</li>
            <br>
        </ul>
    </li>
</ul>
<u><i>Data Ingestion</i></u>
<br><u>O preenchimento deste template será de responsabilidade do sistema de mensageria(xcons) do airflow.</u>
<ul>
    <br>
    <li>
        <b>etl_job_status (Enumerado) -> </b>Status de acompanhamento da ultimo ETL realizado no conjunto de dados.
        <ul>
            <br>
            <li>running</li>     
            <li>sucess</li>           
            <li>failed</li>
            <li>interrupted</li>
            <li>skipped</li>
            <li>queued</li>
            <li>scheduled</li>
            <li>upstream_failed</li>
            <li>removed</li>
            <li>none</li>
            <br>
        </ul>
    </li>
    <li>
        <b>etl_job_start (datetime) -> </b>Data referente ao ínicio d última carga de ETL do conjunto de dados.
        <ul>
            <br>
            <li>Ex. 2021-12-17_22h-36m-52s</li>     
            <br>
        </ul>
    </li>
    <li>
        <b>etl_job_runtime (datetime-segundos) -> </b>Tempo em segundos referente à ultima carga de ETL do conjunto de dados.
        <ul>
            <br>
            <li>Ex. 85</li>     
            <br>
        </ul>
    </li>
    <li>
        <b>etl_data_source (Enumerado) -> </b>Especificação da fonte primária de armazenamento dos dados durante a carga de ETL do conjunto de dados.
        <ul>
            <br>
            <li>Storage</li>     
            <li>Big_Query</li>           
            <li>API</li>
            <br>
        </ul>
    </li>
    <li>
        <b>etl_job_end (datetime) -> </b>Data referente ao fim da última carga de ETL do conjunto de dados.
        <ul>
            <br>
            <li>Ex. 2021-12-17_22h-55m-52s</li>     
            <br>
        </ul>
    </li>
    <li>
        <b>etl_log_url (string) -> </b>link url do log de metadados referente à ultima carga ETL do conjunto de dados.
        <ul>
            <br>
            <li>Ex. https://v67e0c0bf2fc754c2p-tp.appspot.com/log?execution_date=2021-12-17T17%3A55%3A36.168385%2B00%3A00&task_id=delete_node_pool-memory_heavy&dag_id=delete-processing-nodepools)</li>     
            <br>
        </ul>
    </li>
    <li>
        <b>num_rows_inserted (decimal) -> </b>Número de linhas inseridas na ultima carga de ETL do conjunto de dados.
        <ul>
            <br>
            <li>Ex. 1250</li>     
            <br>
        </ul>
    </li>
</ul>