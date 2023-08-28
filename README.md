FCFS Implementation with varying arrival times
#include<iostream>
using namespace std;
 /* Function for calculating the total waiting_time for all the processes */
void find_Waiting_Time(int process[], int n, int b_t[], int w_t[])
{
   	 // waiting time for first process is 0
    	w_t[0] = 0;
 	// calculating waiting time
    	for (int  x = 1; x < n ; x++ )
        	w_t[x] =  b_t[x-1] + w_t[x-1] ;
}
 
/* Calculating turn_around time using this function */
void find_TurnAround_Time( int process[], int n, int b_t[], int w_t[], int ta_t[])
{
    	/* adding b_t[x] + w_t[x] to calculate the turn_around time */
    	for (int x = 0; x < n ; x++)
        	ta_t[x] = b_t[x] + w_t[x];
}
 
/* Calculating avg_time time using this function */
void find_avg_Time( int process[], int n, int b_t[])
{
    	int w_t[n], ta_t[n], wt_total = 0, tat_total = 0;
 	/* Function for calculating the waiting_time of all the operations */
    	find_Waiting_Time(process, n, b_t, w_t);
 	/* Function for calculating turn_around time for all the processes available */   	find_TurnAround_Time(process, n, b_t, w_t, ta_t);
 	/* Display all the procedures with all the available details */
    	cout << "Processes  "<< " Burst time  "
         	<< " Waiting time  " << " Turn around time\n";
 	/* The total_turn_around time and the total_wait time should be calculated */
    	for (int  x=0; x<n; x++)
    	{
        		wt_total = wt_total + w_t[x];
        		tat_total = tat_total + ta_t[x];
        		cout << "   " << x+1 << "\t\t" << b_t[x] <<"\t    "
            	<< w_t[x] <<"\t\t  " << ta_t[x] <<endl;
    	}
 
    	cout << "Average waiting time = "
         	<< (float)wt_total / (float)n;
    	cout << "\nAverage turn around time = "
         	<< (float)tat_total / (float)n;
}
 
int main()
{
    	/*  identifiers for all the processes */
    	int process[] = { 1, 2, 3};
    	int n = sizeof process / sizeof process[0];
 	/* burst_time of all the available processes */
    	int  burst_time[] = {10, 5, 8};
 	find_avg_Time(process, n,  burst_time);
    	return 0;
}
