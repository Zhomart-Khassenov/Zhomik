package com.company;

import java.util.Scanner;
import java.lang.String;

public class Main {
    public static void main(String[] args) {
        String[] var;
        int[] vrem;
        int n;
        Scanner in = new Scanner(System.in);
        System.out.print("Введите количество процессов :");
        n = in.nextInt();
        var = new String[n+1];
        for (int i=0; i<=n;i++) {var[i] = in.nextLine();System.out.print("Введите назвния процессa" + "(" + i + "): ");}
        System.out.println();
        vrem = new int[n+1];
        for (int i = 1; i <= n; i++) {RR och = new RR(var[i], 0, vrem[i]);
            System.out.print("Время выполнения  " + och.getName() + "=");
            vrem[i] = in.nextInt(); }
        int len = -100;
        for (int i = 1; i <= n; i++) { if(vrem[i] > len){ len = vrem[i];}}
        System.out.println();
        System.out.println("Цикл повтора " + len + " раз");
        System.out.println();
        int m;
        int[] time = new int[n+1];
        for(int i=1;i<=n;i++){ time[i] = i-1;}
        m=time[n];
        for(int j=0;j<len;j++){
            for (int i = 1; i <= n; i++) {
                RR och = new RR(var[i], 0, vrem[i]);
                if(vrem[i] > 1){ time[i]+=m;
                    System.out.print(och.getName());
                    och.setBurst_time(och.getBurst_time()-1);
                    vrem[i]=och.getBurst_time();}
                else if(vrem[i] == 1){
                    System.out.print(och.getName());
                    och.setBurst_time(och.getBurst_time()-1);
                    vrem[i]=och.getBurst_time();
                    m-=1;}
                else{och.setBurst_time(och.getBurst_time());
                    vrem[i]=och.getBurst_time();}}
            System.out.println();}System.out.println();
        float mid = 0;
        for(int i=1;i<=n;i++){
            RR och = new RR(var[i], 0, vrem[i]);
            och.setArr_time(mid+=((time[i]/4)+(time[i]%4*0.1)));
            System.out.println("Общее время " + var[i] + " = " + time[i] + "сек.");}
        System.out.println();
        System.out.println("В среднем на каждый процесс = " + mid + "сек.");}}
        //-------------------------------------------------------------------
        package com.company;

import java.util.Scanner;
import java.lang.String;

class RR {
    private String name;
    private float arr_time;
    private int burst_time;
    //public int burst_time;

    public RR(String name,float arr_time, int burst_time){
        this.name = name;
        this.arr_time = arr_time;
        this.burst_time = burst_time;
    }

    public String getName(){
        return  name;
    }

    public void setName(String name){
        this.name = name;
    }

    public float getArr_time(){
        return arr_time;
    }

    public void setArr_time(float arr_time){
        this.arr_time = arr_time;

    }

    public int getBurst_time(){
        return burst_time;
    }

    public void setBurst_time(int burst_time){
        this.burst_time = burst_time;
    }

}
