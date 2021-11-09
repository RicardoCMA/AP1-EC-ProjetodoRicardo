#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <stdlib.h>
#include <windows.h>

#define SIZE 200

char nome[SIZE][20];
char sobrenome[SIZE][20];
char cpfcnpj[SIZE][20];
char telefone[SIZE][15];
char cep[SIZE][10];
char codigo[SIZE][4];
int op;
long int cdg;

void cadastro();
void pesquisa();
void ordena();
void lista();
void excluir();
void atualizar();

int main ()
{    
    UINT CPAGE_DEFAULT = GetConsoleOutputCP();
    SetConsoleOutputCP(CP_UTF8);

    int num1, num2, num3;
    int conta, conta1, conta2, conta3, contab, operacao, operacao_aux;
    float deposito, valor, saldo1 = 0, saldo2 = 0, saldo3 = 0, conta_banco = 0;

    system("cls");
    do
    {
        printf("\n========== Bem Vindo ! ==========");
        printf("\n\n");
        printf("Digite um comando para prossegui:");
        printf("\n");
        printf("\n1 - Gerenciar Clientes\n");
        printf("2 - Gerenciar Contas\n");
        printf("3 - Sair\n");

        scanf("%d", &num1);

        if (num1 == 1 || num1 == 2)
        {
            // Gerenciar Cliente
            if (num1 == 1)
            {
                do
                {
                    printf("\n========== Gerenciar Cliente ==========\n");
                    printf("\nDigite um comando para prosseguir:");
                    printf("\n");
                    printf("\n1 - Cadastrar um cliente\n");
                    printf("2 - Lista de todos os clientes cadastrados\n");
                    printf("3 - Buscar cliente já cadastrado\n");
                    printf("4 - Atualizar um cliente cadastrado\n");
                    printf("5 - Excluir um cliente cadastrado\n");
                    printf("6 - Sair\n");

                    scanf("%d", &num2);

                    if (num2 == 1 || num2 == 2 || num2 == 3 || num2 == 4 || num2 == 5)
                    {
                        if (num2 == 1)
                        {
                            cadastro();
                        }
                        if (num2 == 2)
                        {
                            lista();
                        }
                        if (num2 == 3)
                        {
                            pesquisa();
                        }
                        if (num2 == 4)
                        {
                            atualizar();
                        }
                        if (num2 == 5)
                        {
                            excluir();
                        }
                    }
                    else
                    {
                        printf("\n===== Por favor escolha um dos números apresentados =====\n\n");
                    }
                } while (num2 != 6);
            }
            // Gerenciar Contas
            if (num1 == 2)
            {
                do
                {
                    printf("\n========== Gerenciar Contas ==========\n");
                    printf("\nDigite um comando para prosseguir:");
                    printf("\n");
                    printf("\n1 - Lista de todas as contas cadastradas");
                    printf("\n2 - Cadastrar uma conta para um cliente");
                    printf("\n3 - Listar todas as contas de um cliente");
                    printf("\n4 - Realizar um saque em uma conta");
                    printf("\n5 - Realizar um depósito em uma conta");
                    printf("\n6 - Realizar transferência entre contas");
                    printf("\n7 - Exibir um extrato de uma conta");
                    printf("\n8 - Sair\n");

                    scanf("%d", &operacao_aux);
                    if(operacao_aux == 1)
                    {
                        printf("\nIndisponível no momento, desculpe o transtorno\n");
                    }
                    if(operacao_aux == 2)
                    {
                        printf("\nIndisponível no momento, desculpe o transtorno\n");
                    }
                    if(operacao_aux == 3)
                    {
                        printf("\nIndisponível no momento, desculpe o transtorno\n");
                    }
                    if (operacao_aux == 5)
                    {
                        system("cls");
                        printf("Valor depositado:\n");
                        scanf("%f", &deposito);
                        saldo1 += deposito;
                        printf("Depósito bem sucedido\n");
                    }
                    else if (operacao_aux == 4)
                    {
                        system("cls");
                        printf("Valor (R$):\n");
                        scanf("%f", &valor);
                        if (saldo1 >= valor)
                        {
                            saldo1 = saldo1 - valor; 
                            printf("Saque bem sucesido\n");
                        }
                        else if (saldo1 < valor)
                        {
                            printf("Saldo insuficiente");
                        }
                    }
                    else if (operacao_aux == 6)
                    {
                        system("cls");
                        printf("Digite conta de destino:\n");
                        scanf("%d", &conta);
                        if (conta == 1234)
                        {
                            printf("Valor (R$):\n");
                            scanf("%f", &valor);
                            if (saldo1 >= valor)
                            {
                                printf("Transferencia efetuada com sucesso\n");
                                saldo2 += valor;
                                saldo1 = saldo1 - valor;
                            }
                            else if (saldo1 < valor)
                            {
                                printf("Saldo insuficiente\n");
                            }
                        }
                    }
                    else if (operacao_aux == 7)
                    {
                        system("cls");
                        printf("Saldo(R$): %.2f\n", saldo1);
                    }
                } while (operacao_aux != 8);

            }
        }
        else
        {
            system("cls");
            printf("\n===== Por favor escolha um dos numeros apresentados =====\n\n");
        }      
    }while (num1 != 3);
    
    system("cls");
    printf("\n========== Sair ==========\n");
    printf("\n..... Fim do processo ..... \n\n");
    return 0;

    SetConsoleOutputCP(CPAGE_DEFAULT);

}
 
