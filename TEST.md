# Teste para pessoa desenvolvedora PHP

[← Voltar](README.md).

⚠️ Todas as perguntas são baseadas no **PHP 7.4.28**.

## Exemplo

### 0. Quais os valores de `$a` e `$b` no código abaixo? Por quê?

```php
$a = array_merge(array(1,2), NULL);
$b = array_merge($a, array(3));

var_dump($a);
var_dump($b);
```

> ```
> NULL
> NULL
> ```
> 
> A função `array_merge` retorna `NULL` quando qualquer um dos argumentos não for do tipo `array`. Embora o PHP 7 emita warnings sobre erro no tipo do argumento nem toda instalação está configurada para exibir warnings, logo é importante o desenvolvedor verificar os valores maualmente antes da chamada do `array_merge`, especialmente quando estamos concatenando o retorno de um `array_merge`.
>
> No PHP 8 esse comportamento foi atualizado para emitir um erro, o que ajuda a prevenir problemas.
> 
> ```
> Fatal error: Uncaught TypeError: array_merge(): Argument #2 must be of type array
> ```

## Perguntas

### 1. Qual a diferença entre `echo` e `print`?

> (Sua resposta aqui.)

### 2. Qual é a saída do código abaixo? Por quê?

```php
$x = true and false;
var_dump($x);
```

> Inicialmente pensei que poderia ser pela tabela verdade de conjução V -> F = V, porem ao inverter os condicionais obtive outro resultado, então cheguei a conclusão que esta parte do codigo atribui a primeira flag a variavel e ignora o false.

### 3. Qual é a saída do código abaixo? Por quê?

```php
$x = 5;
$a = array(
    $x++ + $x++,
    $x,
    $x-- - $x--,
    $x,
);

var_dump($a);
```

> O php possuir os operadores aritimeticos, neste casso o $x++ acrescenta +1 nele mesmo, no primeiro item do array,  o x entra valendo 5 ($x++) neste caso ele ainda esta valendo 5, porem na hora da soma com o outro ($x++) ele ja esta valendo 6 e quando sai da operação inteira o x esta acrescido de 2, por isso no segundo item do array ele vale 7, segue a mesma logica para operação de decrease.

### 4. Quais serão os valores de `$a` e `$b` após a execução do código abaixo? Por quê?

```php
$a = '1';
$b = &$a;
$b = "2$b";
```

> Quando declarado a variavel $b é passado a referencia da variavel $a, onde é guardado o endereço na memoria, quando "2$b" é atribuido em $b, ocorre uma concatenação de "21", porem essa string é salvo no endereço de memoria de $a, então a variavel $a e $b tem o mesmo valor.

### 5. O que são Traits e para que servem? 

> Trait é um tipo de classe que possui uma parte de codigo e funções onde é usado em outras sem a necessidade de um copiar e colar e sem precisar de uma herença.

### 6. Qual será a saída do código abaixo? Por quê?

```php
var_dump(0123 == 123);
var_dump('0123' == 123);
var_dump('0123' === 123);
```

> Na primeira condição o operador == compara apenas os valores, o resultado é false porque inicia com um 0 fazendo com que o interpretador do PHP considere um valor ASCII, já na segunda opção como é uma string e o operador == compara os valores o php entende como 123 == 123 true, na terceira condição o valor é false pois o operador === compara alem do valor o tipo de variavel, nesse caso string e int = false.

### 7. Qual será a saída do código abaixo? Por quê?

```php
$a = '';
$b = 0;
$c = '0a';

var_dump($a == $b);
var_dump($b == $c);
var_dump($c == $a);
```

> todas as saidas serão false, pois '', '0a' e 0 são diferentes.

### 8. Qual será o valor de `$x` após a execução do código abaixo? Por quê?

```php
$x = 3 + "15%";
```

> O php apresenta um warning e prossegue com a execução, porem o php entende que a "15%" é apenas 15 e acrescenta 3 + 15 ao $x = 18

### 9. Qual a diferença entre `require_once()` e `include_once()`?

> Os dois adicionam um arquivo auxiliar em uma execução de algum sistema, a diferença é que no require_once o arquivo é obrigado a existir caso contrario a execução para. E no include_once o arquivo não necessita existir.

### 10. Qual será o valor de `$name` após a execução do código abaixo? Por quê?

```php
$name = 'John ';
$name[10] = 'Doe';
```

> No php é possivel manipular strings como se fossem um array, o valor de name sera 'John D', apenas a primeira letra de 'Doe' sera acrescentada em $name por se tratar de um array de chars.

### 11. Qual será a saída do código abaixo? Por quê?

```php
$x = PHP_INT_MAX;
echo gettype($x + 1);
echo (int)($x + 1);

$y = 1.0;
echo is_float($y);
echo gettype($y);
```

> No primeiro bloco de codigo, é atribuido para x o valor maximo de um INT, e logo após acrescido de x + 1, estourando o valor maximo de int e transformando a variavel em double.

### 12. Qual será o valor de `$x` após a execução do código abaixo? Por quê?

```php
$x = "one" + 1;
```

> Como falado em exercicios acima o PHP entende que uma string e um integer não podem realizar operações aritiméticas, então é exibido um fatal error e a operação é finalizada

### 13. Qual a diferença entre `isset()` e `empty()`?

> O isset() verifica se uma variavel,index de array ou campo de um objeto existe retornando bool, já no caso de empty apenas verific se a está vazio, porem deve se existe a variavel com obrigatoriedade
