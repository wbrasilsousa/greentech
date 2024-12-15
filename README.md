# greentech

Eu resolvi dividir em 2 projetos (front e API). `front-greentech` se comunica com `api-greentech` que por sua vez faz todo o trabalho com o banco de dados.

Na raiz do projeto tem um json para o Postman, <a href="https://github.com/wbrasilsousa/greentech/blob/master/GreenTech.postman_collection.json">GreenTech.postman_collection.json</a>

No front eu utilizei um dashboard scaffolding chamado <a href="https://adminlte.io/docs/3.2/index.html">adminlte</a> ele utiliza o Auth do Laravel, como eu não queria que o front se comunicasse com o banco de dados para fazer a autenticação, criei um middleware customizado para permitir a autenticação via API, <a href="https://github.com/wbrasilsousa/front-greentech/blob/master/app/Http/Controllers/CustomAuthController.php">CustomAuthController</a> e <a href="https://github.com/wbrasilsousa/front-greentech/blob/master/app/Http/Controllers/CustomRegistrationController.php">CustomRegistrationController</a> fazem o serviço de login e registro.

`front-greentech` vai criar uma base sqlite default apenas para gerenciamento das sessões.

Obs: Comitei também os arquivos `.env` para facilitar a instalação.

Caso não seja familiarizado com o projeto <a href="https://laradock.io/docs/Intro">laradock</a>, segue um passo a passo para a instalação.

1. Clonar recursivamente
```
git clone --recurse-submodules https://github.com/wbrasilsousa/greentech.git
```

2. Startar os containers, dentro do diretorio `lamp-with-laradock`
```
docker-compose up
```

3. Ainda em `lamp-with-laradock`
```
docker-compose exec --user=laradock workspace bash
```

4. Comandos default do laravel em `front-greentech` e `api-greentech`
```
composer install
php artisan migrate
```

5. Configurar o hosts
```
127.0.0.1 api-greentech.test
127.0.0.1 front-greentech.test
```
