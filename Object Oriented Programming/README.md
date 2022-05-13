# POO

Created: May 3, 2022 10:17 AM
Tags: concepts

# OBJETOS

- Tem propriedades e realizam ações
- Objeto representa uma entidade
- Facilita a reutilização de códigos e manutenção
- cada objeto tem uma utilidade
- objetos conversão entre si

# CLASSE

- Estrutura básica que instancia os objetos
- Serve de escopo para a criação do objeto.

```php
class Produto{
//abaixo são os atributos/variáveis 
   public $descricao; 
   public $preco;
//abaixo estão os métodos/funções
   public functions getDetalhes(){
      //this se refere a classe
      return "O produto {$this->descricao} custa {$this->preco} reais"
   }
}
//objeto/instância da classe do produto
//Variavel = new nome da classe
$p1 = new Produto;
//abaixo o objeto serve de ponte para atribuir valores aos atributos
$p1->descricao = 'Livro';
$p1->preco = 50;
//acessa o método getDetalhes()
echo $p1->getDetalhes();
```

# ATRIBUTOS

## PUBLIC

Acessa de qualquer lugar

## PRIVATE

Acessa apenas dentro da classe

## PROTECTED

Acessado apenas dentro da classe ou em classes que herdaram a classe principal (derivadas)

# HERANÇA

Permite que uma classe herde as funcionalidades de outra classe, mantendo todos os seus métodos e atributos.

```php
<?php
class Conta{
    protected $agencia;
    protected $conta;
    protected $saldo;

    public function __construct($agencia, $conta, $saldo){
        $this->agencia = $agencia;
        $this->conta = $conta;
        $this->saldo = $saldo;
    }

    public function getDetalhes(){
        return "Agencia: {$this->agencia} | Conta: {$this->conta} | Saldo: {$this->saldo}</br>";
    }

    public function depositar($valor){
        $this->saldo += $valor;
    }
}
//extends vai inicar a nova classe com os mesmos atributos e métodos da classe que está sendo extendida
class Poupanca extends Conta{
    public function saque($valor){
        if($this->saldo >= $valor):
            $this->saldo -= $valor;
            echo "Saque de: {$valor} | Saldo atual: {$this->saldo}</br>";
        else:
            echo "Saque não autorizado | Saldo atual: {$this->saldo}</br>";
        endif;

    }
}

class Corrente extends Conta{
    protected $limite;
    public function __construct($agencia, $conta, $saldo, $limite){
        //capta e reescreve a função da classe pai
        parent::__construct($agencia, $conta, $saldo);
        $this->limite = $limite;
    }

    public function saque($valor){
        if(($this->saldo + $this->limite) >= $valor):
            $this->saldo -= $valor;
            echo "Saque de: {$valor} | Saldo atual: {$this->saldo}</br>";
        else:
            echo "Saque não autorizado | Saldo atual: {$this->saldo}</br>";
        endif;

    }
}

$c1 = new Corrente(100, 2586, 5000, 500);
$c1->depositar(1500);
$c1->saque(2500);
$c1->saque(4500);

echo $c1->getdetalhes();
```

# ABSTRAÇÃO

Não pode ser instanciado como objeto.

Quando uma classe é estrutural e é usado como extensão de outras classes, ela é chamada de classe abstrata.

# ENCAPSULAMENTO

Adiciona segurança a um objeto e deixa certas propriedades exclusivas do objeto.

# POLIMORFISMO

Alteração do funcionamento de um objeto por meio de outro.

# CONSTRUCTOR

Inicializado sempre que um objeto da classe é criado.

# FUNÇÃO ABSTRATA vs FUNÇÃO VIRTUAL

## FUNÇÃO ABSTRATA

Não possui definição em si mesma. A classe filha deve substituir a função e fornecer sua própria definição da função abstrata.

```csharp
using System;

namespace abstract_vs_virtual
{
    public abstract class parentClass
    {
        public abstract void name();
    }

    class Program : parentClass
    {
        public override void name()
        {
            Console.WriteLine("This is Child Class");
        }
        static void Main(string[] args)
        {
            Program p = new Program();
            p.name();
        }
    }

}

//OUTPUT
This is Child Class
```

## FUNÇÃO VIRTUAL

Possui sua própria definição, mas também permite que as classes filhas a substituam e tenham sua própria definição da mesma função.

```csharp
using System;

namespace abstract_vs_virtual
{
    public class parentClass
    {
        public virtual void name()
        {
            Console.WriteLine("This is the Parent Class");
        }
    }

    class Program : parentClass
    {
        static void Main(string[] args)
        {
            Program p = new Program();
            p.name();
            parentClass pc = new parentClass();
            pc.name();
        }
    }

}

//OUTPUT
This is the Parent Class
This is the Parent Class
```

[Função abstrata vs função virtual em C# | Delft Stack](https://www.delftstack.com/pt/howto/csharp/abstract-function-vs-virtual-function-in-csharp/#:~:text=Fun%C3%A7%C3%A3o%20Virtual%20em%20C%23%20Uma%20fun%C3%A7%C3%A3o%20virtual%20tem,uma%20fun%C3%A7%C3%A3o%20%C3%A9%20uma%20fun%C3%A7%C3%A3o%20virtual%20em%20C%23.)
