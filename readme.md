# SENDA - GNRE

SENDA - GNRE é um projeto de integração entre o sistema Senda ERP e os portais de geração GNRE.

## Documentação
SENDA - GNRE é baseado no projeto: https://github.com/nfephp-org/sped-gnre mantendo-se atualizado conforme as necessidades do sistema Senda ERP.

## Instalando o Servidor PHP
### Para plataforma windows:
- Recomenda-se instalar para servidor, o XAMPP com versão PHP 7.0.
- Download do XAMPP: "https://www.apachefriends.org/xampp-files/7.0.23/xampp-win32-7.0.23-0-VC14-installer.exe" 
- Após concluir o download do XAMPP, executar o arquivo recém baixado e seguir os passos do assistente de instalação.
- Antes de iniciar o serviço, verifique se a porta padrão a ser utilizada pelo XAMPP não está em uso por outra aplicação (Por padrão o XAMPP utiliza as portas 80 e 443). Caso tenha o skype instalado, verificar se o mesmo não esta usando as portas 80 e 443 (Menu Ferramentas - Opções - Avançado - Conexão).
- Habilitar Extenções PHP no arquivo php.ini:
  - php_soap
  - php_openssl
  - php_gd2
  - php_pdo_pgsql
- Ajustar o parametro max_execution_time no php.ini para 500;

#### Após configurar o PHP.ini - Adicionar a pasta xampp/apache/bin às variáveis de ambiente:
- Siga até as configurações do sistema, mais especificamente nas variáveis de ambiente do sistema. 
- Adicione o caminho de instalação do xampp, exemplo: "C:\xampp\apache\bin" em PATH.
- Pare o XAMPP e inicie novamente como administrador.

#### Verificando a instalação
- Antes de processeguir verifique através do terminal se o openssl esta instalado corretamente, através do comando:
```terminal
openssl version
```
- Verifique se o comando foi reconhecido pelo sistema, caso contrário verifique novamente se a variável de ambiente foi configurada corretamente (pode ser necessário fechar o terminal CMD e abrir novamente).

#### Estrutura de Pastas
- Recomenda-se utilizar a seguinte estrutura de pasta para instalação:
  * ..xampp/htdocs
    * senda
        * empresa
            * certificado
            * senda-gnre (copiar para esta pasta a aplicação baixada - pasta raiz da aplicação)
        * empresa
            * certificado
            * senda-gnre (copiar para esta pasta a aplicação baixada - pasta raiz da aplicação)

#### Ajustando o arquvivo de configuração .ENV
- Assim que as dependências forem baixadas e o serviço esteja devidamente configurado conforme os passos anteriores, acesse a pasta raiz onde foi realizada a instalação.
- Configurando os dados da conexão e certificado do cliente:
    * Abra o arquivo [.env](http://github.com/sendaxe/senda-gnre/blob/master/.env) que esta na raiz do projeto e configure os dados de acesso conforme o arquivo [.env.example](http://github.com/sendaxe/senda-gnre/blob/master/.env.example)

#### Preparando o Senda para gerar GNRE
- Antes de iniciar a aplicação PHP verifique as configurações no cadastro de empresas do Senda.
- No cadastro de empresas, marque a opção "Gera GNRE" na aba "Configurações" - "Contábil/Fiscal" - "Principal".
- Após marcar a opção "Gera GNRE", configure as informações que estarão disponíveis na aba GNRE.
- Informe a url que estará sendo utilizada para rodar o serviço GNRE na opção URL. Exemplos: 
    * http://192.168.133.1/senda/empresa/senda-gnre/public
    * http://endereco-ip/senda/empresa/senda-gnre/public
    * http://nome-da-maquina-na-rede/senda/empresa/senda-gnre/public

### Configurando a URL de Acesso
- Acesse o sistema através da URL da pasta raiz, por exemplo: "http://localhost/sendaxe/senda-gnre/public" 
- Se preferir crie um arquivo .BAT (windows) com os comandos abaixo:
``` terminal
cd C:\xampp\htdocs\sendaxe\senda-gnre
php -S localhost:8000 -t ./public
pause
REM Acesse a url: http://localhost:8000 através de um navegador.
```

### Atualizando o certificado
- Sempre que o certificado estiver expirando será necessário atualizar o arquivo através da URL: "/configuracoes" disponível na aplicação.
- No primeiro acesso também deverá ser realziado este procedimento.

### Atualizando as receitas
- Assim que os passos anteriores forem realziados, abra a aplicação e acesse a opção para atualizar receitas, neste momento deverá atualizar as informações específicas de cada estado.
- No primeiro acesso também deverá ser realziado este procedimento.

## Licença
[MIT license](http://opensource.org/licenses/MIT)
