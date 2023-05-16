* A saida para internet dos dispositivos do backend será pelo outbound rule do loadbalancer
* Private-endpoint para o Storage e sql
* Criar forward para 168.63.129.16 à partir do DNS on-premises para que a rede interna atinga o storage por dentro da VPN
* O plano para o plan do webapp deve ser o V3 premium por causa do autoscale
* Ter redundancia em tudo que possível
* É preciso adicioanar o dominio .com.br ao sistema
* Management group
