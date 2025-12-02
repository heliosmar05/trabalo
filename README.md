/******************************************************************************

Welcome to GDB Online.
  GDB online is an online compiler and debugger tool for C, C++, Python, PHP, Ruby, 
  C#, OCaml, VB, Perl, Swift, Prolog, Javascript, Pascal, COBOL, HTML, CSS, JS
  Code, Compile, Run and Debug online from anywhere in world.

*******************************************************************************/
#include <stdio.h>
#include <string.h>

#define MAX 100
#define TAM 100

typedef struct {
    int id;
    char texto[TAM];
} Item;

int main() {
    Item itens[MAX];
    int total = 0;
    int proximoID = 1;
    int opcao;

 do {
 printf("\n=== MENU ===\n");
 printf("1 - Inserir item\n");
 printf("2 - Consultar por palavra-chave\n");
 printf("3 - Listar todos os itens\n");
 printf("4 - Excluir item\n");
 printf("5 - Atualizar item\n");
 printf("0 - Sair\n");
 printf("Escolha: ");
 scanf("%d", &opcao);
 getchar();

 if (opcao == 1) {
 printf("Digite o novo item: ");
 fgets(itens[total].texto, TAM, stdin);
 itens[total].texto[strcspn(itens[total].texto, "\n")] = '\0';
 itens[total].id = proximoID++;

 total++;
 printf("Item inserido!\n");
    }

 else if (opcao == 2) {
 char chave[TAM];
 printf("Digite palavra-chave: ");
 fgets(chave, TAM, stdin);
 chave[strcspn(chave, "\n")] = '\0';

 printf("\nResultados:\n");
 for (int i = 0; i < total; i++) {
    if (strstr(itens[i].texto, chave)) {
   printf("ID %d: %s\n", itens[i].id, itens[i].texto);
   }
    }
 }

  else if (opcao == 3) {
  printf("\nItens cadastrados:\n");
  for (int i = 0; i < total; i++) {
  printf("ID %d: %s\n", itens[i].id, itens[i].texto);
    }
  }

  else if (opcao == 4) {
    int modo;
  printf("Excluir por: 1-ID ou 2-Palavra? ");
    scanf("%d", &modo);
   getchar();

   if (modo == 1) {
    int id;
    printf("Digite o ID: ");
    scanf("%d", &id);
    getchar();

    int i;
    for (i = 0; i < total; i++) {
    if (itens[i].id == id) {
    for (int j = i; j < total - 1; j++) {
    itens[j] = itens[j + 1];
     }
    total--;
    printf("Item removido!\n");
    break;
    }
     }
   if (i == total) printf("ID não encontrado.\n");
   } else {
   char chave[TAM];
    printf("Digite a palavra: ");
    fgets(chave, TAM, stdin);
    chave[strcspn(chave, "\n")] = '\0';

    int i = 0;
    while (i < total) {
    if (strstr(itens[i].texto, chave)) {
    for (int j = i; j < total - 1; j++) {
    itens[j] = itens[j + 1];
     }
    total--;
    } else {
     i++;
      }
    }
    printf("Itens removidos!\n");
     }
     }

   else if (opcao == 5) {
    int id;
   printf("Digite o ID do item a atualizar: ");
   scanf("%d", &id);
   getchar();

    int i;
    for (i = 0; i < total; i++) {
    if (itens[i].id == id) {
    printf("Novo texto: ");
    fgets(itens[i].texto, TAM, stdin);
    itens[i].texto[strcspn(itens[i].texto, "\n")] = '\0';

    printf("Item atualizado!\n");
    break;
    }
     }
    if (i == total) printf("ID não encontrado.\n");
    }

    } while (opcao != 0);

    return 0;
}
