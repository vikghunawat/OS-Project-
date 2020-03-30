# OS-Project-
Problem :
 Write a C program using the fork() system call that generates this sequence in the child process. The starting number will be provided from the user. For example, if 8 is passed as a parameter on the command line, the child process will output 8, 4, 2, 1. Because the parent and child processes have their own copies of the data, it will be necessary for the child to output the sequence. Have the parent invoke the wait() call to wait for the child process to complete before exiting the program. Perform necessary error checking to ensure that a positive integer is passed on the command line. 







//Necessary header files needed.
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>

int main()
{
	printf("\n\nWelcome to OS project  \n");

	int n=0;
	int g=0;
	
	pid_t pid;

		do
		{
			printf("Input number : \n"); 
  			scanf("%d", &g);
  			//Here user input has been taken by the user .
			if(g<0)
			{
				printf("Invalid Input given , plz input again .\n");
		    }
		    //If user inputs invalid input then invalid input is printed .
		}while (g <= 0);
		

		pid = fork();
		//Here fork system call is called .

		if (pid == 0)
		//child process is working as the value is set to zero.
		{
			printf("-----Child is working------ :\n");
			printf("%d\n",g);
			while (g!=1)//checked if last section of the value is reaached or not.
			{
				if (g%2 == 0)
				{
					g = g/2;
				}
				else if (g%2 == 1)
				{
					g = 3 * (g) + 1;
				}	
			
				printf("%d\n",g);
			}
		
			printf("-----Child process is completed.-----\n");
		}
		else
		{
			printf("----Parent process has to wait for child process.-----\n");
			wait(NULL);
			//Wait fucntion call is placed.
			printf("----Parent process is done.----\n");
			//Final program executed.
		}
	return 0; 
}
