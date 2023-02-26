import java.util.Scanner;
import java.io.*;
import java.util.*;

public class Main{
    public static boolean ifAnyNegativeValue(int[] redCount,int n)
    {    boolean found=false;
        for (int i = redCount.length - 1; i >= 0; i--) {
            
            if (redCount[i] < 0) {
             found=true;}}
             return found;
            
    }
    public static void swapper(char[][] grid,int[] redCount,int n)
    {  boolean found = false;
        
        char temp[][]=new char[n][n];
        for (int i = redCount.length - 1; i >= 0; i--) {
            if (redCount[i] < 0) {
                for (int j = i ; j >= 0; j--) {
                    if (redCount[j] < 0) {
                        if(redCount[j+1]!=0){
                        temp[i] = grid[j + 1];
                        grid[j + 1] = grid[i];
                        grid[i] = temp[i];
                        found = true;
                        
                        break;}
                        if(redCount[j+1]==0){
                        temp[i] = grid[j + 2];
                        grid[j + 2] = grid[i+1];
                        grid[i+1] = temp[i];
                        found = true;
                        
                        break;}
                        
                    }
                }
                if (found) {
                    break;
                }
            }
        }
        ;
        for (int i = 0; i < n; i++){
           for (int j = 0; j < n; j++){
            System.out.print(grid[i][j]);
        }
        System.out.println("");
            
        }
        
    }
        
        public static void red(char[][] grid,int[] redCount,int n)
        {
        for (int i = 0; i < n; i++) {
            for (int j = n-1; j>=0; j--) {
                if (grid[i][j] == 'R') {
                    redCount[i]=i-j;
                    break;
                }}}
            System.out.println("Original Array: " + Arrays.toString(redCount));
        }
        
        
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        sc.nextLine();
        char[][] grid = new char[n][n];
        for (int i = 0; i < n; i++) {
            grid[i] = sc.nextLine().toCharArray();
        }
        int redCount[] = new int[n];
        red(grid,redCount,n);
    
                int sum=0;
                int swap=0;
                for(int i=0;i<n;i++){
                    sum=sum+redCount[i];
                   
                    
                }
                if(Math.abs(sum)!=sum)
                   System.out.println(-1);
                   else
                    {//swapper(grid,redCount,n);
                    while(ifAnyNegativeValue(redCount,n)){
                        swapper(grid,redCount,n);
                    red(grid,redCount,n);
                    
                        swap++;
                    }
                   // red(grid,redCount,n);
                   // swapper(grid,redCount,n);
                   //     red(grid,redCount,n);
                   // swapper(grid,redCount,n);
                  //  red(grid,redCount,n);
                   // swapper(grid,redCount,n);
                   // red(grid,redCount,n);
                   // swapper(grid,redCount,n);
                    //red(grid,redCount,n);
                   // swapper(grid,redCount,n);
                    }
                    
                   System.out.println(swap);
                    
                    
                  // int[] arr = {0, 1, -1, 0, 2};
       // System.out.println("Original Array: " + Arrays.toString(arr));
     }}
