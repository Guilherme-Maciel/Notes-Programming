# C#

Created: June 12, 2021 7:28 PM
Tags: back, c#

- LINKS
    - Variáveis globais: [https://www.youtube.com/watch?v=dl3nbacvOHE](https://www.youtube.com/watch?v=dl3nbacvOHE)
    - Concatenação de strings: [https://docs.microsoft.com/pt-br/dotnet/csharp/how-to/concatenate-multiple-strings](https://docs.microsoft.com/pt-br/dotnet/csharp/how-to/concatenate-multiple-strings)
    - Música C#: [https://social.msdn.microsoft.com/Forums/en-US/4085fc50-a3e1-4e90-b6b7-ad165223ca6c/c-playing-music-amp-sound-from-resources?forum=csharpgeneral](https://social.msdn.microsoft.com/Forums/en-US/4085fc50-a3e1-4e90-b6b7-ad165223ca6c/c-playing-music-amp-sound-from-resources?forum=csharpgeneral)
    - Identar código: Ctrl + k + d
- **FECHAR E ABRIR CORRETAMENTE UM FORM PARA NÃO TER INTERFERÊNCIA**
    
    ```csharp
    //Via cronometro
    private void Timer2_Tick(object sender, EventArgs e)
            {
                this.Hide();
                Form f = new Form3();
                Timer2.Enabled = false;
                f.Closed += (s, args) => this.Close();
                f.Show();
            }
    
    //Botão
    
    private void btn_crafting_Click(object sender, EventArgs e)
            {
                this.Hide();
                Form f = new Form2();
                f.Closed += (s, args) => this.Close();
                f.Show();
            }
    ```
    
    [https://pt.stackoverflow.com/questions/8987/chamar-um-form-e-fechar-um-form-no-mesmo-evento](https://pt.stackoverflow.com/questions/8987/chamar-um-form-e-fechar-um-form-no-mesmo-evento)
    
- ÍNDICE

# VARIÁVEIS

## STRING

```csharp
string name = "Guilherme";

name[0] //G

//CONCATENAÇÃO
console.writeline(string1 + string2)

//INTERPOLAÇÃO
console.writeline($"{string1}, {string2}")

//COMPRIMENTO DO TEXTO
name.Length()

```

## INTEGER

```csharp
int num = 2;

//Converter texto em inteiro
entrada = Convert.ToInt32(Console.ReadLine())
 
```

## DOUBLE

```csharp
double num = 2.0;

//Converter texto em decimal
entrada = Convert.ToDouble(Console.ReadLine())
```

## ARRAY

```csharp
int[] vetor = new int[5];
```

## OUTRAS

```csharp
//BYTE
//SBYTE - pode ser negativo
//UNIT - não pode ser negativo
//SHORT
//USHORT
//LONG
//ULONG
//FLOAT
//CHAR
//BOOL
```

# FOREACH

```csharp
string[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
foreach (string i in cars) 
{
  Console.WriteLine(i);
}
```

# FUNÇÕES

```csharp
Array.sort(cars); //Deixa em ordem de crescente
```

# SAÍDA

```csharp
Console.WriteLine() //Pula uma linha após exibir mensagem.
Console.Write() //Não pula uma linha ao exibir a mensagem

Console.WriteLine($"A={area:F4}"); //Arredonda número decimal para 4 casas
```

# ENTRADA

```csharp
Console.ReadKey() //Lê uma tecla do teclado
Console.ReadLine() //Lê uma informação digitada pelo usuário

r = Convert.ToDouble(Console.ReadLine()); //Lê valor double

//ENTRADA DE MULTIPLOS VALORES EM UMA LINHA DE CÓDIGO
string linha = Console.ReadLine();
String[] v = linha.Split(' ');

int a = int.Parse(v[0]);
int b = int.Parse(v[1]);
int c = int.Parse(v[2]);
```

# OPERADORES ARITMÉTICOS

| + | soma |
| --- | --- |
| ++ | incremento  |
| - | subtração |
| -- | decremento |
| * | multiplicação |
| / | divisão |
| % | resto |

# COMANDO DE DECISÃO

```csharp
if (condição){

}else if (condicao){

}else{

}
```

## OPERADORES DE COMPARAÇÃO

| == | igual |
| --- | --- |
| != | diferente |
| >= | maior igual |
| > | maior |
| <= | menor igual |
| < | menor |

## OPERADOR TERNÁRIO

```csharp
if (a > b)
{
	result = "a is greater than b";
}
else if (a < b)
{
	result = "b is greater than a";
}
else
{
	result = "a is equal to b";
}

//OPERADOR TERNÁRIO
a > b ? "a is greater than b" : a < b ? "b is greater than a" : "a is equal to b";
```

# LAÇO DE REPETIÇÃO

```csharp
while(condicao){

}

for(i = 2; i <= 10; i++){

}
```

# SWITCH CASE

```csharp
int day = 3;
switch (day) 
{
case 1:
    Console.WriteLine("Today is Saturday");
    break;
  
case 2:
    Console.WriteLine("Today is Sunday");
    break;
  
default:
    Console.WriteLine("Looking forward to the Weekend");
    break;
}
```

# DEBUG

clicar no lado esquerdo na linha que deseja iniciar o debug → breakpoint.

`F10` → prossegue a depuração na linha de código seguinte.

## STEP INTO

Executa comando por comando

# TIPOS FUNÇÕES

## PUBLIC

pode ser utilizado em classes diferentes

```csharp
//Função abaixo retorna um Boolean
public Boolean numeroPar(int num){
  Boolean retorno = false;
  if (num % 2 == 0) retorno = true;
  return retorno
}
```

## STATIC

A função pertence a classe e não ao objeto.

```csharp
//Retorna um valor decimal
static Double calculoDiametro(double r){
    return 2 * r;
}
```

## VOID

Função que não retorna nenhum valor

```csharp
static void Main(string[] args){

}
```

# CLASSES

```csharp
class MyClass{
}
```

## OBJETO DA CLASSE

```csharp
MyClass obj = new MyClass()
```

# MÉTODOS

## MATH

```csharp
Math.Max(x, y) //Mostra o maior valor
Math.Sqrt(64) //Calculo da raiz quadrada
Math.Round(2.4) //Aredonda um número
```

# NAMESPACES

## System.Collections.Generic

### List<T>

```csharp
//É equivalente ao ArrayList, mas fortemente tipada.
IList<int> lista = new IList<int>();
```

# PASSAGEM DE PARÂMETROS POR REFERÊNCIA

Variáveis utilizam o mesmo endereço de memória

```csharp
static void passagemRef(ref int a){
   a = 10
}

static void Main(string[] args){
   int n = 5
   passagemRef(ref n)
   //n = 10
}
```
