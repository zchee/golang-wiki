import java.util.*;
public class main 
{

    public static void main(String[] args) 
    {
       
        Scanner input = new Scanner(System.in);
        String[] Name = {"elena","thomas","james","douglas","jane","emily","john"};
        

         int count = 0;
         int min = 999999;
        for(int j=0;j<=6;j++)
        {
           
            
            System.out.format("Tedade Timehaye sabt shode baraye %s ra vared konid \n", Name[j]);
            int x = input.nextInt();
        
            int[] a =new int[x];
            
            int[] minTime= new int[7];
            for(int z=0;z<=a.length-1;z++)
            {
                
             System.out.format("  %dth timeh sabt shode baraye %s ra vared konid  \n",z+1, Name[j]);   
                int[] b;
                
                b = new int[a.length];
                
               b[z]  = input.nextInt();
               
              
               if(b[z]<min)
               {
                   min = b[z];
               }
                
                minTime[j]=min;
                
                while(count>=6)
                {

System.out.format("Name\t\t\t\tTime(minute)\n");

                  for(int y=0;y<7;y++)
                  {
                   System.out.println(Name[y]+"\t\t\t\t"+minTime[y]);
                  }
                  break;
        
                }
                
            }
            
        count++;

        }

        
      
        
        
        }
        

        
        
        
        
        
 }
    

