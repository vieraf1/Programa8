# Programa 8

Linguagem Utilizada: C++.

Programa que calcula a área de um triângulo, utilizando o Teorema de Heron, fazendo a leitura apenas dos valores dos três lados da figura.

Programa Desenvolvido Utilizando o Dev C++ IDE.

Código:

#include "iostream"
#include "cstdlib"
#include "math.h"
#include "conio.h"
#include "windows.h" 
#include "string"
#include <iomanip>
using namespace std;

struct Heron
{
	float a;
	float b;
	float c;
	float area;
};

struct Heron q[10];

void armazenamento(int line, float ladoa, float ladob, float ladoc)
{
	q[line].a = ladoa;
	q[line].b = ladob;
	q[line].c = ladoc;
}

void exibir(int line)
{
  system("cls");
  
  for (int j = 0; j <= line; j ++)
  {
    cout << "\nValor do primeiro lado: " << q[j].a << " - Valor do segundo lado: " << q[j].b << " - Valor do terceiro lado: " << q[j].c << " - Valor da área do triângulo: " << q[j].area;
  }
  
  cout << "\n\n";
  system("pause");
}

void calculos(int line)
{
	float a, b, c;
	float P = 0;
	float A = 0, AT = 0;
	for (int i = 0; i <= line; i ++)
	{
	  a = q[i].a;
	  b = q[i].b;
	  c = q[i].c; 
	  
	  P = (a + b + c)/2;
	  
	  A = P * (P-a) * (P-b) * (P-c);
	  
	  AT = sqrt(A);
	  
	  q[i].area = AT;	
	}
	
	system("cls");
	cout << "\nCalculando....Aguarde..." << endl;
	Sleep(2000);
}


int menu()
{
	     int tecla;
         system("cls");
         cout << "\n**Cálculo da Área do Triângulo usando Teorema de Heron**\n";
	     cout << "\n**Tela Inicial**\n";
         cout << "\n1 - Inserir valores";
         cout << "\n2 - Realizar Cálculos";
         cout << "\n3 - Exibir Resultados";
         cout << "\n4 - Sair \n" << endl;
         cin >> tecla;
		  
return tecla;}

int contmenu()
{
	int tecla = 0, linha = -1;
	float lado1 = -1, lado2 = -1, lado3 = -1;
	while (tecla != 4)
	{
		 tecla = menu(); 
		 
		 switch(tecla)
		 {
		 	case 1:
		 	    {
		 	    	int con1 = 0, con2 = 0, con3 = 0;
		 	    	 
		 	    	 while (con1 == 0)
		 	    	 {
		 	    	   system("cls");
		 	    	   cout << "\nDigite o valor do primeiro lado: ";
		 	    	   cin >> lado1;
		 	    	   if(lado1 >= 0)
		 	    	   {
					      con1 = 1;
					   }
					   else
					   {
					   	 cout << "\nPor Favor, digite um valor de lado de triângulo válido! \n";
					   	 system("pause");
					   }
		 	         } 
		 	    	 
		 	    	 while (con2 == 0)
		 	    	 {
		 	    	   system("cls");
		 	    	   cout << "\nDigite o valor do segundo lado: ";
		 	    	   cin >> lado2;
		 	    	   if(lado2 >= 0)
		 	    	    {
					      con2 = 1;
					    }
					   else
					    {
					   	  cout << "\nPor Favor, digite um valor de lado de triângulo válido! \n";
					   	  system("pause");
					    }
				      }
		 	    	 
		 	    	  while (con3 == 0)
		 	    	  {
		 	    	  	system("cls");
		 	    	    cout << "\nDigite o valor do terceiro lado: ";
		 	    	    cin >> lado3;
		 	    	    if(lado3 >= 0)
		 	    	     {
					        con3 = 1;
					     }
					    else
					     {
					   	    cout << "\nPor Favor, digite um valor de lado de triângulo válido! \n";
					   	    system("pause");
					     }
				      } 
		 	    	 
		 	    	 linha ++;
		 	    	 armazenamento(linha, lado1, lado2, lado3);
			         break;
			    }
			
			case 2:
				{
					if (linha >= 0)
					{
						calculos(linha);
					}
					break;
				}
			case 3:
				{
					if (linha >= 0)
					{
						exibir(linha);
					}
					break;
				}	
		 }
	}
return 0;}


int main()
{
	setlocale (LC_ALL, "portuguese");
	contmenu();

return 0;}
