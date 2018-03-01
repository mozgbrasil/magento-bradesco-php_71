[checkmark]: https://raw.githubusercontent.com/mozgbrasil/mozgbrasil.github.io/master/assets/images/logos/logo_32_32.png "MOZG"
![valid XHTML][checkmark]

[url-method]: http://www.bradesco.com.br/
[requerimentos]: http://mozgbrasil.github.io/requerimentos/
[contact-bradesco]: http://www.bradesco.com.br/bradesco/ecp/comunidade.do?app=portal&pg=20004&view=faleconosco
[tickets]: https://cerebrum.freshdesk.com/support/tickets/new
[preco]: http://www.cerebrum.com.br/preco/
[getcomposer]: https://getcomposer.org/
[uninstall-mods]: https://getcomposer.org/doc/03-cli.md#remove
[artigo-composer]: http://mozg.com.br/ubuntu/composer
[ioncube-loader]: http://www.ioncube.com/loaders.php
[acordo]: http://mozg.com.br/acordo-licenca-usuario-final/

# Mozg\Bradesco

## Sinopse

Integração ao [Bradesco][url-method]

## Motivação

Atender o mercado de módulos para Magento oferecendo melhorias e um excelente suporte

## Demonstração

[![Clique para visualizar o vídeo](https://img.youtube.com/vi/1iNsHpI-Ya8/0.jpg)](https://youtu.be/1iNsHpI-Ya8 "Clique para visualizar o vídeo")

## Suporte / Dúvidas

Para obter o devido suporte [Clique aqui][tickets], relatando o motivo da ocorrência o mais detalhado possível e anexe o print da tela para nosso entendimento

## Preço

[Clique aqui][preco]

## Recursos do módulo

- [✓] Transação
- [✓] Consulta

## Característica técnica

No checkout é feito o processo de autorização

Na página de sucesso é exibido a janela que acessa o tipo de pagamento

Via CRON deve ser processado a notificação da transação,

No processamento da notificação caso o pagamento seja confirmado, deve ser alterado o "state/status" do pedido para "processing" ou seja "Processando", liberando as ações para processar a fatura e o envio

Quando o pedido é enviado o status é alterado para "complete" ou seja "Completo"

Antes do envio da mercadoria, sempre confira as informações do pedido, se o status da transação está sendo exibido que o pagamento foi confirmado, inclusive junto a operadora financeira se a transação foi capturada, caso algo esteja inconsistente será necessário cancelar o pedido até a correção da ocorrência

## Setup Cron

Para o uso do método é necessário ativar a <a href="https://pt.wikipedia.org/wiki/Crontab">CRON</a> para o <a href="https://magento.com/">Magento</a>

<a href="https://mozg.com.br/dicas/dicas-magento1#como-ativar-a-cron-no-magento">Clique aqui</a> para visualizar o documento da MOZG

Certifique-se de que ação esteja sendo executado a cada minuto

Esse módulo usa o cronjob para processar as notificações

O módulo executa as notificações que foram recebidas há pelo menos 5 minutos.

## Testando na Heroku

Gostaria de apresentar o aplicativo que disponibilizei para a plataforma Heroku

Com apenas 1 clique, o aplicativo cria sua loja virtual usando a plataforma de comércio eletrônico Magento e instala os módulos da MOZG

[https://github.com/mozgbrasil/heroku-magento#descrição](https://github.com/mozgbrasil/heroku-magento#descrição)

## Instalação - Atualização - Desinstalação - Desativação

--

Sugiro "printar" as telas com todos os procedimentos executados

Envie para nós as imagens das telas na eventualidade de quaisquer dificuldades

--

Este módulo destina-se a ser instalado usando o [Composer][getcomposer]

Execute o seguinte comando no terminal, para visualizar a existencia do Composer e sua versão

    composer --version

Caso não tenha o Composer em seu ambiente, sugiro ler o seguinte artigo [Clique aqui][artigo-composer]

--

É necessário que o servidor tenha o suporte a extensão [ionCube PHP Loader][ioncube-loader]

Execute o seguinte comando no terminal, para visualizar a existencia da extensão nesse ambiente denominado PHP CLI

	php -v

Para visualizar se essa extensão está ativa em seu servidor no ambiente denominado PHP WEB

Certique se da presença do arquivo phpinfo.php na raiz do seu projeto

    <?php phpinfo(); ?>

Caso não exista o arquivo phpinfo.php na raiz do projeto Magento, crie o mesmo adicionado o conteúdo acima

Acesse o arquivo pelo browser

Em seguida pesquise pelo termo "ionCube PHP Loader"

Caso o seu servidor não tenha o suporte a extensão, entre em contato com sua empresa de hospedagem e peça para que eles ativem a extensão

Caso tenha a permissão e queira ativar a extensão, [Clique aqui][ioncube-loader]

Em "Loader Downloads API", efetue download do pacote compatível com o seu servidor

Descompacte o pacote e faça upload do arquivo "loader-wizard.php" para seu servidor, onde será demonstrado o passo a passo para a ativação da extensão

[Clique aqui](https://youtu.be/GZ2J6MLkko4) para ver os processos executados

--

Na presença do "ionCube PHP Loader" efetue o download do seguinte arquivo e coloque na raiz do seu servidor e acesse, se funcionar quer dizer que o "ionCube" está lendo esse tipo de encriptação

https://raw.githubusercontent.com/mozgbrasil/heroku-magento/master/phpinfo-ioncube-encoder10-x86-64-php_71.php

--

Para utilizar o(s) módulo(s) da MOZG é necessário aceitar o [Acordo de licença do usuário final][acordo]

--

Sugiro manter um ambiente de testes para efeito de testes e somente após os devidos testes aplicar os devidos procedimento no ambiente de produção

--

Sugiro efetuar backup da plataforma Magento e do banco de dados

--

Antes de efetuar qualquer atualização no Magento sempre mantenha o Compiler e o Cache desativado

--

Certique se da presença do arquivo composer.json na raiz do seu projeto Magento e que o mesmo tenha os parâmetros semelhantes ao modelo JSON abaixo

    {
      "minimum-stability": "dev",
      "prefer-stable": true,
      "license": [
        "proprietary"
      ],
      "repositories": [
        {
          "type": "composer",
          "url": "https://packages.firegento.com"
        }
      ],
      "extra": {
        "magento-root-dir": "./",
        "magento-deploystrategy": "copy",
        "magento-force": true
      }
    }

Caso não exista o arquivo composer.json na raiz do projeto Magento, crie o mesmo adicionado o conteúdo acima

### Para instalar o módulo execute o comando a seguir no terminal do seu servidor no diretório do seu projeto

    composer require mozgbrasil/magento-bradesco-php_71:dev-master

Você pode verificar se o módulo está instalado, indo ao backend em:

    STORES -> Configuration -> ADVANCED/Advanced -> Disable Modules Output

--

### Para atualizar o módulo execute o comando a seguir no terminal do seu servidor no diretório do seu projeto

Antes de efetuar qualquer processo que envolva atualização no Magento é recomendado manter o Compiler e Cache desativado

    composer update

Na ocorrência de erro, renomeie a pasta /vendor/mozgbrasil e execute novamente

Para checar a data do módulo execute o seguinte comando

    grep -ri --include=*.json 'time": "' ./vendor/mozgbrasil

--

### Para [desinstalar][uninstall-mods] o módulo execute o comando a seguir no terminal do seu servidor no diretório do seu projeto

    composer remove mozgbrasil/magento-bradesco-php_71

--

### Para desativar o módulo

1. Antes de efetuar qualquer processo que envolva atualização sobre o Magento é necessário manter o Compiler e Cache desativado

2. Caso queira desativar os módulos da MOZG renomeie a seguinte pasta app/code/local/Mozg

A desativação do módulo pode ser usado para detectar se determinada ocorrência tem relação com o módulo

## Como configurar o método de pagamento

Para configurar o método de pagamento, acesse no backend em:

    STORES -> Configuration -> Sales/Payment Methods -> Bradesco (powered by MOZG)

Você terá os campos a seguir

### Bradesco Meios de Pagamentos - Configurações Padrão

#### Configurações necessárias

##### • **Modo Teste ou Produção**

Deve ser informado o devido ambiente

##### • **Merchant ID ou "MID" para o ambiente de teste**

Ao se logar em

https://homolog.meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp

Na parte superior direita temos essa informação como MID

##### • **Chave de Segurança para o ambiente de teste**

Em

https://homolog.meiosdepagamentobradesco.com.br/gerenciadorapi/meiopagamento/form

É possível gerar a chave de segurança caso não tenha definido

##### • **Merchant ID para o ambiente de produção**

A informação deve ser fornecido pelo Bradesco

##### • **Chave de Segurança para o ambiente de produção**

A informação deve ser fornecido pelo Bradesco

#### Avançado: Processamento de Pedidos Magento

##### • **Status do pedido: ordem de criação**

Status dos pedidos recém-criados, antes da confirmação de resultado de pagamento via notificações de servidor da operadora

##### • **Status do pedido: autorização de pagamento**

Status dos pedidos após autorização confirmada por uma notificação de AUTORIZAÇÃO da operadora

##### • **Status do pedido: pagamento confirmado**

Status dos pedidos após captura confirmada por uma notificação de AUTORIZAÇÃO da operadora

##### • **Status do pedido: cancelamento de pedido**

Status dos pedidos após cancelamento confirmada por uma notificação de CANCELAMENTO da operadora

Se as encomendas já estiverem faturadas, não poderão ser canceladas

##### • **Status do pedido: captura de pagamento (produtos virtuais)**

Selecione somente o status atribuído ao estado concluído, deixe vazio para usar o mesmo que os produtos normais

##### • **Status do pedido: Reembolsado**

Status dos pedidos após reembolso confirmada por uma notificação de REEMBOLSO da operadora

##### • **Status do pedido: Reembolsado Parcial**

Status dos pedidos após reembolso (parcial) confirmada por uma notificação de REEMBOLSO_PARCIAL da operadora. Recomendamos que não defina este status e deixe Magento decidir o status.

##### • **Status do pedido: pedidos pendentes**

Status dos pedidos após notificação de PENDENCIA da operadora

##### • **Tipo de Captura**

Imediato é o padrão

Defina como manual se você quiser executar a captura de fundos manualmente mais tarde

##### • **Criar uma fatura pendente (apenas para captura manual)**

Isso criará uma fatura pendente se a notificação de AUTORIZAÇÃO for recebida.

 Nota: isto fará com que Magento empurre todas as encomendas para o estado: 'Processamento' uma vez que a factura é criada, ignorando todas as outras definições.

##### • **Status do pedido: Capturar no embarque**

Se você habilitar esta função será feito uma solicitação de captura para a operadora se você fizer o envio

##### • **Ativar Descancelar pedido**

Se uma pedido é cancelada por algum motivo, mas recebeu uma notificação de que o pagamento é autorizado, isso cancelará automaticamente o pedido

##### • **Cancelamento\Reembolso automático quando o pedido é cancelado**

Ativar / Desativar reembolso automático ao cancelar um pedido

##### • **E-mail da fatura**

Ativar / desativar atualizações de e-mails

##### • **Enviar e-mail de notificaçao do status do pedido**

Ativar / desativar e-mails de atualização para todas as alterações no status do pedido para o cliente

##### • **Ativar log de depuração**

Deve ser armazenado os processos do módulo em var/log/

O arquivo

DATE_mozg.log

se trata de log do módulo sendo um log mais detalhado contendo todos os processos inclusive das execuções realizadas pelas bibliotecas externas do módulo

O arquivo

payment_METHOD.log

#### Avançado: Bradesco Notificações

##### • **Ignorar notificação de reembolso**

Se o reembolso for feito na operadora, e a mesma enviar uma notificação de reembolso para o Magento, deve ser criado automaticamente uma nota de crédito. Se você definir essa configuração como 'Sim', isso não acontecerá porque ele não processará nenhuma das notificações de REEMBOLSO recebidas.

<!--
#### Avançado: Contratos de faturamento

##### • **Tipo de Contrato**

Quando ativado, os usuários podem salvar seus cartões de crédito e suas autorizações

ONECLICK exigirá a entrada do CVC para pagamentos subsequentes, enquanto RECURRING não.
-->

#### Avançado: Experiência de Checkout

##### • **Redirecionar o destino após o cancelamento**

Determina como os compradores são redirecionados após cancelar um pagamento.

##### • **Método de pagamento método de renderização**

Determina se os métodos de pagamento serão exibidos com seu logotipo ou apenas o nome.

##### • **Idioma local (opcional)**

Isso substituirá o local do cliente padrão do armazenamento do Magento.

Deixe vazio para deixar Magento decidir (Ex: nl_NL)

##### • **Código do país ISO (opcional)**

Isso irá substituir o país do endereço de faturamento do comprador ao determinar quais métodos de pagamento serão exibidos.

### Boleto Bradesco

#### • **Ativar**

Para "ativar" ou "desativar" o uso do método

#### • **Ordem de exibição**

É a ordem apresentada em métodos de entrega no passo de fechamento de pedido

#### • **Título**

Nome do método que deve ser exibido

#### • **Pagamentos aplicáveis aos países**

Você pode definir se o método deve funcionar para "Todos os Países aceito" ou "Especificar Países "

#### • **Pagamentos específicos aos países**

Você deve selecionar os países que o método deve ser funcional

#### • **Nome do beneficiário/cedente**

Nome do beneficiário/cedente

#### • **Carteira**

Carteira

#### • **Vencimento**

Vencimento

#### • **Logo**

Logo

O tamanho da imagem deve ser de 120px largura por 80px de altura

#### • **Mensagem de cabeçalho exibida no topo do boleto**

Mensagem de cabeçalho exibida no topo do boleto

#### • **Instruções (máximo de três linhas)**

Instruções (máximo de três linhas)

#### • **Status do pedido não pago**

Com Boleto é possível pagar menos do que o valor total. Selecione aqui o status, se este for o caso. Se você deixar isso em branco, ele tomará o status de pedido de pagamento autorizado como status padrão

#### • **Status do pedido pago em excesso**

Com Boleto é possível pagar mais do que o valor total. Selecione aqui o status, se este for o caso. Se você deixar isso em branco, ele tomará o status de pedido de pagamento autorizado como status padrão

#### • **Visível em**

Determine a visibilidade desse método de pagamento no frontend e/ou backend do Magento

### Transferência Eletrônica Bradesco

#### • **Ativar**

Para "ativar" ou "desativar" o uso do método

#### • **Ordem de exibição**

É a ordem apresentada em métodos de entrega no passo de fechamento de pedido

#### • **Título**

Nome do método que deve ser exibido

#### • **Pagamentos aplicáveis aos países**

Você pode definir se o método deve funcionar para "Todos os Países aceito" ou "Especificar Países "

#### • **Pagamentos específicos aos países**

Você deve selecionar os países que o método deve ser funcional

#### • **Tipos de Transferência Eletrônica**

Selecione as bandeiras liberadas pela operadora

#### • **Status do pedido não pago**

Com Boleto é possível pagar menos do que o valor total. Selecione aqui o status, se este for o caso. Se você deixar isso em branco, ele tomará o status de pedido de pagamento autorizado como status padrão

#### • **Status do pedido pago em excesso**

Com Boleto é possível pagar mais do que o valor total. Selecione aqui o status, se este for o caso. Se você deixar isso em branco, ele tomará o status de pedido de pagamento autorizado como status padrão

#### • **Visível em**

Determine a visibilidade desse método de pagamento no frontend e/ou backend do Magento

## Perguntas mais frequentes "FAQ"

### Oque fazer após a instalação do módulo ?

Primeiro deve ser feito o teste sobre o ambiente de homologação

Acesse o gerenciador do Bradesco

https://homolog.meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp

Acesse: Configurações -> Meios de Pagamentos

E obtenha as informações

    merchantId=???
    email=???
    chaveSeguranca=???

Atualize essas configurações no método de pagamento no Magento

Crie um pedido de teste de R$ 1,00

Efetue testes de finalização do pedido

Caso seja exibido a transação do pedido

Envie e-mail para a Scopus solicitando homologação dessa integração e solicitando os dados para ser usados em ambiente de produção

#### Como é feito a alteração do statuso dos métodos: Boleto e TEF

Para o processamento do Boleto e TEF, a cada 5 minutos a CRON acessa a operadora para obter o status da transação a fim de efetuar o processamento da notificação

O serviço da CRON "mozg_bradesco_trigger_notification" deve estar operando

#### Como é criado o cabeçalho de autorização para a transação

Abaixo temos uma transação com o seguinte cabeçalho de autorização

    --header 'Authorization: Basic MTAwMDA2ODczOm1WeWFuZzZpZm9GNjNkMWE1UFFqd25GQ3ZrWDM0bV9ZMWVQREpjQms3clE='

Que equivale ao recurso "base64_encode(merchantId:chaveSeguranca)"

Podemos usar o seguinte serviço para codificar a informação

Acesse

https://www.base64encode.org/

e informe

seu_merchantId:sua_chaveSeguranca

No meu caso é os dados a seguir

"100006873:mVyang6ifoF63d1a5PQjwnFCvkX34m_Y1ePDJcBk7rQ"

#### Simulação de autenticação

Abaixo simulação usando o ambiente de teste do bradesco e meus dados, veja que funciona o retorno de autenticação

    merchantId=100006873
    email=suporte@cerebrum.com.br
    chaveSeguranca=mVyang6ifoF63d1a5PQjwnFCvkX34m_Y1ePDJcBk7rQ

suporte@cerebrum.com.br:mVyang6ifoF63d1a5PQjwnFCvkX34m_Y1ePDJcBk7rQ

    curl --request GET https://homolog.meiosdepagamentobradesco.com.br/SPSConsulta/Authentication/100006873 --header 'Content-Type: application/json' --header 'Authorization: Basic c3Vwb3J0ZUBjZXJlYnJ1bS5jb20uYnI6bVZ5YW5nNmlmb0Y2M2QxYTVQUWp3bkZDdmtYMzRtX1kxZVBESmNCazdyUQ==' --data '' --verbose

#### Simulação de transação para boleto

    curl --request POST https://homolog.meiosdepagamentobradesco.com.br/apiboleto/transacao --header 'Content-Type: application/json' --header 'Authorization: Basic MTAwMDA2ODczOm1WeWFuZzZpZm9GNjNkMWE1UFFqd25GQ3ZrWDM0bV9ZMWVQREpjQms3clE=' --data '{
         "merchant_id":"100006873",
         "meio_pagamento":"300",
         "pedido":{
                "numero":"145000639",
                "valor":10000,
                "descricao":"Compra pelo site http://127.0.0.1/public_html/magento-1.9.3.1-dev34/root/"
         },
         "comprador":{
                "nome":"Eula Jackson",
                "documento":"25739569000102",
                "endereco":{
                     "cep":"08215070",
                     "logradouro":"Avenida Córrego do Jacuu",
                     "numero":"12",
                     "complemento":"ap. 23 B",
                     "bairro":"Itaquera",
                     "cidade":"São Paulo",
                     "uf":"CE"
                },
                "ip":"127.0.0.1",
                "user_agent":"Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:53.0) Gecko/20100101 Firefox/53.0"
         },
         "boleto":{
                "beneficiario":"ACME (American Company Makes Everything)",
                "carteira":"25",
                "nosso_numero":"145000639",
                "data_emissao":"2017-05-25",
                "data_vencimento":"2017-06-01",
                "valor_titulo":10000,
                "url_logotipo":"",
                "mensagem_cabecalho":"mensagem de cabecalho",
                "tipo_renderizacao":"2",
                "instrucoes":{
                     "instrucao_linha_1":"- instrucao_linha_1",
                     "instrucao_linha_2":"- instrucao_linha_2",
                     "instrucao_linha_3":"- instrucao_linha_3"
                },
                "registro":null
         },
         "token_request_confirmacao_pagamento":"a784f7b1e854b967da7fc2e2bc91ef2465712196"
    }' --verbose

#### Simulação de transação para transferência eletrônica

    curl --request POST https://homolog.meiosdepagamentobradesco.com.br/transf/transacao --header 'Content-Type: application/json' --header 'Authorization: Basic MTAwMDA2ODczOm1WeWFuZzZpZm9GNjNkMWE1UFFqd25GQ3ZrWDM0bV9ZMWVQREpjQms3clE=' --data '{
         "merchant_id":"100006873",
         "meio_pagamento":"800",
         "pedido":{
                "numero":"145000641",
                "valor":100,
                "descricao":"Compra pelo site http://127.0.0.1/public_html/magento-1.9.3.1-dev34/root/"
         },
         "comprador":{
                "nome":"Eula Jackson",
                "documento":"25739569000102",
                "endereco":{
                     "cep":"08215070",
                     "logradouro":"Avenida Córrego do Jacuu",
                     "numero":"12",
                     "complemento":"ap. 23 B",
                     "bairro":"Itaquera",
                     "cidade":"São Paulo",
                     "uf":"CE"
                },
                "ip":"127.0.0.1",
                "user_agent":"Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:53.0) Gecko/20100101 Firefox/53.0"
         },
         "token_request_confirmacao_pagamento":"a784f7b1e854b967da7fc2e2bc91ef2465712196"
    }' --verbose

### Sobre o retorno "Erro no tratamento da resposta do pagamento. Entre em contato com a loja" que é exibido no uso do ambiente de teste

A Scopus menciona o seguinte

Prezado (a),

Verificamos que a sua URL de Notificação está apresentando erro no Ambiente de Teste, o qual estamos verificando para lhe posicionar.

Em contrapartida a fim de agilizar e para que possa seguir para o Ambiente de Produção o qual a sua URL funcionará corretamente, disponibilizamos a URL:

https://homolog.meiosdepagamentobradesco.com.br/lojatesteapi/

para que possa incluir no campo URL DE NOTIFICAÇÃO do gerenciador.

### Como configurar a URL de notificação

http://SEU_DNS/index.php/mozg_bradesco/process/notification/

### Como alterar a imagem do método

Pode ser adicionado a imagem, contendo qualquer uma das nomenclaturas a seguir

- method-boleto.png
- method-eletronictransfer.png

E adicione a imagem no diretório do seu template

/skin/frontend/<TEMPLATE>/default/images/mozg_bradesco

### Como personalizar os arquivos phtml

Você pode personalizar o arquivo phtml editando o mesmo e em seguida adicionado o arquivo na estrutura de diretório do seu template

A seguir aplicamos o suporte a um template especifico

cp -r app/design/frontend/base/default/template/mozg_bradesco/ app/design/frontend/smartwave/porto/template

### Dados de contato - SCOPUS TECNOLOGIA

Sistema de Pagamento Seguro  
Suporte Técnico  
Scopus Tecnologia  
(11) 3909-3482  
(11) 3909-3637  
kit@scopus.com.br, homologacao@scopus.com.br, comerciobradesco@scopus.com.br

## Manual

https://homolog.meiosdepagamentobradesco.com.br/manual/Manual_BoletoBancario.pdf

https://homolog.meiosdepagamentobradesco.com.br/manual/Manual_ConsultaPedidos.pdf

https://homolog.meiosdepagamentobradesco.com.br/manual/Manual_API_Transferencia.pdf

## Contribuintes

Equipe Mozg

## License

[Comercial License](LICENSE.txt)

## Badges

[![Join the chat at https://gitter.im/mozgbrasil](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/mozgbrasil/)
[![Latest Stable Version](https://poser.pugx.org/mozgbrasil/magento-bradesco-php_71/v/stable)](https://packagist.org/packages/mozgbrasil/magento-bradesco-php_71)
[![Total Downloads](https://poser.pugx.org/mozgbrasil/magento-bradesco-php_71/downloads)](https://packagist.org/packages/mozgbrasil/magento-bradesco-php_71)
[![Latest Unstable Version](https://poser.pugx.org/mozgbrasil/magento-bradesco-php_71/v/unstable)](https://packagist.org/packages/mozgbrasil/magento-bradesco-php_71)
[![License](https://poser.pugx.org/mozgbrasil/magento-bradesco-php_71/license)](https://packagist.org/packages/mozgbrasil/magento-bradesco-php_71)
[![Monthly Downloads](https://poser.pugx.org/mozgbrasil/magento-bradesco-php_71/d/monthly)](https://packagist.org/packages/mozgbrasil/magento-bradesco-php_71)
[![Daily Downloads](https://poser.pugx.org/mozgbrasil/magento-bradesco-php_71/d/daily)](https://packagist.org/packages/mozgbrasil/magento-bradesco-php_71)
[![Reference Status](https://www.versioneye.com/php/mozgbrasil:magento-bradesco-php_71/reference_badge.svg?style=flat-square)](https://www.versioneye.com/php/mozgbrasil:magento-bradesco-php_71/references)
[![Dependency Status](https://www.versioneye.com/php/mozgbrasil:magento-bradesco-php_71/1.0.0/badge?style=flat-square)](https://www.versioneye.com/php/mozgbrasil:magento-bradesco-php_71/1.0.0)

:cat2:
