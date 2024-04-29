1. Write shell scripts to do the following:
• Display OS version, release number, kernel version
echo ' kernel in your system'
uname -a
#ubuntu version
echo 'ubuntu version and release number '
lsb_release -a
• Display top 10 processes in descending order
echo 'Top processes in descending order'
ps aux|sort -r
• Display processes with highest memory usage.
echo 'Top memory consuming processes'
ps aux --sort -rss|head
• Display current logged in user and log name.
echo 'current login user and log name'
w
• Display current shell, home directory, operating system type, current Path setting,
current working directory.
echo ' Current shell'
ps -p $$
echo 'Display home directory'
ls
echo 'current working directory'
pwd
echo 'operating system type'
uname -r


3. Implement cp and mv command
• cp
#include <stdio.h>
#include <stdlib.h>
int main()
{
FILE *fptr1, *fptr2;
char filename[100], c;
printf("Enter the filename to open for reading \n");
scanf("%s", filename);
fptr1 = fopen(filename,"r"); 
if (fptr1 == NULL)
{
printf("Cannot open file %s \n", filename);
exit(0);
}
printf("Enter the filename to open for writing \n");
scanf("%s", filename);
fptr2 = fopen(filename,"w"); 
if (fptr2 == NULL)
{
printf("Cannot open file %s \n", filename);
exit(0);
}
c = fgetc(fptr1);
while (c != EOF)
{
fputc(c,fptr2); 
c =fgetc(fptr1);
}
printf("\nContents copied to %s", filename);
fclose(fptr1);
fclose(fptr2);
return 0;
}

• mv
#include<stdio.h>
#include<stdlib.h>
int main(){
char old[100], new[100];
printf("Enter old file path:"); 
if (scanf("%99s", old) !=1) {
fprintf(stderr, "Error reading old file path.\n");
exit(EXIT_FAILURE);
}
printf("Enter new file path:"); 
if (scanf("%99s", new) !=1) {
fprintf(stderr, "Error reading new file path.\n");
exit(EXIT_FAILURE);
}
if (rename(old, new) == 0) {
printf("File renamed successfully.\n");
} else {
perror("Unable to rename files");
exit(EXIT_FAILURE);
}
return 0;
}



4.
a. Create a child process using the fork system call.
b. Obtain the process ID of both child and parent by using getpid and getppid
system call
#include <stdio.h>
#include<sys/types.h>
#include <unistd.h>
int main()
{
 fork();
 printf("Hello World!\n");
 printf("Parent Process id = %d\n", getppid());
 printf("Child Process id = %id\n", getpid());
 return 0;
}


5. Write a program to demonstrate the concept of non-pre-emptive
scheduling algorithms.
• FCFS
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
 printf("P[%d] Arrival Time : ", i);
 scanf("%d",&AT[i]);
 printf("P[%d] Burst Time : ", i);
 scanf("%d",&BT[i]);
 }
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


• SJF
#include<stdio.h>
void main()
{
 int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,ps,temp;
 float avg_wt,avg_tat;
 printf("Enter number of process:");
 scanf("%d",&n);
 printf("\nEnter Burst Time:\n");
 for(i=0;i<n;i++)
 {
 printf("p%d:",i+1);
 scanf("%d",&bt[i]);
 p[i]=i+1;
 }
 for(i=0;i<n;i++)
 {
 ps=i;
 for(j=i+1;j<n;j++)
 {
 if(bt[j]<bt[ps])
 ps=j;
 }
 temp=bt[i];
 bt[i]=bt[ps];
 bt[ps]=temp;
 temp=p[i];
 p[i]=p[ps];
 p[ps]=temp;
 }
 wt[0]=0;
 for(i=1;i<n;i++)
 {
 wt[i]=0;
 for(j=0;j<i;j++)
 wt[i]+=bt[j];
 total+=wt[i];
 }
 avg_wt=(float)total/n;
 total=0;
 printf("\n Process \t Waiting Time \t\t\t Turnaround Time");
 for(i=0;i<n;i++)
 {
 tat[i]=bt[i]+wt[i];
 total+=tat[i];
 printf("\n p%d \t\t\t %d\t\t\t %d\t\t %d",p[i],bt[i],wt[i],tat[i]);
 }
 avg_tat=(float)total/n;
 printf("\n\nAverage Waiting Time=%f",avg_wt);
 printf("\nAverage Turnaround Time=%f\n",avg_tat);
}


6. Write a c program to implement the producer-consumer problem
#include <stdio.h>
#include <stdlib.h>
int mutex = 1;
int full = 0;
int empty = 3, x = 0;
void producer()
{
 --mutex;
 ++full;
 --empty;
 x++;
 printf("\nProducer produces item %d", x);
 ++mutex;
}
void consumer()
{
 --mutex;
 --full;
 ++empty;
 printf("\nConsumer consumes item %d", x);
 x--;
 ++mutex;
}
int main()
{
 int n, i;
 printf("\n1. Press 1 for producer\n");
 printf("\n2. Press 2 for consumer\n");
 for (i=1; i>0; i++)
 {
 printf("\nEnter your choice: ");
 scanf("%d", &n);
 switch (n)
 {
 case 1:
 if ((mutex == 1) && (empty != 0))
 {
 producer();
 }
 else
 {
 printf("Buffer is full");
 }
 break;
 case 2:
 if ((mutex == 1) && (full!= 0))
 {
 consumer();
 }
 else
 {
 printf("Buffer is empty");
 }
 break;
 case 3:
 printf("We have studied the Producer Consumer Problem using seaphore");
 exit(0);
 break;
 }
 }
}


7. Write a program for FCFS disk scheduling algorithm
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
 mov=mov+abs(cp-req[0]);
 printf("%d -> %d",cp,req[0]);
 for(i=1;i<n;i++)
 {
 mov=mov+abs(req[i]-req[i-1]);
 printf(" -> %d",req[i]);
 }
 printf("\n");
 printf("total head movement = %d\n",mov);
}



8. Write a program in C to demonstrate the FIFO page replacement algorithm for
handling page faults
#include <stdio.h>
int main()
{
 int i, j, k, n, no, a[50], frame[10], count = 0, isfault;
 printf("\n Enter reference string size : ");
 scanf("%d", &n);
 printf("\n Enter the reference string:\n");
 for (i = 0; i < n; i++)
 {
 scanf("%d", &a[i]);
 }
 printf("\n Enter the Frame Size : ");
 scanf("%d", &no);
 for (i = 0; i < no; i++)
 {
 frame[i] = -1;
 }
 j = 0;
 printf("\treference string \t page frame\n");
 for (i = 0; i < n; i++)
 {
 printf("\t\t%d\t\t", a[i]);
 isfault = 0;
 for (k = 0; k < no; k++)
 {
 if (frame[k] == a[i])
 isfault = 1;
 }
 if (isfault == 0)
 {
 frame[j] = a[i];
 j = (j+1) % no;
 count++;
 }
 for (k = 0; k < no; k++)
 {
 printf("%d\t", frame[k]);
 }
 printf("\n\n");
 }
 printf("\n No of page Fault is %d", count);
 return 0;
}
