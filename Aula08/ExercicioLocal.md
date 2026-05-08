# Atividades: Montar duas imagens via VirtualBox

**Objetivo:** Montar duas imagens via VirtualBox. A primeira imagem com a instalação do NetData e a segunda com o Webmin.

## Passos para a Montagem das Imagens

1.  **Baixar a imagem .ova:**
    *   Sua máquina hospedeira já deve possuir o VirtualBox instalado.
    *   A instalação padrão do Linux deve ser feita com usuário `satc` e senha `satc`.
    *   Se já possui uma máquina virtual Linux pronta, pode clonar, evitando a necessidade de baixar novamente.
    *   **Link:** [Ubuntu_SATC.ova](http://example.com/Ubuntu_SATC.ova) (Assumindo que este link é um placeholder e deve ser substituído pelo link real)

2.  **Importar e Configurar a Imagem:**
    *   Após baixar o arquivo `.ova`, importe-o para o VirtualBox.
    *   **Configuração de Rede:**
        *   Antes de ligar, configure a rede da imagem recém-importada como **“Placa em modo BRIDGE”**.
        *   Se estiver na SATC, configure como **NAT** e utilize o redirecionamento de portas para acessar o NetData e o Webmin.

3.  **Verificar e Clonar a Imagem:**
    *   Confira a imagem inicializando com o usuário e senha `satc`.
    *   Após isso, desligue o Linux com `init 0`.
    *   Efetue um clone desta imagem, pois será utilizada na instalação do Webmin.
    *   **Importante:** No clone, lembre-se de trocar o endereço MAC para evitar conflitos de rede.
    *   Comandos de usuário comum devem ser antecedidos de `sudo`.

4.  **Instalação do NetData:**
    *   Acesse o site da NetData.
    *   Em "GET NetData", siga as instruções de instalação na máquina virtual.
    *   **Vídeo Adicional:** Pode ser utilizado como referência para a instalação do NetData.
    *   **Link NetData:** [https://www.netdata.cloud/](https://www.netdata.cloud/)
    *   **Link Adicional:** [https://youtu.be/H-ZxEnYjLfM](https://youtu.be/H-ZxEnYjLfM)

5.  **Instalação do Webmin:**
    *   Acesse o site do Webmin para a instalação.
    *   O Webmin é uma ferramenta completa de administração de servidor Linux.
    *   **Objetivo:** O intuito é visualizar o status do servidor naquele determinado momento, embora ele permita a instalação de serviços e aplicações.
    *   **Comando para instalar pacote Debian:** `dpkg -i <nomepacote.deb>`
    *   **Link Webmin:** [http://www.webmin.com/download.html](http://www.webmin.com/download.html)

6.  **Análise da Documentação:**
    *   Ambos os ambientes (NetData e Webmin) possuem manuais de acesso e instalação em suas documentações.
    *   Estes devem ser analisados a partir das estatísticas do servidor onde se encontram.

## Entrega da Atividade

*   Deve ser entregue uma filmagem de **até 30 segundos**.
*   Apresentar as duas interfaces (NetData e Webmin) sendo acessadas.
*   Mencionar qual a métrica que mais chamou atenção e o porquê.
*   O arquivo deve ser postado no AVA.
*   **Formatos aceitos:** `.avi`, `.mp4` ou `.mpeg`.