void cadastro() 
{
    static int linha;
    system("cls");
    printf("\n===== Cadastrar um cliente =====\n");
    do{
        printf("\nDigite o primeiro nome do cliente: ");
        scanf("%s", &nome[linha]);
        printf("\nDigite o último nome do cliente: ");
        scanf("%s", &sobrenome[linha]);
        printf("\nDigite o CPF ou o CNPJ do cliente: ");
        scanf("%s", &cpfcnpj[linha]);
        printf("\nDigite o número de telefone do cliente (ex: (061)940028922): ");
        scanf("%s", &telefone[linha]);
        printf("\nDigite o CEP do cliente: ");
        scanf("%s", &cep[linha]);
        printf("\nEscolha o cógido que deseja ter (4 numeros): ");
        scanf("%s", &codigo[linha]);
        printf("\n===========================\n");
        system("cls");
        printf("\nDigite 1 para uma nova atualização de cadastro || digite qualquer outro valor para voltar\n\n");
        scanf("%d", &op);
        ++linha;
        system("cls");
    }while(op == 1);
    system("cls");
}

void ordena ()
{
    int x, y, r, a;
    char aux[20];

    for (x = 0; x < SIZE; x++)
    {
        for (y = x+1; y < SIZE; y++)
        {
            r = strcmp(nome[x], nome[y]);
            if (r > 0)
            {
                strcpy(aux, nome[x]);
                strcpy(nome[x], nome[y]);
                strcpy(nome[y], aux);
            }
        }
    }
    for (a=0; a < SIZE; a++)
    {
        printf("%s %s", nome[a], sobrenome[a]);
        printf("\n");
    }
}

void lista ()
{
   system("cls");
    printf("\n===== Listar todos os clientes cadastrados =====\n");
    printf("\n");
    int i = 0;
    for (i = 0; i < SIZE; i++)
    {
        if (codigo[i] > 0)
        {
            printf("\n\nNome: %s %s", nome[i], sobrenome[i]);
        }else{
            break;
        }
    }
    printf("\n\n");
}

