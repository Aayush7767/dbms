Write shell scripts to do the following:
Steps:
1. Open Text Editor
2. Type shell program
3. Save the file with extension sh (eg:- shellpdemo.sh)
4. Open Terminal (ctrl + alt + T)
5. To run the program type bash shellpdemo.sh

#Shell Program 1
#To know the kernel being used
echo ' kernel in your system'
uname -a
#ubuntu version
echo 'ubuntu version and release number '
lsb_release -a
echo 'Top processes'
ps aux
echo 'Top processes in ascending order'
ps aux|sort
echo 'Top processes in descending order'
ps aux|sort -r

#Shell Program 2
echo 'Top memory consuming processes'
ps aux --sort -rss|head
echo 'current login user and log name'
w
echo ' Current shell'
ps -p $$
echo 'Display home directory'
ls
echo 'current working directory'
pwd
echo 'operating system type'
uname -r


2) CP NAD MV

 CP:
 #include <stdio.h>
#include <stdlib.h> // For exit()
int main()
{
FILE *fptr1, *fptr2;
char filename[100], c;
printf("Enter the filename to open for reading \n");
scanf("%s", filename);
// Open one file for reading
fptr1 = fopen(filename, "r");
if (fptr1 == NULL)
{
printf("Cannot open file %s \n", filename);
exit(0);
}
printf("Enter the filename to open for writing \n");
scanf("%s", filename);
// Open another file for writing
fptr2 = fopen(filename, "w");
if (fptr2 == NULL)
{
printf("Cannot open file %s \n", filename);
exit(0);
}
// Read contents from file
c = fgetc(fptr1);
while (c != EOF)
{
fputc(c, fptr2);
c = fgetc(fptr1);
}
printf("\nContents copied to %s", filename);
fclose(fptr1);
fclose(fptr2);
return 0;
}

MV:
#include <stdio.h>
int main()
{
char old[100], new[100];
printf("Enter old file path: ");
scanf("%s", old);
printf("Enter new file path: ");
scanf("%s", new);
if (rename(old, new) == 0)
{
printf("File renamed successfully.");
}
else
{
printf("Unable to rename files");
}
return 0;
}


3) Create a child process using the fork system call.
#include<stdio.h>
#include<sys/types.h>
#include<unistd.h>
int main()
{
   fork();
   printf("Hello World\n");
   printf("Parent id=%d",getppid());
   printf("Child Process id=%d",getpid());
   return 0;
}

4)Write a program to demonstrate the concept of non-pre-emptive
scheduling algorithms.

#include<stdio.h>
int main()
{
int AT[10],BT[10],WT[10],TT[10],i,n;
int b=0,cmpl_T;
float Avg_WT,Avg_TT,Total=0;
printf("Enter number of the process\n");
scanf("%d",&n);
printf("Enter Arrival time and Burst time of the process\n");
printf("AT\tBT\n");
for(i=0;i<n;i++)
{
scanf("%d%d",&AT[i],&BT[i]);
}
// Logic for calculating Waiting time
for(i=0;i<n;i++)
{
if(i==0)
WT[i]=AT[i];
else
WT[i]=b-AT[i];
b+=BT[i];
Total+=WT[i];
}
Avg_WT=Total/n;
// Logic for calculating Turn around time
cmpl_T=0;
Total=0;

for(i=0;i<n;i++)
{
cmpl_T+=BT[i];
TT[i]=cmpl_T-AT[i];
Total+=TT[i];
}
Avg_TT=Total/n;
// printing of outputs
printf("Process ,Waiting_time ,TurnA_time\n");
for(i=0;i<n;i++)
{
printf("%d\t\t%d\t\t%d\n",i+1,WT[i],TT[i]);
}
printf("Average waiting time is : %f\n",Avg_WT);
printf("Average turn around time is : %f\n",Avg_TT);
return 0;
}



5)Write a c program to implement the producer-consumer problem

#include<stdio.h>
#include<stdlib.h>
int mutex=1;
int full=0;
int empty=3,x=0;
void producer()
{
   --mutex;
   ++full;
   --empty;
   x++;
   printf("\nProducer produces item=%d",x);
   ++mutex;
}   
void consumer()
{
   --mutex;
   --full;
   ++empty;
   printf("\nConsumer consumes item=%d",x);
   x--;
   ++mutex;
}
int main()
{
   int n,i;
   printf("\n1.Press for Producer");
   printf("\n2.Press 2 for consumer");
   for(i=1;i>0;i++)
   {  
      printf("\n Enter your choice:");
      scanf("%d",&n);
      switch(n)
      {
        case 1:
        if((mutex==1)&&(empty !=0))
        {
           producer();
        }
        else
        { 
           printf("Buffer is full");
        }
        break;
        case 2:
        if((mutex==1)&&(full !=0))
        {
           consumer();
        }
        else
        {
           printf("Buffer is empty");
        }
        break;
        case 3:
        printf("We hav studied producer Consumer problem");
        exit(0);
        break;
        }
    }
}


6. Write a program for FCFS disk scheduling algorithm

#include<math.h>
#include<stdio.h>
#include<stdlib.h>
int main()
{
int i,n,req[50],mov=0,cp;
printf("enter the current position\n");
scanf("%d",&cp);
printf("enter the number of requests\n");
scanf("%d",&n);
printf("enter the request order\n");
for(i=0;i<n;i++)
{
scanf("%d",&req[i]);
}
mov=mov+abs(cp-req[0]); // abs is used to calculate the absolute value
printf("%d -> %d",cp,req[0]);
for(i=1;i<n;i++)
{
mov=mov+abs(req[i]-req[i-1]);
printf(" -> %d",req[i]);
}
printf("\n");
printf("total head movement = %d\n",mov);
}


8. FIFO
#include<stdio.h> 
int main() 
{ 
int i,j,n,a[50],frame[10],no,k,avail,count=0; 
printf("\nenter the length of the Reference string:\n"); 
scanf("%d",&n); 
printf("\n enter the reference string:\n"); 
for(i=1;i<=n;i++) 
scanf("%d",&a[i]); 
printf("\n enter the number of Frames:"); 
scanf("%d",&no); 
for(i=0;i<no;i++) 
frame[i]= -1; 
j=0; 
printf("\tref string\t page frames\n"); 
for(i=1;i<=n;i++) 
printf("%d\t\t",a[i]); 
avail=0; 
for(k=0;k<no;k++) 
if(frame[k]=a[i]) 
avail=1; 
if (avail=0) 
{ 
frame[j]=a[i]; 
j=(j+1)%no; 
count++; 
for(k=0;k<no;k++) 
printf("%d\t",frame[k]);
}
printf("\n\n");
}
printf("Page Fault Is %d",count); 
return 0; 
}


         
