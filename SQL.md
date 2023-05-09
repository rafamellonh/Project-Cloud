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

* Managed Instances
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

* Databases
  * SQL Single Database
  * Elastic Pool

 * O gerenciamento da infraestrutura é todo voltado para Microsoft (updates de patchs e etc)


