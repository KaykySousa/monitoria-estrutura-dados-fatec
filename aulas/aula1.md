# Aula 1 - Monitoria de Estruturas de Dados

## 1. Introdução ao C

```c
// aula1_ex1.c

#include <stdio.h>

int main(void) {
    printf("Hello, World!\n");

    return 0;
}
```

Você pode compilar e executar o código acima com os seguintes comandos ou usando uma IDE de sua preferência:

```bash
gcc ./aula1_ex1.c -o ./aula1_ex1
./aula1_ex1
```

OnlineGDB (IDE online): https://www.onlinegdb.com/online_c_compiler


## 2. Variáveis

```c
#include <stdio.h>

int main(void) {
    int idade = 20;
    float altura = 1.75;
    double peso = 70.5;
    char genero = 'M';
    char nome[] = "João da Silva";

    return 0;
}
```

> Note que C não possui um tipo booleano nativo. Usamos `0` para falso e `1` para verdadeiro.

```c
#include <stdio.h>

int main(void) {
    short int a; // 2 bytes: -32.768 a 32.767
    int b;       // 4 bytes: -2.147.483.648 a 2.147.483.647
    long int c;  // 8 bytes: -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807
    long long int d; // 8 bytes: -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807

    unsigned short int e; // 2 bytes: 0 a 65.535
    unsigned int f;       // 4 bytes: 0 a 4.294.967.295
    unsigned long int g;  // 8 bytes: 0 a 18.446.744.073.709.551.615
    unsigned long long int h; // 8 bytes: 0 a 18.446.744.073.709.551.615

    h = 18446744073709551615ULL;
    printf("%llu\n", h);

    return 0;
}
```

> Os intervalos dos números de cada tipo podem variar dependendo da arquitetura do sistema (32 bits ou 64 bits) e detalhes da implementação do compilador.

## 3. Operadores

```c
#include <stdio.h>

int main(void) {
    int a = 10, b = 3;
    
    int soma = a + b;
    int subtracao = a - b;
    int multiplicacao = a * b;
    int divisao = a / b;
    int modulo = a % b;

    a++; // Pós-incremento
    ++a; // Pré-incremento

    b--; // Pós-decremento
    --b; // Pré-decremento

    return 0;
}
```

## 4. Estruturas condicionais

```c
/* if-else */
#include <stdio.h>

int main(void) {
    int idade = 20;

    if (idade < 18) {
        printf("Menor de idade\n");
    } else if (idade >= 18 && idade < 65) {
        printf("Adulto\n");
    } else {
        printf("Idoso\n");
    }

    return 0;
}
```

```c
/* switch */
#include <stdio.h>

int main(void) {
    int dia = 3;

    switch (dia) {
        case 1:
            printf("Domingo\n");
            break;
        case 2:
            printf("Segunda-feira\n");
            break;
        case 3:
            printf("Terça-feira\n");
            break;
        case 4:
            printf("Quarta-feira\n");
            break;
        case 5:
            printf("Quinta-feira\n");
            break;
        case 6:
            printf("Sexta-feira\n");
            break;
        case 7:
            printf("Sábado\n");
            break;
        default:
            printf("Dia inválido\n");
    }

    return 0;
}
```

```c
/* operador ternário */
#include <stdio.h>

int main(void) {
    int a = 10, b = 20;

    a += (b > a) ? 100 : 200;

    printf("a = %d\n", a);

    return 0;
}
```

## 5. Estruturas de repetição

```c
/* for */
#include <stdio.h>

int main(void) {
    for (int i = 0; i < 5; i++) {
        printf("%d\n", i);
    }

    return 0;
}
```

```c
/* while */
#include <stdio.h>

int main(void) {
    int i = 0;
    while (i < 5) {
        printf("%d\n", i);
        i++;
    }

    return 0;
}
```

```c
/* while com break e continue */
#include <stdio.h>

int main(void) {
    int i = 0;
    while (true) { // loop infinito
        if (i % 2 == 0) {
            i++;
            continue; // pula para a próxima iteração
        }
        if (i >= 10) {
            break; // sai do loop
        }
        printf("%d\n", i);
        i++;
    }

    return 0;
}
```

```c
/* do-while */
#include <stdio.h>

int main(void) {
    int i = 0;
    do {
        printf("%d\n", i);
        i++;
    } while (i < 5);

    return 0;
}
```

