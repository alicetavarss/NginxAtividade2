# Configuração do Nginx para Redirecionamento (Roteamento) em Aplicações ReactJS

## Passo a Passo de Configuração:

### 1- Acessar o Servidor e Localizar o Arquivo de Configuração:

Conecte-se ao seu servidor Linux via SSH e abra o arquivo de configuração do seu site no Nginx:
```
sudo nano /etc/nginx/sites-available/default
```
    
### 2- Ajustar o Bloco de Configuração do Nginx:

  No arquivo de configuração, você deve garantir que a diretiva try_files esteja presente dentro do bloco location /.

  Exemplo de configuração completa e corrigida:

  ```
  server {
  listen 80;
  server_name localhost;

  root /var/www/html/build;
  index index.html index.htm;

  location / {
     try_files $uri$uri/ /index.html;
  }

  error_page 404 /index.html;

  }
```

>A linha essencial é "try_files $uri$uri/ /index.html;". É ela quem garante o funcionamento do React Router ao atualizar a página.

### 3- Validar a Sintaxe da Configuração:

Antes de reiniciar o Nginx, verifique se não há erros de sintaxe nos arquivos:

`sudo nginx -t`

### 4-Recarregar o Servidor Nginx:

Aplique as alterações recarregando as configurações do Nginx:

`sudo systemctl reload nginx`

### 4- Validação do Teste:

  Acesse a aplicação React no seu navegador.
  
  Navegue até uma rota interna (ex: http://seu-ip/dashboard).
  
  Recarregue a página (F5 ou Ctrl + R).

  >Resultado esperado: A página deve recarregar normalmente exibindo o conteúdo da rota, sem apresentar o erro 404.
