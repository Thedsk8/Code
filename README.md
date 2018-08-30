# Instruction to compile
Use C++ compiler to compile the code


# Code
#include <iostream>
// to use sting datatype and its inbuilt function 
#include<string.h>
using namespace std;

struct Date
{
    int month;
    int year;
    int day;
};

struct node
{
    int OwnerId;
    string OwnerName;
    Date timestamp;
    int nodeNumber;
    string data;
    string nodeId;
    node * referenceNodeId;
    node * childRefernceNodeId;
    node * genesisrefernceNodeId;
    string HashValue;
};

int main() 
{
    node * GenesisNode;
    //Creating a GenesisNode
    GenesisNode = new node;
    //Intialising its parent to NULL
    GenesisNode->referenceNodeId = NULL;
    GenesisNode->OwnerId = 1;
    GenesisNode->OwnerName = "record";
    //Adding owner id to ownername so its name will now be record1
    GenesisNode->OwnerName += to_string(GenesisNode->OwnerId);
    string data;
    //data contains Value
    GenesisNode->data = "";
    GenesisNode->data+=to_string(GenesisNode->OwnerId);
    int i,flag=1,count=0;
    // count is used to make sure we have used number upt 2 decimal places
    //flag is used to find out the point afte which decimal values start
    for(i=0;i<data.length();i++)
    {
        GenesisNode->data += data[i];
        if(flag==1)
        {
            count++;
            if(count==2)
                break;
        }
        if(data[i] == '.')
        {
            flag=1;
        }
    }
    GenesisNode->data+=GenesisNode->OwnerName;
    // Now data is encrypted. Value lie betwen Ownerid and OwnerName
    
    // To decrypt
    string Id = to_string(GenesisNode->OwnerId);
    for(i=0;i<GenesisNode->data.length();i++)
    {
        if(Id[i]!=GenesisNode->data[i])
            break;
    }
    string value="";
    int j;
    for(j=i;j<GenesisNode->data.length();j++)
    {
        //When First letter of OwmerName Is found We need to break;
        if(isalpha(GenesisNode->data[i]))
            break;
        value += GenesisNode->data[i];
    }
    
    //To enter timestamp we can ask user to enter month ,day,year and display it using Date Structure
    
    // To create a child 
    GenesisNode->childRefernceNodeId =new node;
    //Similar process will follow to create this node
    
	return 0;
}
