# ACSL-WrapAroundCode

//Andrea Shulman
//ACSL Problem 2000-2001

import javax.swing.JOptionPane;
import java.util.ArrayList;

public class WrapAroundCode
{
	private ArrayList<String> input, output;
	private String alpha;

	public WrapAroundCode()//input has all lines as separate strings output is empty
	{
		input=new ArrayList<String>();
      int i=0;
		while(i<4)
		{
         input.add(JOptionPane.showInputDialog("Enter list of capital letters and numbers without spaces."));
         i++;
		}
		alpha="ABCDEFGHIJKLMNOPQRSTUVWXYZ";
		output=new ArrayList<String>();
   }
   
	private void method()
	{
      int num, rule,temp;
		String outp, charac;
		for(int i=0;i<input.size();i++)//goes through all lines of input
		{
			num=1;//position
			temp=0;
			outp="";
			for(int j=0;j<input.get(i).length()-2;j+=2)//goes through each input String w/o $
			{	
            charac=input.get(i).substring(j,j+1); //ignore commas
            rule=Integer.parseInt(input.get(i).substring(j+1,j+2));
            temp=alpha.indexOf(charac)+1;//assigned number
            if(rule==1)
  					num+=temp*2;
				else if(rule==2)
					num+=(temp%3)*5;
				else if(rule==3)
					num+=temp/4*(-8);
				else if(rule==4)
					num+=(((int)Math.sqrt(temp))*(-12))%26;
				else if(rule==5)
					num+=(sumOfFactors(temp)*10);
            if(num>26)
               num= num%26;
            if(num<0)
               num=alpha.length()+num;
            outp+=alpha.substring(num-1,num);
        }
			System.out.println(outp);
		}
   }
   
   public int sumOfFactors(int n)
   {
      int prod=1;
      for(int k=2;k*k<=n;k++)
      {
      	int p=1;
  	   	while(n%k==0)
         {
        		p=p*k+1;
        		n/=k;
       	}
        	prod*=p;
      }
      if(n>1)
         prod*=1+n;
      return prod;
   }
   
   public static void main(String[]args)
   {
      WrapAroundCode test=new WrapAroundCode();
      test.method();
   }
}