void pesquisa() 
{
    
    char nomePesquisa[20];
    char cpfcnpjPesquisa[20];
    char Pesquisa[50];
    char codigoPesquisa[5];
    int i = 0;

    system("cls");
    printf("\n===== Buscar clientes já cadastrados =====\n");

    do
    {
        printf("\nDigite 1 - (NOME) para PESQUISAR  por nome  ||  2 - (CPF/CNPJ) para PESQUISAR por CPF ou CNPJ  ||  3 - (CODIGO) para PESQUISAR por codigo\n");
        scanf("%d", &op);
        switch(op)
        {
            case 1:
                printf("\nDigite o nome: ");
                scanf("%s", nomePesquisa);
                system("cls");
                for( i = 0; i < SIZE; i++)
                {
                    if(strcmp(nome[i], nomePesquisa) == 0)
                    {
                        printf("\nNome: %s \nSobrenome: %s \nCPF/CNPJ: %s \nTelefone: %s \nCEP: %s \nCodigo: %s", nome[i], sobrenome[i],
                         cpfcnpj[i], telefone[i], cep[i], codigo[i]);
                    }
                }
                break;
            case 2:
                printf("\nDigite o CPF ou o CNPJ: ");
                scanf("%s", cpfcnpjPesquisa);
                system("cls");
                for( i = 0; i < SIZE; i++)
                {
                    if(strcmp(cpfcnpj[i], cpfcnpjPesquisa) == 0)
                    {
                        printf("\nNome: %s \nSobrenome: %s \nCPF/CNPJ: %s \nTelefone: %s \nCEP: %s \nCodigo: %s", nome[i], sobrenome[i],
                         cpfcnpj[i], telefone[i], cep[i], codigo[i]);
                    }
                }
                break;
            case 3:
                printf("\nDigite o codigo: ");
                scanf("%s", codigoPesquisa);
                system("cls");
                for( i = 0; i < SIZE; i++)
                {
                    if(strcmp(codigo[i], codigoPesquisa) == 0)
                    {
                        printf("\nNome: %s \nSobrenome: %s \nCPF/CNPJ: %s \nTelefone: %s \nCEP: %s \nCodigo: %s", nome[i], sobrenome[i],
                         cpfcnpj[i], telefone[i], cep[i], codigo[i]);
                    }
                }
                break;
            default:
                    printf("\nOpcao invalida\n");
                break;
        }
        printf("\n===========================\n");
        printf("\nDigite 1 para uma nova busca || digite qualquer outro valor para voltar\n\n");
        scanf("%d", &op);
        system("cls");
    }while(op == 1);
    system("cls");
}

void excluir() 
{
    char nomePesquisa[20];
    char cpfcnpjPesquisa[20];
    char Pesquisa[50];
    char codigoPesquisa[5];
    int i = 0;

    system("cls");
    printf("\n===== Excluir um cliente cadastrado =====\n");

    do
    {
        printf("\nDigite 1 - (CPF/CNPJ) para EXCLUIR por CPF ou CNPJ  ||  2 - (CODIGO) para EXCLUIR por codigo\n");
        scanf("%d", &op);
        switch(op)
        {
            case 1:
                printf("\nDigite o CPF ou o CNPJ: ");
                scanf("%s", cpfcnpjPesquisa);
                system("cls");
                for( i = 0; i < SIZE; i++)
                {
                    if(strcmp(cpfcnpj[i], cpfcnpjPesquisa) == 0)
                    {
                        strcpy(nome[i], "\0");
                        strcpy(sobrenome[i], "\0");
                        strcpy(cpfcnpj[i], "\0");
                        strcpy(telefone[i], "\0");
                        strcpy(cep[i], "\0");
                        strcpy(codigo[i], "\0");
                    }
                }
                break;
            case 2:
                printf("\nDigite o codigo: ");
                scanf("%s", codigoPesquisa);
                system("cls");
                for( i = 0; i < SIZE; i++)
                {
                    if(strcmp(codigo[i], codigoPesquisa) == 0)
                    {
                        strcpy(nome[i], "\0");
                        strcpy(sobrenome[i], "\0");
                        strcpy(cpfcnpj[i], "\0");
                        strcpy(telefone[i], "\0");
                        strcpy(cep[i], "\0");
                        strcpy(codigo[i], "\0");
                    }
                }
                break;
            default:
                    printf("Opcao invalida");
                break;
        }
        printf("\nO cliente solicitado foi excluído com sucesso");
        printf("\n===========================\n");
        printf("\nDigite 1 para uma nova exclusão || digite qualquer outro valor para voltar\n");
        scanf("%d", &op);
        system("cls");
    }while(op == 1);
    system("cls");
}

