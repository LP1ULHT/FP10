**UNIVERSIDADE LUSÓFONA DE HUMANIDADES E TECNOLOGIAS**

*Linguagens de Programação I - 2019/2020*

# Ficha de Exercícios - 10: Pilhas

Na resolução destes exercícios deve ser utilizada a Linguagem de Programação C. Para além da correta implementação dos requisitos, tenha em conta os seguintes aspetos:

- O código apresentado deve ser bem indentado. 
- O código deve compilar sem erros ou *warnings* utilizando o *gcc* com as seguintes flags:
- `gcc -Wall -Wextra -Wpedantic -std=c99 -g exercicio1.c -o exercicio1`
- Tenha em atenção os nomes dados das variáveis, para que sejam indicadores daquilo que as mesmas vão conter.
- Evite o uso de constantes mágicas. 
- Evite duplicação de código. 
- Considere a implementação de funções para melhorar a legibilidade, evitar a duplicação e criar soluções mais genéricas.


1. Implemente um programa que recebe uma frase e, recorrendo a uma pilha, inverte a ordem dos seus caracteres, imprimindo a sequência resultante. Por exemplo, se inserir a palavra "roma", deverá imprimir "amor".


2. Recorrendo a uma pilha, implemente um programa que recebe uma expressão matemática e, recorrendo a uma pilha, valida se os parêntesis estão devidamente balanceados. Por exemplo, a expressão `(2 + 3) + 4 * (5 - (6 / 7))` tem os parêntesis bem balanceados, mas a expressão `(2 + 3 * 4` não. 

    Sugestão de implementação: recorrendo a uma pilha, percorra os carateres da expressão da esquerda para a direita:
   * sempre que é encontrado um '(', este é colocado na pilha. 
   * sempre que é encontrado um ')', consulta-se o elemento no topo da pilha. Se existir, retira-se; senão, interrompe-se o programa indicando que não se encontram balanceados.
   * ignororar qualquer outro símbolo
   * Depois de lida toda a expressão, podemos pronunciar-nos sobre o balanceamento de parêntesis na expressão, dependendo de a pilha estar vazia.


3. Implemente, recorrendo a uma pilha, uma calculadora com notação pós-fixa. Esta é uma notação em que o operador é escrito após os operandos. Esta notação tem a vantagem de não necessitar da especificação de precedencia entre operadores nem de parêntesis. Para avaliar uma expressão em notação pos-fixa, percorremos a expressão da esquerda para a direita. Ao encontrar um operador aplicamos esse operador aos dois ultimos operandos e colocamos oseu valor na expressão. Este processo é repetido, até que a expressão seja reduzida a um único valor, o qual representa o valor da expressão.
   Exemplo de notação:
   * `4 + 3` escreve-se `4 3 +`. Quando se lê o operador `+`, aplica-se este aos dois operandos anteriores, `4` e `3` (operação `4 + 3`).
   * `( 4 + 36 ) + 58` em notação pós-fixa fica `4 36 + 58 +`

   Sugestão de implementação:
   * Na sequência de entrada, os elementos estão separados de espaços. 
   * crie uma pilha vazia
   * leia a sequencia da esquerda para a direita
   * se ler um operando (número), armazene-o na pilha.
   * se ler um operador (+, -, * ou /), recorra ao metodo pop para extrair os ultimos dois operandos, avalie a operação devida e armazene o resultado na pilha. 
   * repita até terminar de ler a sequencia. na pilha terá o resultado.

   Sugestão de implementação, tomando como exemplo para a expressão de entrada `4 3 5 * +` (equivalente a  `4 + 3 * 5`):
   * é lido e colocado na pilha o 4
   * é lido e colocado na pilha o 3
   * é lido e colocado na pilha o 5
   * quando é lido o *, é feita a multiplicação 3 * 5 = 15, e o resultado guardado na pilha
   * quando é lido o +, é feita a soma 4 + 15 = 19, o resultado guardado na pilha
   * chegando ao fim da sequencia, apresenta-se o resultado da operação, armazenado na pilha, 19
