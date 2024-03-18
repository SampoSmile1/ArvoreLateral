#include <stdio.h>
#include <stdlib.h>

/* run this program using the console pauser or add your own getch, system("pause") or input loop */

typedef struct arvore
{
  char elem;
  struct arvore* esq;	
  struct arvore* dir;
}Arvore;
typedef struct arvore Arvore;

typedef struct fila
{
	char elem_fila;
	struct fila* prox;
}Fila;

Fila* prim;
Fila* ult;

Arvore* raiz;

int FilaVazia()
{
 if (prim == NULL)
  return 1;
 else 
 return 0;
}

Fila* CriaFilaNo()
{
  Fila* pt = (Fila*)malloc(sizeof(Fila));
   if(pt != NULL)
       return pt;
   return NULL;	
}


Arvore* CriaNo(char valor)
{
  Arvore* pt = (Arvore*)malloc(sizeof(Arvore));
   if(pt != NULL)
   {
   	   pt->elem = valor;
   	   pt->dir = NULL;
   	   pt->esq = NULL;
       return pt;
   }
   return NULL;	
}

insereElem(char valor)
{
	Fila* x = prim;
  if (FilaVazia()) // no inserido é o primeiro no da Fila
  {
  	x = CriaFilaNo();
  	x->elem_fila = valor;
  	x->prox = NULL;
  	prim = x;
  	ult = x;
  }
  else
  {
  	x = CriaFilaNo();
  	x->elem_fila = valor;
  	x->prox = NULL;
  	ult->prox = x;
  	ult = x;
  }
}

void imprime()
{
	printf("\n");
	Fila* x = prim;
	
	while(x!=NULL)
	{
		 printf("\nVisitando o no = %c\n",x->elem_fila);
		x=x->prox;
	}
	printf("\n");
	printf("\n");
}




void lateral (){ //Lógica mas não funciona como deveria, não aloca os nós
	Arvore*x;
	Fila*y;
	x=raiz;
	insereElem(raiz->elem);
	while(y!=NULL){
		if(x->esq!=NULL){
			insereElem(x->esq);
		}
		if(x->dir!=NULL){
			insereElem(x->dir);
		}
		y=y->prox;
		x=y;
	}
}




















int main(int argc, char *argv[]) {

Arvore* noB;
Arvore* noC;
Arvore* noD;
Arvore* noE;
Arvore* noF;
Arvore* noG;
Arvore* noH;
Arvore* noI;

    raiz = NULL;
    prim = NULL;
    ult = NULL;
    
    raiz = CriaNo('A');
	noB = CriaNo('B');
	noC = CriaNo('C');	
	noD = CriaNo('D');
	noE = CriaNo('E');
	noF = CriaNo('F');
	noG = CriaNo('G');
	noH = CriaNo('H');
	noI = CriaNo('I');
	
	
	raiz->esq=noB;
	raiz->dir=noC;
	noB->esq=noD;
	noD->dir=noG;
	noC->esq=noE;
	noE->esq=noH;
	noE->dir=noI;
	noC->dir=noF;
	
		insereElem(raiz->elem);
		insereElem(noB->elem);
		insereElem(noC->elem);
		insereElem(noD->elem);
		insereElem(noE->elem);
		insereElem(noF->elem);
		insereElem(noG->elem);
		insereElem(noH->elem);
		insereElem(noI->elem);
	
	
	lateral();
	imprime();
	
	return 0;
}
