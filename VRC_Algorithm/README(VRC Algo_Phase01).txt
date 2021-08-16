/* VRC(Vertical Redundancy check) Algorithm 1st Phase 
       Take the char input and convert into Low level and high level signal
       and store it in a file(.txt).
*/

#include<stdio.h>
#include<string.h>

int main()
{
	char ch[100];
	
	int len;
	int i,j,k;
	int count=0,bcount=0;
	int b[500];
	int a[10];
	char LH[500];
	
	printf("Enter String :");
	fflush(stdin);
	gets(ch);
	len = strlen(ch);
	printf("No of characters = %d\n",len);
	printf("No of Bits = %d\n",len*8);
    for(i=0;i<len;i++)
	   {
	   	printf("ASCII Value = %d\t8_Bit Binary Value = \t",ch[i]);
	   	j = ch[i];
	   	while(j>0)
	   	   {
	   	   	count = count + 1;
	   	   	a[count-1]=j%2;
	   	   	j = j/2;
		   }
		if(count == 6)
		  {
		  	a[count] = 0;
		  	a[count+1] = 0;
		  }
		else if(count == 7)
		       {
		       	a[count] = 0;
			   }
		for(k=7;k>=0;k--)
		   {
		   	b[bcount]=a[k];
		   	printf("%d",a[k]);
		   	bcount++;
		   }
	   	count = 0;
	   	printf("\n");
	   }
	printf("\nBinary Format :-\n"); //convert string into binary format
	for(i=0;i<bcount;i++)
	   {
	   	printf("%d",b[i]);
	   }
	
	printf("\n\nVoltage Level Format :-\n"); //convert binary code into digital signal
	for(i=0;i<bcount;i++)
	   {
	   	if(b[i]==0)
	   	  {
	   	  	printf("L"); // L -> Low Level voltage
	   	  	LH[i]='L';
		  }
	   	else
	   	  {
	   	  	printf("H"); // H -> High level Voltage
	   	  	LH[i]='H';
		  }
	   } 
	   //printf("\n%s\n",LH);
	   
FILE *fptr;
fptr = fopen("encoding.txt","w");
fprintf(fptr,"%s",LH);

fclose(fptr);	     
	
	return 0;
}

