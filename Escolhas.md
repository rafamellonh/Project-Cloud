## Breve resumo

### Azure Application Gateway

* O Azure Application Gateway é um balanceador de carga de aplicativo da Microsoft, que fornece vários recursos e benefícios para o gerenciamento, desempenho e segurança de aplicativos web e  atua na camada 7 . Abaixo alguns dos benefícios incluídos no Application Gateway.

* Roteamento : Ele a faz o roteamento de carga entre os aplicativos, garantido a distribuição de carga equilibrada com base em algumas métricas (regras) assim podendo garantir a melhora do desempenho e a disponibilidade dos aplicativos.
* SSL/TLS : Temos a opção de trabalhar com SSL/TLS offload onde ele descriptografa o conteúdo no listener para depois enviar os dados para o backend pool, assim tirando sobrecarga das aplicações, mas é possível fazer o trafego passar criptografado de ponta a ponta (end to end).
* Dimensionamento : Ele pode ser dimensionado de forma automática, sendo assim expandindo ou reduzindo com base nos padrões na mudança do tráfego.
* Disponibilidade : Com redundância de Zona, podemos mantê-lo seguro quanto a falhas zonais.
* Firewall de Aplicativos : Contém opção de ativação do WAF (Web Application Firewall) que é um serviço que dispoem proteção focada para aplicativos web contra ataques e vulnerabilidades comuns. O WAF é baseado em regras do OWASP (Open Web Application Security Project) que é uma organização sem fins lucrativos que tem como seu objetivo principal fornecer ferramentas, informações e recursos para ajudar as empresas desenvolver, adquirir e manter seus aplicativos seguros.
* Roteamento de URL : Com o roteamento baseado em URL é possível rotear o tráfego para pools de backend conforme a URL da requisição, também podendo ter vários aplicativos em seu backend.
* Redirecionamento de HTTP para HTTPS: 
* Afinidade de sessão : Com esse recurso é possível manter a conexão do usuário no mesmo servidor.
* Páginas de erro personalizadas : O Application gateway permite que você personalize páginas de erro ao invés de exibir erros padrões.
* Reescreve cabeçalhos HTTP e URL : Podemos remover conteúdos do cabeçalho, como url, porta e etc... 

### Azure Web Service

* O WebAPP, serviço de aplicativo do Azure, é uma oferta pas totalmente gerenciada ppara hospedar aplicativos Web.
* Você pode desenvolver usando sua linguagem favorita, tais como Java, PHP, Python, .NET, NET CORE entre outras.
* Os aplicativos são executados e escalados com facilidade, tanto em ambiente Windows quanto Linux.
* Pode ser aplicado em recursos como DevOPs para implantação contiínua. Azure DevOps, GitHub, Docker Hub entre outras fontes.
* Tem integração com outros serviços do Azure, como banco de dados SQL do Azure, Azure Functions, Azure Storate e também o Azure Active Directory.
* Disponibilidade: Possui failover automático, replicação geográfica.
* Possui vários modelos de faturamento.


### Azure LoadBalancer 

* O balanceador de carga do Azure opera na camada 4 da camada OSI.
* Ele distribui os fluxos de entrada que chegam às instâncias do pool de front e backend de forma equilibrada.
* É possível utilizar ele como externo e interno, mas aqui iremos utilizar ele no modo interno.
* Distribui os recursos dentro e entre zonas.
* É possível criar regras de outbound para as máquinas virtuais em seu backend
* Dispoem de verificações de integridade, monitorando a saúde dos recursos.
* Balanceia as cargas dos fluxo em TCP e UDP.

### VMSS - Conjunto de dimensionamento de Máquinas Virtuais

* O VMSS permite criar e gerenciar um grupo de VMs com balanceamento de carga. 
* O número de instâncias de VM pode aumentar ou diminuir automáticamente conforme a demanda ou agendamento definido.
* Fornece alta disponibilidade e resiliência, distribuindo as VMs por zonas de disponibilidaes ou domínios de falha.
* Todas as VMs são criadas a partir da mesma imagem e da mesma configuraçã odo sistema operacional base.
* Trabalha em larga escala chegando até 1000 VMs para imagens padrões do Azure e 600 para uma imagem personalizada.