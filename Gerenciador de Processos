#include<stdio.h>
#include<stdlib.h>
#include<locale.h>
#include<string.h>

void InserirProcesso(char nomepro[], int tamanho);
void Listar();
void OrdeMem();
void OrdeStat();
void display();
void dequeue();


int totalmemo = 0;
int menu();
int status;


struct GerenProce_2cenario {
	char processo[50];
	int tamanho;
	int status;
	struct GerenProce_2cenario* prox;
} *Head = NULL, * Tail = NULL;

struct GerenProce_2cenario* AlfaAux[50];


int main()
{
	setlocale(LC_ALL, "");
	int op, num, c;
	char nomepro[50];
	int tamanho;
	int status = 0;

	while (1) {

		op = menu();
		switch (op) {
		case 1:
			printf("Inserira o processo desejado: \n");
			gets_s(nomepro);
			printf("Inserira o tamanho do processo: \n");
			scanf_s("%d", &tamanho);
			if (tamanho <= 100)
			{
				InserirProcesso(nomepro, tamanho);
			}
			break;

		case 2:// inserir busca de processo  e escolha do mesmo.
		{
			printf("Escolha um processo para executar! \n");
			display();
			printf("\n\n");
			gets_s(nomepro);// Lê o nome do processo que mudara de status
			GerenProce_2cenario* NovoElemento;
			NovoElemento = (struct GerenProce_2cenario*)malloc(sizeof(struct GerenProce_2cenario));
			NovoElemento = Head;
			while (strcmp(NovoElemento->processo, nomepro) != 0)
			{

				NovoElemento = NovoElemento->prox;
				if (NovoElemento->status == 0)
				{
					if (totalmemo < 1024)
					{
						NovoElemento->status = 1;
						return 0;
					}
					else
					{
						dequeue();
					}
				}
			}
			if (Head == NULL)
			{
				Head = NovoElemento;
				Head->prox = NULL;

				printf_s("A lista de processos está vazia ! \n");
			}
			else
			{
				NovoElemento->prox = Head;
				Head = NovoElemento;
			}
		}
		printf("Digite 1 para executar o processo: \n");
		scanf_s("%d", &num);
		while ((c = getchar()) != '\n' && c != EOF) {} // sempre limpe o buffer do teclado.
		if (num = 1)
		{
			printf("Processo ja em execução! \n");
		}
		break;
		case 3:
			printf("Listar processos.\n ");
			Listar();// vai para submenu de opções  de listagem
			break;
		case 4:
			return 0;// encerrar programa.
		default:
			printf("Invalido\n");
		}
	}
	return 0;
}

int menu() {
	int op, c;
	system("Cls");
	system("cls");
	printf("\n");
	printf("  ********** Lista de Processos ********\n");
	printf("  *                                    *\n");
	printf("  *1 Inserir processos                 *\n");
	printf("  *                                    *\n");
	printf("  *2 Executar processos                *\n");
	printf("  *                                    *\n");
	printf("  *3 Listar processos                  *\n");
	printf("  *                                    *\n");
	printf("  *4 Sair do programa                  *\n");
	printf("  *                                    *\n");
	printf("  **************************************\n");
	printf("\n");
	printf("\n");
	printf("\n");
	printf("\n");

	scanf_s("%d", &op);
	while ((c = getchar()) != '\n' && c != EOF) {} // sempre limpe o buffer do teclado.

	system("Cls");
	return op;
}

void InserirProcesso(char nomepro[], int tamanho)
{
	GerenProce_2cenario* InserirProcesso;
	InserirProcesso = (struct GerenProce_2cenario*)malloc(sizeof(struct GerenProce_2cenario));

	GerenProce_2cenario* ElementoVarredura;
	ElementoVarredura = (struct GerenProce_2cenario*)malloc(sizeof(struct GerenProce_2cenario));

	GerenProce_2cenario* NovoElemento;
	NovoElemento = (struct GerenProce_2cenario*)malloc(sizeof(struct GerenProce_2cenario));

	NovoElemento = Head;


	strcpy_s(InserirProcesso->processo, nomepro);
	InserirProcesso->tamanho = tamanho;
	InserirProcesso->status = 0;

	if (Head == NULL)
	{
		Head = InserirProcesso;
		Tail = InserirProcesso;
		
	}
	else
	{
		Tail->prox = InserirProcesso;
		Tail = InserirProcesso;
		Tail->prox = NULL;
	
	}

}//inserir ponteiros no vetor 

