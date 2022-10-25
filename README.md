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
