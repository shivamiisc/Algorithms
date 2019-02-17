# Algorithms
This repository contains basic algorithms in C++.Feel free to comment. Edits are welcome
###############################################################
Below is code for the Knapsack problem using the greedy method
###############################################################

                                          <- Knapsack Problem ->

#include <cstdlib>
#include<iostream>
#include<vector>
#include<iomanip>
using namespace std;
int main() {
    int objects,index,k;
    float bin,knapsack,totalprofit;
    cin>>objects;
    float weight[objects];
    float profit[objects];
    float x[objects];
    for(int i=0;i<objects;i++)
    {
        cin>>weight[i];
    }
    for(int i=0;i<objects;i++)
    {
        cin>>profit[i];
    }
    
    vector<float> pbw;
    for(int i=0;i<objects;i++)
    {
        bin=profit[i]/weight[i];
        pbw.push_back(bin);
    }
     for(int i=0;i<objects;i++)
     {
         cout<<pbw[i]<<" ";
     }
    cin>>knapsack;
     for(int i=0;i<objects;i++)
    {
        x[i]=0;
    }
    
    while(knapsack>0)
    {
 
        index=max_element(pbw.begin(),pbw.end()) - pbw.begin();
        pbw[index]=0;
        
        if(weight[index]<=knapsack)
        {
            knapsack=knapsack-weight[index];
            x[index]=1;
        }
        else if(weight[index]>knapsack)
        {
            x[index]=knapsack/weight[index];
            knapsack=0;
        }
            
    }
    totalprofit=0;
    for(int i=0;i<objects;i++)
    {
        totalprofit=totalprofit+(x[i]*profit[i]);
    }
    cout<<totalprofit;
        
    
    return 0;
}