int listordem() {
	int opc, c;

	system("cls");
	printf("\n");
	printf("  ****** Lista de Processos *****\n");
	printf("  *                                    *\n");
	printf("  *1 Listar em ordem alfabetica.       *\n");
	printf("  *                                    *\n");
	printf("  *2 Listar por memoria consumida.     *\n");
	printf("  *                                    *\n");
	printf("  *3 Listar  por status.               *\n");
	printf("  *                                    *\n");
	printf("  *4 Sair para o menu.                 *\n");
	printf("  *                                    *\n");
	printf("  **************************************\n");
	printf("\n");

	scanf_s("%d", &opc);
	while ((c = getchar()) != '\n' && c != EOF) {} // sempre limpe o buffer do teclado.

	system("Cls");
	return opc;
}

void Listar()
{
	int opc, c;
	//	char nomepro[50];

	GerenProce_2cenario* ElementoVarredura;
	ElementoVarredura = (struct GerenProce_2cenario*)malloc(sizeof(struct GerenProce_2cenario));
	opc = listordem();

	switch (opc)
	{
	case 1:
		printf("Processos em ordem alfabetica. ");
		while ((c = getchar()) != '\n' && c != EOF) {} // sempre limpe o buffer do teclado.
		//Ordenação de quick sort ou merge por ordem alfabetica
		break;
	case 2:
		printf("Processos em ordem de gasto de memoria. ");
		while ((c = getchar()) != '\n' && c != EOF) {} // sempre limpe o buffer do teclado.
		OrdeMem();//Ordenação de processos por gasto de memoria.
		break;
	case 3:
		printf("Processos em ordem den status. ");
		while ((c = getchar()) != '\n' && c != EOF) {} // sempre limpe o buffer do teclado.
		OrdeStat();// Ordenação de ponteiros por status
		break;
	case 4:
		printf("Sair para o menu. ");
		while ((c = getchar()) != '\n' && c != EOF) {} // sempre limpe o buffer do teclado.
		main();// fechar o programa
		break;
	default:
		break;
	}
	printf("\n");
	system("pause");
	return;
}
void dequeue()
{
	GerenProce_2cenario* ElementoVarredura = Head;

	if (Head == NULL)
		printf("\nError 404 Not Found ! .\n");
	else
	{
		Head = Head->prox;
		printf("\nElemento Deletado: %d\n", ElementoVarredura->processo);
		free(ElementoVarredura);

		/*while (ElementoVarredura->prox != NULL) {
			printf("%d", ElementoVarredura->tamanho);
			ElementoVarredura = ElementoVarredura->prox;
			printf("\n");

		}*/
	}
	system("pause");
}

void display()
{
	GerenProce_2cenario* ElementoVarredura = Head;

	if (Head == NULL) {
		printf("\nError 404 Not Found ! .\n");
		printf("\nSem processos para serem executados!!!\n");
		main;
	}
	else {

		while (ElementoVarredura->prox != NULL) {
			printf("%s", ElementoVarredura->processo);
			printf("        %d MB" , ElementoVarredura->tamanho);
			if (ElementoVarredura->status==0)
			{
				printf(" -- Criado. ");
			}
			if (ElementoVarredura->status == 1)
			{
				printf(" -- Em execução. ");
			}				
			printf("\n____________________________");
			ElementoVarredura = ElementoVarredura->prox;
			printf("\n");

		}
		printf("%s", ElementoVarredura->processo);
		printf("        %d MB", ElementoVarredura->tamanho);
		if (ElementoVarredura->status == 0) {
			if (ElementoVarredura->status == 0)
			{
				printf(" -- Criado. ");
			}
			if (ElementoVarredura->status == 1)
			{
				printf(" -- Em execução. ");
			}
		}
			printf("\n\n____________________________");
		
	}
}

void OrdeMem() {
	GerenProce_2cenario* ElementoVarredura;
	ElementoVarredura = (struct GerenProce_2cenario*)malloc(sizeof(struct GerenProce_2cenario));

}
void OrdeStat() {
	{
		GerenProce_2cenario* ElementoVarredura = Head;


		if (Head == NULL)
			printf("\nFila vazia!!!\n");
		else {

			while (ElementoVarredura->prox != NULL) {
				printf("%d--->", ElementoVarredura->processo);
				ElementoVarredura = ElementoVarredura->prox;
			}
			printf("%d--->NULL", ElementoVarredura->processo);
		}
		printf("\n");
		system("pause");
	}
}