## 6. Ponteiros

Um ponteiro é uma variável que armazena um endereço de memória de outra variável. Ou seja, em vez de guardar um valor diretamente, ele aponta para onde esse valor está guardado.

```c
#include <stdio.h>

int main(void) {
    int valor;
    int *ponteiro;

    valor = 10;
    ponteiro = &valor;

    printf("Valor: %d\n", valor);
    printf("Ponteiro: %p\n", ponteiro);

    printf("Obter valor através do ponteiro: %d\n", *ponteiro);
    printf("Endereço de memória de valor: %p\n", &valor);

    return 0;
}
```

```c
int *p;  // ponteiro para um inteiro
float *f; // ponteiro para um float
char *c;  // ponteiro para um char
```

```c
#include <stdio.h>

int main(void) {
    int a = 10;
    int *p = &a;

    printf("Valor de A: %d\n", a);
    a = 20;
    printf("Valor de A após modificação: %d\n", a);

    *p = 30; // Modifica o valor de 'a' através do ponteiro
    printf("Valor de A após modificação via ponteiro: %d\n", a);

    return 0;
}
```

## 7. Arrays

Um array é uma coleção de variáveis do mesmo tipo armazenadas em endereços de memória contínuos. Em outras palavras, é uma lista de valores que você pode acessar usando índices.

```c
#include <stdio.h>

int main(void) {
    int numeros[5];

    numeros[0] = 10;
    numeros[1] = 20;
    numeros[2] = 30;
    numeros[3] = 40;
    numeros[4] = 50;

    for (int i = 0; i < 5; i++) {
        printf("Número %d: %d\n", i, numeros[i]);
    }

    return 0;
}
```

Outra forma de declarar e inicializar um array:

```c
int numeros[] = {10, 20, 30, 40, 50};
```

```c
#include <stdio.h>

int main(void) {
    int numeros[] = {10, 20, 30, 40, 50};
    
    printf("Endereço de memória do array: %p\n", numeros);

    printf("Endereço de memória do primeiro elemento: %p\n", &numeros[0]);
    printf("Primeiro elemento: %d\n", *numeros);
    
    printf("Endereço de memória do segundo elemento: %p\n", (numeros + 1));
    printf("Segundo elemento: %d\n", *(numeros + 1));

    return 0;
}
```

## 8. Funções

```c
#include <stdio.h>

// Definição do protótipo da função
void hello();

int main(void) {
    hello(); // Chamada da função

    return 0;
}

// Implementação da função
void hello() {
    printf("Hello, World!\n");
}
```

```c
#include <stdio.h>

int soma(int a, int b) {
    return a + b;
}

int main(void) {
    int resultado = soma(10, 20);
    printf("Resultado: %d\n", resultado);

    return 0;
}
```

```c
// Passagem por valor
#include <stdio.h>

void dobrar(int num) {
    num = num * 2;
    printf("Dentro da função: %d\n", num);
}

int main(void) {
    int valor = 10;
    dobrar(valor);
    printf("Fora da função: %d\n", valor);

    return 0;
}
```

```c
// Passagem por referência
#include <stdio.h>

void dobrar(int *num);

int main(void) {
    int valor = 10;
    dobrar(&valor);
    printf("Fora da função: %d\n", valor);

    return 0;
}

void dobrar(int *num) {
    *num = *num * 2;
    printf("Dentro da função: %d\n", *num);
}
```

## 9. Bubble Sort

```c
#include <stdio.h>
#include <stdbool.h>

void bubbleSort(int arr[], int n);
void swap(int *l, int *r);
void printArray(int arr[], int n);

int main(void) {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);

    bubbleSort(arr, n);

    printArray(arr, n);

    return 0;
}

void bubbleSort(int arr[], int n) {
    int i, j, swapped;
    for (i = 0; i < n - 1; i++) {
        swapped = false;
        for (j = 0; j < n - i - 1; j++) {
            if (*(arr + j) > *(arr + j + 1)) {
                swap(arr + j, arr + j + 1);
                swapped = true;
            }
        }
        if (!swapped) {
            break;
        }
    }
}

void swap(int *l, int *r) {
    int temp = *l;
    *l = *r;
    *r = temp;
}

void printArray(int arr[], int n) {
    int i;
    for (i = 0; i < n; i++) {
        printf("%d ", *(arr + i));
    }
    printf("\n");
}
```
