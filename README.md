    #include <stdio.h>
#include <string.h>


int type,catg,submenu,option;
int total=0;
char soption[50];


/*********************


decoding the option to text/string form
input : option  in int form
output : string name in global array soption[]


*******************/
void decode(int option)
{




if (option==1)	{
 		strcpy(soption,": Veg Biriyani Rs 150/-");
 		total = total + 150;
}	


if (option==2)	{ 
strcpy(soption,": Tomato Rice Rs 90/- ");
 		total = total + 90;
}
if (option==3)	{ 
 		strcpy(soption,": Curd Rice Rs 50/-");
 		total =total +50;
}
if (option==4)	{
strcpy(soption,": Fruitninja Rs 20/-");
total += 20;
}
if (option==5)	{
strcpy(soption,": Tornado Rs 25/-");
total += 25;
}




if (option==6)	{
total+=30;
strcpy(soption,": Lightning Bolt Rs 30/- ");
}
if (option==7)	{
total += 100;
strcpy(soption,": Cake Rs 100/-");
}
if (option==8)	{
total += 40;
strcpy(soption,": Ice Cream Rs 40/-");
 }


}


/*******************


To add line based on supplied character as argument
input : function argument as character
output : 80 characters in one row




*******************/
void beautyline(char *c){
printf("\n");
for (int i=0;i< 80; i++) {
printf("%c",*c);
}
printf("\n");
}


/*********************


file : srmeats2.c
input : config.txt




*********************/
int main() {
  
  


   

 char useranswer[100] ="default" ; 
    char welcome[100] ; 
    char category[100] ;
    char meals[100] ;
    char juice[200]; 
    char deserts[100];
    char support[100];
    char mobile[20];


 char filename[20] = "config.txt";
 FILE  *fp; int i;
 char line [200];
   
    fp = fopen(filename, "r");
    
     if (fp == NULL)
    {
        printf("Error: could not open file %s", filename);
        return 1;
    }
    
  


  if (fgets(line,sizeof (line),fp)!= NULL){

    	strcpy(welcome,line) ;
   // printf("%s\n", welcome);
   }
    if (fgets(line,sizeof (line),fp)!= NULL){

    	strcpy(category, line) ;
   // printf("%s\n", category);
   }
   if (fgets(line,sizeof (line),fp)!= NULL){

    	strcpy(meals,line) ;
   // printf("%s\n", meals);
   }
   
   if (fgets(line,sizeof (line),fp)!= NULL){

    	strcpy(juice,line) ;
   // printf("%s\n", juice);
   }




   if (fgets(line,sizeof (line),fp)!= NULL){

    	strcpy(deserts,line) ;
   // printf("%s\n", deserts);
   }
   
    if (fgets(line,sizeof (line),fp)!= NULL){

    	strcpy(support,line) ;
   // printf("%s\n", deserts);
   }
    fclose(fp);
    
  
    
   // readfromfile();
   int decision=0;
    	
while (strcmp(useranswer, "bye") !=0) {
  if (decision ==0 ) { //get hello  string
   		beautyline("*");
     	

printf(" CHATBOT FOR ORDERING FOOD\n");
    	scanf("%s", useranswer);
  }
  if (decision==0 && (strcmp(useranswer, "hello") ==0)){
     	decision=1;
  }


 //  printf("%s\n",response2);
  
   
if (decision ==1){   //welcome
  		printf("%s\n", welcome);
  		decision =2; //order or support
  		scanf("%s", useranswer);
  		printf("you chosen : %s\n", useranswer);
  		if (strcmp(useranswer, "1") ==0) 
  	decision =3;  //order
}

 if (decision==3 ||  strcmp(useranswer, "1") ==0){   //order 
    //printf("you chosen : %s\n", useranswer);
    //type=1;


decision=3; //category
    
    	if (decision==3) {
    			printf("%s\n",category);
    			scanf("%s", useranswer);    
   		}
   
    	if (strcmp(useranswer, "1") ==0){// category meals
        		printf("you chosen : %s\n", useranswer);
        		decision=4;
       
        
        		if (decision==4) {
printf("%s\n", meals);
scanf("%d", &submenu);
        			if (submenu <1 || submenu > 3 ) {
printf ("invalid\n"); decision=4; continue;
}		
        			option = submenu;
          		}				
    	}//meals




    else if (strcmp(useranswer, "2") ==0){ //juice
    		printf("you chosen : %s\n", useranswer);
     		//catg=2;
decision=5;
     
    
 if (decision ==5 ) {
     	  	printf("%s\n", juice);
     	  	scanf("%d", &submenu);
     	  	printf("you chosen : %d\n", submenu);
      	}	
       if (submenu <1 || submenu > 3 ) {
   		   printf ("invalid\n"); 
   decision=5; 
   continue;
   }
        	option = submenu+3;
         
      } //juice
     



 else if (strcmp(useranswer, "3") ==0){ //desert
       		printf("you chosen : %s\n", useranswer);
       		//catg=3;
   		decision=6;
            if (decision==6) {
       	 		printf("%s\n", deserts);
         		scanf("%d", &submenu);
}
       		if (submenu <1 || submenu > 2 ) {
      		printf ("invalid\n"); decision=6; continue; 
       		} 
       		option = submenu+6;
     } //deserts
        
     decode(option);
     printf("Confirm Order   %s . \nPlease type \n yes to confirm order and exit. \n no to add more items. \n cancel to cancel and restart.  \n bye to exit.\n ",soption);
     scanf("%s",useranswer);








  if (strcmp(useranswer, "yes") ==0)  {
  	    beautyline("*");
   		printf("Your order total : %d \n ",total);
   		printf("\nplease enter mobile number\n");
   		scanf("%s",mobile);
   		printf("\nConfirmed order will be delivered soon!\n Thank you!\n");
   		beautyline("*");
   		scanf("%s",mobile);
   		return 1;
  } 
  else if (strcmp(useranswer, "no") ==0) {
  		printf(" Add more items-\n");
         decision =3; //order is decided take category
        // strcpy(useranswer, "1");
         
  		continue;
}   
    else if (strcmp(useranswer, "cancel")==0){
decision =0; continue;
}




else if (strcmp(useranswer, "bye") ==0) {
return 1;
}

}//order
 else if (strcmp(useranswer, "2") ==0) {   //support
  
    printf(" %s\n", support);
    scanf("%s", useranswer); 
    //type=2;
    if (strcmp(useranswer, "1") ==0)
    printf("Please Contact support: 999-999-999\nThank you");
    
    if (strcmp(useranswer, "2") ==0)
    printf ("please contact: 100-110-111\nThank you");
    
    return 1;
  }
} 
return 1;
}
