# Multilevel-Queue-Scheduling-with-c
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
struct node1
{
int priority,arrival_time,burst_time;
int process_id,ready;
};
struct node2
{
	int priority_range,process_counter;
	int process_queue[10];
}queue1,queue2,queue3;
int main()
{
int i,j,n;
printf("Enter number of processes\n");
scanf("%d",&n);
 struct node1 process[n];
 struct node2 *q1=&queue1;
  struct node2 *q2=&queue2;
   struct node2 *q3=&queue3;
for(i=0;i<n;i++)
{
printf("Enter process Id\n");
scanf("%d",&process[i].process_id);
printf("Enter Arrival time\n");
scanf("%d",&process[i].arrival_time);
printf("Enter Burst time \n");
scanf("%d",&process[i].burst_time);
printf("Enter priority of process\n");
scanf("%d",&process[i].priority);
}
q1->process_counter=0;
q2->process_counter=0;
q3->process_counter=0;
	for(i=0;i<n;i++)
	{
		if(process[i].priority<=4)
		{
			q1->process_queue[q1->process_counter]=process[i].process_id;
			q1->process_counter+=1;
		}
		if(process[i].priority>4 && process[i].priority<=8)
		{
			q2->process_queue[q2->process_counter]=process[i].process_id;
		q2->process_counter+=1;
		}
		if(process[i].priority>8 && process[i].priority<=12)
		{
			q3->process_queue[q3->process_counter]=process[i].process_id;
			q3->process_counter+=1;
		}
	}
printf("The processes after sorting them to three queues are as\n");
printf("QueueNo\tProcess_id\tProcess_Priority\tProcess_arrival_time\tBurst_time\n");


	if(q1->process_counter>0)
	{
	for(i=0;i<q1->process_counter;i++)
	{
		for(j=0;j<=n;j++)
		{
			if(process[j].process_id==q1->process_queue[i])
			{
				printf("%d\t\t%d\t\t%d\t\t%d\t\t\t%d\n",1,q1->process_queue[i],process[j].priority,process[j].arrival_time,process[j].burst_time);
			}
	    }
    }
    }
    if(q2->process_counter>0)
	{
	for(i=0;i<q2->process_counter;i++)
	{
		for(j=0;j<=n;j++)
		{
			if(process[j].process_id==q2->process_queue[i])
			{
				printf("%d\t\t%d\t\t%d\t\t%d\t\t\t%d\n",2,q2->process_queue[i],process[j].priority,process[j].arrival_time,process[j].burst_time);
			}
		}
    }
    }
    if(q3->process_counter>0)
	{
	for(i=0;i<q3->process_counter;i++)
	{
		for(j=0;j<=n;j++)
		{
			if(process[j].process_id==q3->process_queue[i])
			{
				printf("%d\t\t%d\t\t%d\t\t%d\t\t\t%d\n",3,q3->process_queue[i],process[j].priority,process[j].arrival_time,process[j].burst_time);
			}
		}
}
}
}