void atualizar() 
{
    char novonome[20];
    char novosobrenome[20];
    char novocpfcnpj[20];
    char novotelefone[15];
    char novocep[10];
    char novocodigo[5];
    char nomePesquisa[20];
    char cpfcnpjPesquisa[20];
    char Pesquisa[50];
    char codigoPesquisa[5];
    int i = 0;

    system("cls");
    printf("\n===== Atualizar um cliente cadastrado =====\n");

    do
    {
        printf("\nDigite 1 - (CPF/CNPJ) para ATUALIZAR por CPF ou CNPJ  ||  2 - (CODIGO) para ATUALIZAR por codigo\n");
        scanf("%d", &op);
        switch(op)
        {
            case 1:
                printf("\nDigite o CPF ou o CNPJ: ");
                scanf("%s", cpfcnpjPesquisa);
                system("cls");
                for( i = 0; i < SIZE; i++)
                {
                    if(strcmp(cpfcnpj[i], cpfcnpjPesquisa) == 0)
                    {
                        printf("\nInformações antigas:\n");
                        printf("\nNome: %s \nSobrenome: %s \nCPF/CNPJ: %s \nTelefone: %s \nCEP: %s \nCodigo: %s", nome[i], sobrenome[i],
                            cpfcnpj[i], telefone[i], cep[i], codigo[i]);
                        printf("\n\n====================");    
                        printf("\n\nNovas informações:\n");
                        printf("\nDigite o novo primeiro nome:");
                        scanf("%s", &novonome[i]);
                        strcpy(nome[i], novonome);
                        printf("\nDigite o novo último nome: ");
                        scanf("%s", &novosobrenome[i]);
                        strcpy(sobrenome[i], novosobrenome);
                        printf("\nDigite o novo CPF ou CNPJ: ");
                        scanf("%s", &novocpfcnpj[i]);
                        strcpy(cpfcnpj[i], novocpfcnpj);
                        printf("\nDigite o novo número de telefone (ex: (061)940028922): ");
                        scanf("%s", &novotelefone[i]);
                        strcpy(telefone[i], novotelefone);
                        printf("\nDigite o novo CEP: ");
                        scanf("%s", &novocep[i]);
                        strcpy(cep[i], novocep);
                        printf("\nEscolha o novo cógido que deseja ter (4 numeros): ");
                        scanf("%s", &novocodigo[i]);
                        strcpy(codigo[i], novocodigo);
                    }
                }
                break;
            case 2:
                printf("\nDigite o codigo: ");
                scanf("%s", codigoPesquisa);
                system("cls");
                for( i = 0; i < SIZE; i++)
                {
                    if(strcmp(codigo[i], codigoPesquisa) == 0)
                    {
                        printf("\nInformações antigas:\n");
                        printf("\nNome: %s \nSobrenome: %s \nCPF/CNPJ: %s \nTelefone: %s \nCEP: %s \nCodigo: %s", nome[i], sobrenome[i],
                            cpfcnpj[i], telefone[i], cep[i], codigo[i]);
                        printf("\n\n====================");    
                        printf("\n\nNovas informações:\n");
                        printf("\nDigite o novo primeiro nome:");
                        scanf("%s", &novonome[i]);
                        strcpy(nome[i], novonome);
                        printf("\nDigite o novo último nome: ");
                        scanf("%s", &novosobrenome[i]);
                        strcpy(sobrenome[i], novosobrenome);
                        printf("\nDigite o novo CPF ou CNPJ: ");
                        scanf("%s", &novocpfcnpj[i]);
                        strcpy(cpfcnpj[i], novocpfcnpj);
                        printf("\nDigite o novo número de telefone (ex: (061)940028922): ");
                        scanf("%s", &novotelefone[i]);
                        strcpy(telefone[i], novotelefone);
                        printf("\nDigite o novo CEP: ");
                        scanf("%s", &novocep[i]);
                        strcpy(cep[i], novocep);
                        printf("\nEscolha o novo cógido que deseja ter (4 numeros): ");
                        scanf("%s", &novocodigo[i]);
                        strcpy(codigo[i], novocodigo);
                    }
                }
                break;
            default:
                    printf("Opcao invalida\n");
                break;
        }
        printf("\n===========================\n");
        printf("\nDigite 1 para uma nova atualização cadastro || digite qualquer outro valor para voltar\n\n");
        scanf("%d", &op);
        system("cls");
    }while(op == 1);
    system("cls");
}
