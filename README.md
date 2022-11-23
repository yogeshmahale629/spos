import java.util.*;
public class fcfs {

	public static void main(String[] args)
	{
		Scanner sc=new Scanner(System.in);
		int p;
		System.out.print("Enter number of processes: ");
		p=sc.nextInt();
		int process[]=new int[p];
		int at[]=new int[p];
		int bt[]=new int[p];
		System.out.println("Enter Arrival time and Brust time");
		
		for(int i=0;i<p;i++)
		{
			System.out.print("p["+(i+1)+"]: ");
			at[i]=sc.nextInt();
			bt[i]=sc.nextInt();
		}
		fcfs(p,at,bt);
		
	}
	static void fcfs(int p,int at[],int bt[])
	{
		int ct[]=new int[p];
		int tat[]=new int[p];
		int wt[]=new int[p];
		if(at[0]==0)
		ct[0]=bt[0];
		else
		ct[0]=at[0]+bt[0];
		for(int i=1;i<p;i++)
		{
			if(ct[i-1]>=at[i])
			{
				ct[i]=ct[i-1]+bt[i];
			}
			else
			{
				ct[i]=at[i];
				ct[i]=ct[i]+bt[i];
				
			}
		}
		wt[0]=0;
		tat[0]=ct[0]-at[0];
		for(int i=1;i<p;i++)
		{
			tat[i]=ct[i]-at[i];
			wt[i]=tat[i]-bt[i];
		}
		float ttat=0,twt=0;
		System.out.println("Process"+"\t"+"AT"+"\t"+"BT"+"\t"+"CT"+"\t"+"TAT"+"\t"+"WT");
		for(int i=0;i<p;i++)
		{
			System.out.println("p["+(i+1)+"]"+"\t"+at[i]+"\t"+bt[i]+"\t"+ct[i]+"\t"+tat[i]+"\t"+wt[i]);
			ttat+=tat[i];
			twt+=wt[i];
		}
		System.out.println("Avarage Turn Around Time: "+(float)(ttat/p));
		System.out.println("Avarage Waiting Time: "+(float)(twt/p));
		
	}
}
