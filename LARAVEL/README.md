# Laravel

Created: March 14, 2022 1:59 PM
Tags: framework, laravel, php

- LARAVEL 9.x
    
    [LARAVEL 9.x](https://www.notion.so/LARAVEL-9-x-dd35de943c504a0585c18f179c5701b7)
    
    # 
    
- ÍNDICE

# INSTALLATION

- Ter o composer instalado
- Digitar o comando: `composer global require laravel/installer`

# FIRST PROJECT

- Na pasta de projetos, digite: `composer create-project laravel/laravel example-app`
- Abra a pasta do projeto e rode o programa com: `php artisan serve`
- Abra no browser, digitando: [http://localhost:8000](http://localhost:8000)

# ROTAS E VIEWS

Rota: URL que acessa as páginas do projeto.

Views: Representação gráfica das páginas.

- Templates e estruturação em html
- Dados dinâmicos

## ROTAS

Routes > web.php

```php
//get('/', ...) representa a sintaxe da URL, que retornará a função como resposta.
Route::get('/', function () {
//Sempre retorna uma view .blade.php
    return view('welcome');
});
```

### ADICIONAR OUTRAS ROTAS

- Basta copiar e colar a anterior e alterar o nome da view e da rota.

```php
Route::get('/', function () {
    return view('welcome');
});

//Nova rota
Route::get('/contact', function () {
    return view('contact');
});
```

## VIEWS

- Utiliza a engine Blade.
- resources > views
- Crie suas views chamando os arquivos “nome.blade.php”

# **BLADE**

- Template engine HTML do Laravel (permite pegar dados)
- Deixa as views dinâmicas
- Insere tags HTML e dados do banco
- Operadores lógicos disponíveis no Blade

## **RETORNO DE DADOS VIA GET**

- Envio feito pelo arquivo `route > web`

```php
//Retornar variáveis na página 'welcome'
//web.php
Route::get('/', function () {
    $data = "Exemplo de dado retonado via GET";
    //Retornando dados via get
    return view('welcome', ['data' => $data]);
});
```

## **USANDO DADOS DINÂMICOS NO BLADE**

```html
    <body>
        <h1>TESTANDO ENGINE BLADE</h1>
        <ul>
        @if(10 > 5)
            <li>TESTANDO IFs</li>
        @endif
        <li>{{ $data }}</li>
        <!-- O nome dos dados dinâmicos é a chave do array, e não a variável PHP-->
        </li>
    </body>
```

## **ESTRUTURA DE REPETIÇÃO**

- Enviando um array pela função get, no `web.php`:

**FOR:**

```html
    <h1>USO DE ESTRUTURA DE REPETIÇÃO FOR</h1>
        <h2>FOR</h2>
        <ul>
            @for($i = 0; $i < count($arr); $i++)
                <li>{{$arr[$i]}}</li>
            @endfor
        </ul>
```

**FOR EACH**

```html
    <h2>FOR EACH</h2>
        <ul>
            @foreach($nomes as $nome)
                <li>{{$loop->index}} - {{$nome}}</li>
            @endforeach
        </ul>
```

## **EXECUTAR PHP PURO**

- Possibilidade para alcançar resultados além do Blade.

```html
    <h1>UTILIZANDO PHP PURO</h1>
        @php
            $name = "Exemplo de PHP puro";
            echo $name;
        @endphp
```

## **COMENTÁRIOS EM BLADE**

- Não aparecem na tela do usuário como os do HTML

```html
{{-- COMENTÁRIO BLADE --}}
```

## **LAYOUT COM BLADE**

- Reaproveitamento de código para evitar repetições.
1. Criar pasta `layouts`
2. Adicionar arquivo `main.blade.php`

```html
<!-- main.blade.php -->
<!DOCTYPE html><html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">

        <title>@yield('title')</title>

        <link rel="stylesheet" href="/css/styles.css">
        <script src="/js/scripts.js"></script>

        <!-- Fonts -->
        <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@200;600&display=swap" rel="stylesheet">

    </head>
    <body>
        @yield('content')

    <footer>
        <p>Guizo &copy; 2022</p>
    </footer>
    
    </body>
</html>
```

📓 @yield() permite que o conteúdo se realoque no template main.

- `@yield('content')`: todo o conteúdo da página ficará aqui, de forma dinâmica.
- `@yield('title')`: Muda o título dinâmicamente

Nas Views, você pode remover as tags , e , deixando apenas o conteúdo em si.

```html
{{-- Define o uso do template MAIN --}}
@extends('layouts.main')

{{-- Seções que possuem referências nos parâmetros <b>yield</b> --}}
@section('title', 'Guizo - Welcome')
@section('content')

{{-- Conteúdo da página --}}
<nav>
    <div class="links">
        <span><h1>USO DE ROTAS: </h1></span>
        <a href="/products">PRODUCTS</a>
        <a href="/contact">CONTACT</a>
    </div>
</nav>
<h1>TESTANDO ENGINE BLADE</h1>
<ul>
@if(10 > 5)
    <li>TESTANDO IFs</li>
@endif
<li>{{ $data }}</li>

@if($var == "")
    <li>Variável vazia</li>
@else 
    <li>Variável contém dados</li>
@endif
<!-- O nome dos dados dinâmicos é a chave do array, e não a variável PHP-->
</li>
</ul>
<h1>USO DE ESTRUTURA DE REPETIÇÃO FOR</h1>
<h2>FOR</h2>
<ul>
    @for($i = 0; $i < count($arr); $i++)
        <li>{{$arr[$i]}}</li>
    @endfor
</ul>
<h2>FOR EACH</h2>
<ul>
    @foreach($nomes as $nome)
        <li>{{$loop->index}} - {{$nome}}</li>
    @endforeach
</ul>
<h1>UTILIZANDO PHP PURO</h1>
@php
    $name = "Exemplo de PHP puro";
    echo $name;
@endphp

{{-- Comentário não aparece na tela --}}
<h1>ARQUIVO ESTÁTICO</h1>
<img src="/img/hachiman.jpg" alt="hachiman" height="100xp" style="border-radius:50%">

@endsection
```

# **ARQUIVOS ESTÁTICOS**

- CSS, JavaScript, imagens...

`public`: Pasta de acesso direto aos arquivos estáticos.

- Basta criar uma pasta e acessá-la nas views.

```html
<link rel="stylesheet" href="/css/styles.css">
```

`/css`: acessa a `public/css`

# RESGATANDO PARÂMETROS DE URL

- Mudar como uma view nos responde;

PARÂMETROS: `{id}`
PARÂMETROS ADICIONAIS: `?`
QUERY PARAMETERS: `?nome=Matheus&idade=29`

Definir parâmetros em `routes/web.php`

# CONTROLLERS

- Parte fundamental da aplicação
- Contêm boa parte da lógica (actions)
- envia e espera resposta do banco de dados
- envia e recebe algumas respostas das views
- Criados via artisan

## CRIAR CONTROLLER

```
php artisan make:controller EventController
```

📓 O carregamento das páginas deve ser de responsabilidade do controller, assim como os métodos HTTP

- Irá criar o arquivo `EventController.php` na pasta app/Http/Controllers

# CONEXÃO COM BANCO DE DADOS

- Configuradas pelo arquivo .env
- ORM (Object-Relational Mapping) chamada Eloquent (Query, insert ... do banco)
- migrations para a criação das tabelas (versionamento do banco de dados)

## TESTANDO AS CONEXÕES DO BANCO

```
php artisan migrate
```

- Comando `migrate` cria algumas tabelas no banco

## AVANÇANDO EM MIGRATIONS

- Uma nova migration cria um novo campo na tabela

### COMANDOS

`fresh`: apaga todos os dados existentes ⚠️
`rollback`: usado para voltar uma migration 
`reset`: voltar todas as migrations 
`refresh`: voltar todas as migrations e rodar o Migrate novamente.

### CRIANDO TABELA PRODUCTS

```
php artisan make:migration create_products_table
```

### ADICIONANDO NOVO CAMPO À PRODUCTS

```
php artisan make:migration add_category_to_products_table
```
