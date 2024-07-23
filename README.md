# verifica-palindromo

Função que identifica possível palíndromo. Evita aninhamento de "for" e mantém complexidade O(n).


1) Não é necessário que as strings sejam palavras que existem na vida real
2) Recebe como parâmetro uma string
3) Retorne True, caso a palavra seja potencialmente palíndroma. Retorne False, caso contrário

Exemplos
Exemplo 1:
Entrada: palavra = "abbac"
Saída: True

Exemplo 2:
Entrada: palavra = "abba"
Saída: True

Exemplo 3:
Entrada: palavra = "abbacd"
Saída: False


# Respostas
Para ser um possível palíndromo o texto inserido pode conter no máximo um caracter que não se repita. 
Por exemplo: "aabbc" é um possível palíndromo, mas "aabbcd" não é porque existem dois caracteres únicos: o "c" e o "d".

## Resposta com complexidade O(n²)
Obtendo a resposta desejada com laços aninhados.

```
function isPalindromo(text){
    let isTextPalindromo = true;
    
    let charOcurrency = 0;
    let hasOdd = false;
    
    for(i = 0; i < text.length; i++){
        for(j = 0; j < text.length; j++){
            if(text[i] == text[j]){
                charOcurrency++;
            }
        }
        
        if (charOcurrency % 2 == 1 && hasOdd){
            isTextPalindromo = false;
            return isTextPalindromo;
        }
        
        if(charOcurrency % 2 == 1){
         hasOdd = true;
        } 
        
        charOcurrency = 0;

    }
    
    return isTextPalindromo;
}


console.log(isPalindromo("abba"));
```

## Resposta com complexidade O(n)
Para diminuir a complexidade do algoritmo podemos utilizar a criação de um objeto como abordagem para resolver esse problema. Assim, não será necessário o aninhamento de laços de repetição.

```
function isPossiblePalindromo(text) {
  const letters = {};

  for (let i = 0; i < text.length; i++){
    if(!Object.hasOwn(letters, text[i])){
       letters[text[i]] = 1;
    } else {
      letters[text[i]] = letters[text[i]] + 1;
  }
 }
 
 let hasOdd = false;
 
 for (const [key, value] of Object.entries(letters)){
     if(value % 2 == 1 && hasOdd){
         return false;
     }
     
     if (value % 2 == 1){
         hasOdd = true
     }
 }
 return true;
}


console.log("É um possível palíndromo: " + isPossiblePalindromo("aabccd"))
```
