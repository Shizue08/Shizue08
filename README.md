I'm- 👋 Hi, I’m @Shizue08
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Shizue08/Shizue08 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

import java.util.Scanner;

public class FCFS_Scheduling {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter the number of processes: ");
        int n = sc.nextInt();

        int[] processes = new int[n];
        int[] burstTime = new int[n];
        int[] completionTime = new int[n];
        int[] turnaroundTime = new int[n];
        int[] waitingTime = new int[n];

        // Input the burst time for each process
        for (int i = 0; i < n; i++) {
            processes[i] = i + 1;
            System.out.print("Enter burst time for process " + (i + 1) + ": ");
            burstTime[i] = sc.nextInt();
        }

        // Calculating completion time
        completionTime[0] = burstTime[0];
        for (int i = 1; i < n; i++) {
            completionTime[i] = completionTime[i - 1] + burstTime[i];
        }

        // Calculating turnaround time and waiting time
        for (int i = 0; i < n; i++) {
            turnaroundTime[i] = completionTime[i];
            waitingTime[i] = turnaroundTime[i] - burstTime[i];
        }

        // Displaying the results
        System.out.println("\nProcess\tBurst Time\tCompletion Time\tTurnaround Time\tWaiting Time");
        for (int i = 0; i < n; i++) {
            System.out.println("P" + processes[i] + "\t\t" + burstTime[i] + "\t\t" + completionTime[i] + "\t\t" + turnaroundTime[i] + "\t\t" + waitingTime[i]);
        }

        // Calculating average turnaround time and average waiting time
        double totalTurnaroundTime = 0;
        double totalWaitingTime = 0;
        for (int i = 0; i < n; i++) {
            totalTurnaroundTime += turnaroundTime[i];
            totalWaitingTime += waitingTime[i];
        }

        System.out.println("\nAverage Turnaround Time: " + (totalTurnaroundTime / n));
        System.out.println("Average Waiting Time: " + (totalWaitingTime / n));

        sc.close();
    }
}
