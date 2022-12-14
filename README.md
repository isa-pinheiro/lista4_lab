# lista4_lab

## Questão 01
Escreva um programa que adicione dois números usando ponteiros. Além do valor da soma, imprima
também o endereço de memória onde o valor resultante dessa soma está armazenado.

```c
#include <stdio.h>

int main(void) {
  int x, y, s;
  int *px = &x, *py = &y, *ps = &s;

  puts("Insina dois números: ");
  scanf("%d %d", &x, &y);
  
  *ps = *px + *py;

  printf("O endereço da soma é [%p]", ps);

  return 0;
}
```

## Questão 02
Escreva um programa que troque o valor de dois números utilizando ponteiros.
#include <stdio.h>

```c
int main(void) {
  int x, y, z;
  int *px = &x, *py = &y, *pz = &z;

  puts("insira dois dígitos: ");
  scanf("%d %d", &x, &y);

  printf("ordem original: %d, %d", x, y);
  *pz = *px;
  *px = *py;
  *py = *pz;
  printf("\nordem invertida: %d, %d", x, y);
  
  return 0;
}
```

## Questão 03
Escreva um programa que solicite iterativamente um número do usuário e imprima sempre o menor
valor fornecido. Crie um critério para finalização do programa. Utilize ponteiros.

```c
#include <stdio.h>

int main(void) {
  int n, *pn = &n, menor;
  puts("digite um número inicial: ");
  scanf("%d", &menor);
  do {
    puts("\ndigite um número para comparar: ");
    puts("digite 0 para sair:");
    scanf("%d", &n);
    
    if (menor > *pn){
      menor = *pn;
    } 
    
    printf("%d é o menor", menor);

    puts("\n");
    menor = *pn;
    
  } while(n != 0);
  return 0;
}
```
## Questão 04
Escreva um programa que leia um vetor do usuário e imprima seus valores e seus endereços. Teste
o vetor com tipos de dados diferentes, analise os endereços. O que você observou?

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
void imprimirvetor(int *, int );
void pedirvetor(int *, int );

int main(void) {
  int qtd1, qtd2, qtd3;
  int *p1 = NULL, *p2 = NULL, *p3 = NULL;

  puts("Insira a quantidade de vetores do primeiro, segundo e terceiro vetor, respectivamente: ");
  scanf("%d %d %d", &qtd1, &qtd2, &qtd3);

  p1 = (int *) malloc(qtd1 * sizeof(int));
  p2 = (int *) malloc(qtd2 * sizeof(int));
  p3 = (int *) malloc(qtd3 * sizeof(int));

  if(!p1 || !p2 || !p3){
    puts("não tem memória suficiente. tente de novo");
    exit(0);
  }
  
  puts("\nprimeiro vetor:");
  pedirvetor(p1, qtd1);
  imprimirvetor(p1, qtd1);
  
  puts("\nsegundo vetor:");
  pedirvetor(p2, qtd2);
  imprimirvetor(p2, qtd2);
  
  puts("\nterceiro vetor:");
  pedirvetor(p3, qtd3);
  imprimirvetor(p3, qtd3);
  
  return 0;
}


void pedirvetor(int *px, int qtdx){  
  for(int i = 0; i < qtdx; i++){
    printf("v[%d]", i);
    scanf("%d", px + i);
 
    }
}

void imprimirvetor(int *px, int qtd){
  for (int i = 0; i < qtd; i++){
    printf("[%p] %d\n", px + i, *(px + i));
      }
}
```

## Questão 05
Escreva um programa que encontre o tamanho de uma string fornecida. Utilize ponteiros.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MX 50
int length(char *);

int main(void) {
  char str[MX];  
  int tamanho;
  puts("Digite um string:");
  fgets(str, MX, stdin);
  str[strcspn(str, "\n")] = 0; 
  
  tamanho = length(str);
  printf("A string \"%s\" tem %d caracteres", str, tamanho);

  return 0;
}

int length(char *s) {
  int len = 0;
  while(*s){
    len++;
    s++;
  }
  return len;
}
```

## Questão 06
Escreva um programa que copie uma string para outra usando ponteiros.

```c
#include <stdio.h>
#define MX 50

void copia(char *, char *);
int main(void) {
  char s1[MX] = "por favor funciona";
  char s2[MX];

  copia(s1, s2);

  printf("%s", s2);
  return 0;
}

void copia(char *string1, char *string2){
  for(int i = 0; ; i++){
    *(string2 + i) = *(string1 + i);
    if(*(string1 + i) == '\0'){
      *(string2 + i) = *(string1 + i);
      break;
    }
  }
}

```


## Questão 07 
Escreva um programa que concatene duas strings utilizando ponteiros.

```c
#include <stdio.h>
#include <string.h>
#define MAX 50

void concatena(char *, char *);

int main(void) {
  char str1[MAX], str2[MAX];

  puts("Insira a primeira string: ");
  fgets(str1, MAX, stdin);
  str1[strcspn(str1, "\n")] = 0;
  
  puts("Insira a segunda string: ");
  fgets(str2, MAX, stdin);
  str2[strcspn(str2, "\n")] = 0;
  
  strcat(str1, str2); //funçao para concatenar, a segunda é adicionada ao lado da 1

  printf("Strings concatenadas: %s", str1);
    
  return 0;
}
```

## Questão 08
Escreva um programa que busque um caracter fornecido em uma string utilizando ponteiros.

```c
#include <stdio.h>
#include <string.h>
#define MAX 50
int main(void) {
  char str1[MAX], carac;
  int count = 0;

  puts("Insira uma string: ");
  fgets(str1, MAX, stdin);
  str1[strcspn(str1, "\n")] = 0;

  puts("Insira um caractere: ");
  carac = getchar();

  for(int i = 0; i < strlen(str1) ; i++){
    if(*(str1 + i) == carac){
      printf("O caractere está na posição: %d\n", i);
      count++;
    }
  }

  printf("Na string \"%s\" o caractere \'%c\' aparece %d vezes", str1, carac, count);
  return 0;
}
```

## Questão 09
Implemente o método de ordenação bolha utilizando ponteiros.

```c

```
