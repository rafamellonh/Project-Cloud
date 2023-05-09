* Dados estruturados

## IaaS

* SQL Virtual Machine : [Docs](https://learn.microsoft.com/en-us/azure/azure-sql/virtual-machines/?view=azuresql)
  * A migração direta para o Azure Database é mais complicada devido qualquer tipo de personalização
  * Recomenda-se migrar para Managed Instances
  * É nessário todo o tipo de gerenciamento, EX: Rede, updates do Windows, pacthes do SQL, versões do SQL e também algum tipo de redundância
  * O lado positivo é que você tem acesso total ao SQL podendo fazer todo tipo de modificações pois tem acesso direto ao sistema operacional
  * Facilita o troubleshoot pois temos acesso ao sistema operacional
  * É possivel utilizar o licenciamento de [Software assurance](https://www.microsoft.com/pt-br/licensing/licensing-programs/software-assurance-default)
    * Ganha na econômia do licenciamento

## PaaS

* Managed Instances : [Docs](https://learn.microsoft.com/pt-br/azure/azure-sql/managed-instance/?view=azuresql)
  * Single instance
  * Instance Pool

  * É um meio termo entre Azure Databases e Azure VM SQL
  * Tem uma facilidade maior para migrações on-premises para cloud
  * Integração direto com o Virtual Network, pode ser integrado diretamente na VNET
  * Pode ser usado como ``` Single Instance ``` ou ```Instance Pool ```
  * É possível ter o gereciamento total do banco mesmo rodando como plataforma
  * Conectividade com usuários do AD local através do ADConnect
  * Downtime de quase 0 para a migração
  * Gerenciamento de Failover Groups
  * ``` Segundo a Microsoft, você terá um retorno de 212% após 3 anos ```


* Databases : [Docs](https://learn.microsoft.com/pt-br/azure/azure-sql/database/?view=azuresql)
  * SQL Single Database
  * Elastic Pool

 * O gerenciamento da infraestrutura é minimizado, todo voltado para Microsoft (updates de patchs e etc)
 * É uma solução PaaS
 * Não tem integração direta com VNET's
 * Totalmente Serverless compute
 * É indicado para ambientes onde o tamanho do banco é acima de 100TB
 * Autoscaling
 * Trabalha com ```Single Database``` ou ```Elastic Pool```
 * Suporta [``` Private Link ```](https://learn.microsoft.com/pt-br/azure/private-link/private-link-overview)
 * SLA de ``` 99.995% ```
 * SLA : ``` RPO ``` de 5 segundos e ``` RTO ``` de 30 segundos. [RPO/RTO](https://learn.microsoft.com/pt-br/azure/azure-sql/database/business-continuity-high-availability-disaster-recover-hadr-overview?view=azuresql)


## [Scalability](https://learn.microsoft.com/en-us/azure/azure-sql/database/elastic-scale-introduction?view=azuresql)

* SQL elastic pools
  * Para cenários onde não conseguimos prever a demanda necessária para suprir o funcionamento
  * Dentro do pool é possível colocar diversos databases dentro dele, e podemos aumentar ou reduzir a qualquer momento
  * É possível aumentar/diminuir os recursos do pool quando necessário
  * Escalonamento vertical
  * Basic:
    * Pode ser escalado até 5 eDTUs por DB.
    * Pode ter de 100-1200 eDTUs para utilizar de forma compartilhada no Pool
  * Standard
    * Pode ser escalado até 100 eDTUs por DB.
    * Pode ter de 100-1200 eDTUs para utilizar de forma compartilhada no Pool
  * Premium
    * Pode ser escalado até 1000 eDTUs por DB.

  * Calculador [DTU](https://dtucalc.azurewebsites.net/)


* Horizontal Scaling by [Sharding](https://learn.microsoft.com/pt-br/azure/azure-sql/database/elastic-scale-introduction?view=azuresql)
  * Quando você tem diferentes seções de bancos de dados residindo em diferentes partes do mundo
* Elastic database tools
  * Para quando você tem uma dependência de ferramentas comerciais ou de integração de dados como Power BI, Cognos, Excel onde a consulta deve ser 
    realizado uma consulta em multiplos databases
  * Ele é capaz de fazer consultar, querys em diversos databases segnmentados
    * Com a ferramenta Elastic database Tools

 * Sharding :
    * Os dados são dividos horizontalmente e destribuidos em multiplos servidores de DB.
    * Com uma estrutura de vários servidores, onde cada um tem apenas uma parte do dado e responde somente a consultas relacionadas a essa parte.
    * Ele tem um Shard map manager que seria um gerenciador que responde por todos os DBs

## [Availability](https://learn.microsoft.com/pt-br/azure/azure-sql/database/high-availability-sla?view=azuresql&tabs=azure-powershell)

* Por padrão no Azure já tem uma camada básica de alta disponibilidade
* Temos praticamente duas formas de disponibilidade

* General Purpose/Standard Tier (Azure SQL Database)
  * Trabalha no modelo cluster ```Failvober ```
  * O gerenciamento da estrutura de alta disponibilidade do Azure é gerenciada pelo Azure Service Fabric
  * Ele tem uma réplica principal (uma VM) e mais nós que estão separados, os pairs
  * Essas instâncias tem um SSD local onde armazena o tempdb para poder dar agilidade nas transações do banco
  * Os discos de logs e de Data, serão armazenados dentro de um Storage account Premium (geralmente)
  * O Backup é realizado em um armazenamento standard do Storage account
  * Se a instância principal vier a apresentar falhas e ficar offline, o Service Fabric vai fazer o failover para outra instância que está no failover
  * Com os dados nos Storage accounts, o apontamento na VM será diratamente para o Storage
  * Projetado para cargas de trabalho comuns
  * Computação e armazenamento equilibrados orientados para o orçamento
  * Usa nós com capacidade sobressalente para criar novas instâncias do SQL Server
  * 

* Premium/Critical (Azure SQL Database)
  * Chega a ter até 100% de disponibilidade
  * Trabalha no modelo ``` AlwaysON```, onde todas as instâncias esão ativas e com os dados
  * A parte de dados e de logs estão em todas as máquinas localmente podendo as solicitações serem respondidads por qualquer instância
  * O Backup é igual ao tier Standard
    * O Backup é realizado em um armazenamento standard do Storage account
  * Projetado para aplicativos OLTP
  * Alta taxa de transação e baixa latência de E/S
  * Oferece a maior resiliência a falhas usando várias réplicas isoladas
  * Implanta um grupo de disponibilidade sempre ativado usando várias réplicas atualizadas de forma síncrona

* Hyperscale Tier/ Business Critical (Azure SQL Database)
  * Projetado para bancos de dados OLTP muito grandes - até 100 TB
  * Capaz de dimensionar automaticamente o armazenamento e dimensionar a computação muito rapidamente
  * Captura backups instantâneos (usando snapshots)
  * Restaura em minutos em vez de horas e dias
  * Amplie ou reduza em tempo real para acomodar as mudanças na carga de trabalho
  * Todos as partes são separadas e replicadas
    * Nodes computacionais
    * Server pages (cache)
      * Usa RBPEX Data Cache : 
        * É um cache de dados inteligente de baixa latência que minimiza a necessidade de buscar dados de servidores de páginas remotas
    * Log service
    * Storages
  * Pode ter nodes somente leitura assim podendo apontar aplicações que necessitam somente ler os dados para esses nodes