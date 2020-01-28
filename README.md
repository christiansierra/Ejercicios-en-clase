# Ejercicios-en-clase
#include<conio.h>
#include<stdio.h>
#include<stdlib.h>
void retiro(int * valorR,int * cuenta );
void deposito(int * valorD,int * cuenta );
void Guardar(int * valorR,int * cuenta,int * valorD);
void Consulta(int * valorR,int * cuenta,int * valorD);
FILE *archivo;
main(){
	
	int cuenta=500,valorR=0,valorD=0;
	int opcion;
	char usuario[50];
	char clave[50];
	printf("\n USUARIO ");
	scanf("%s",usuario);
    printf("\n CONTRASE%cA ",165);
    scanf("%s",clave);
    printf("%s",usuario);

system("cls");
    do{
    	printf("\n1.-Realizar un retiro\n2.-Realizar un deposito\n3.-Guardar Datos\n4.-Consultar datos\n5.-Salir");
    	scanf("%d",&opcion);
    	switch(opcion){
    		case 1:
    			retiro(&valorR,&cuenta);
    			system("cls");
    		break;
    		case 2:
    		deposito(&valorD,&cuenta);
    		system("cls");
			break;
			case 3:
	archivo=fopen("cajero.txt","w");
	fputs("Usuario:",archivo);
	fprintf(archivo,"%s\n",usuario);
	fputs("Contraseña:",archivo);
	fprintf(archivo,"%s\n",clave);
				Guardar(&valorR,&cuenta,&valorD);
				system("cls");
			break;
			case 4:
			printf("\n%s",usuario);
			printf("\n%s",clave);	
			Consulta(&valorR,&cuenta,&valorD);
			system("cls");
			break;
			
				
		}


    	}
    	while(opcion<5);
    
}
void retiro(int *valorR ,int *cuenta){
	printf("\ningrese el valor");
	scanf("%d",&*valorR);
	*cuenta=*cuenta-*valorR;
	printf("\nsu cuenta actual es de :%d",*cuenta);
	getch();
	
}
void deposito(int *valorD ,int *cuenta){
	printf("\ningrese el valor");
	scanf("%d",&*valorD);
	*cuenta=*cuenta+*valorD;
	printf("\nsu cuenta actual es de :%d",*cuenta);
		getch();
}
void Guardar(int * valorR,int * cuenta,int * valorD ){
	fprintf(archivo,"El Dinero retirado Fue%d\n",*valorR);
	fprintf(archivo,"El Dinero depositado Fue%d\n",*valorD);
	fprintf(archivo,"Su Saldo actual es%d\n",*cuenta);
		getch();
	
}
void Consulta(int * valorR,int * cuenta,int * valorD ){
printf("\nRetiro:%d",*valorR);
printf("\nDeposito:%d",*valorD);
printf("\nSu Cuenta Actual es:%d",*cuenta);
	getch();
	
}
