#include <stdio.h>
#include <string> 
#include <iostream>
#include <algorithm> 
#include <vector>
#include<sstream>
#include <ctype.h>
using namespace std;


class Robot {
    
private:
    int x = 0;
    int y = 0;

    char current_dir = 'N';
    
    string ltrim(string s) 
    {
            s.erase(
                s.begin(),
                find_if(s.begin(), s.end(), not1(ptr_fun<int, int>(isspace)))
            );
        
        return s;
    }
        
    string rtrim(string s) 
    {
            s.erase(
                find_if(s.rbegin(), s.rend(), not1(ptr_fun<int, int>(isspace))).base(),
                s.end()
            );
        
        return s;
    }
    
public:
    bool process_command(string input) {
            string instructions = ltrim(rtrim(input));

            if(instructions.compare("MOVE") == 0 )  
            {

                y += (current_dir =='N' ? (y+1 > 5 ? 0 : 1) : 0);
				y += (current_dir =='S' ? (y-1 < 0  ? 0 : -1) : 0);
				x += (current_dir == 'E' ? (x+1 > 5 ? 0 : 1) : 0);
				x += (current_dir == 'W' ? (x-1 < 0 ? 0 : -1) : 0);
            }
            else if(int pos = instructions.find("PLACE ") != std::string::npos)
            {
                string command = "PLACE ";
                vector<string> result;
                
                //Remove the "PLACE " command in string
               if (int pos = instructions.find(command) != std::string::npos){
                    instructions.erase(pos - 1 , command.length());
                    //cout<<"instructions="<<instructions<<endl;
               }
               
               
               stringstream s_stream( instructions ); 
               
               
               while(s_stream.good()) {
                  string substr;
            
                  if (getline(s_stream,substr, ',')){ //get first string delimited by comma
                    result.push_back(substr);
                  }
               }
               //for(int i = 0; i<result.size(); i++) {    //print all splitted strings
                  //cout << i<<" "<< result[i] << endl;
                  
               //}
               
               if(stoi(result[0]) > 5 || stoi(result[0]) < 0 ||stoi(result[0]) > 5 || stoi(result[0]) < 0 ) 
                    displayError(2);
                else{
                    x = stoi(result[0]);
                    y = stoi(result[1]);
                }

               
               result[2] = ltrim(rtrim(result[2]));
               current_dir = (toupper(result[2][0]));
                
            
            }
            else if(instructions.compare("LEFT") == 0)
            {
                switch (current_dir){
                case 'N':
                    current_dir = 'W';
                    break;
                case 'S':
                    current_dir = 'E';
                    break;
                case 'E':
                    current_dir = 'N';
                    break;
                case 'W':
                    current_dir = 'S';
                    break;
                default:
                    ;
                }
                
            } 
            else if(instructions.compare("RIGHT") == 0)
            {
                switch (current_dir)
                {
                case 'N':
                    current_dir = 'E';
                    break;
                case 'S':
                    current_dir = 'W';
                    break;
                case 'E':
                    current_dir = 'S';
                    break;
                case 'W':
                    current_dir = 'N';
                    break;
                default:
                    ;
                }
            }
            else if(instructions.compare("REPORT") == 0)
            {
                string direction;
                switch(current_dir)
                {
                case 'N':
                    direction = "NORTH";
                    break;
                case 'S':
                    direction = "SOUTH";
                    break;
                case 'E':
                    direction = "EAST";
                    break;
                case 'W':
                    direction = "WEST";
                    break;
                default:
                    ;
                }
                cout<<x<<","<<y<<", "<<direction<<endl;
            }
            else
                displayError(1);
            
        return true;
        }
        
        void displayError(int err)
        {
            switch(err){
            case 1:
                cout<< "Error:Invalid Command"<<endl;
                break;
            case 2:
                cout<< "Error: Initial Position Out Of Range"<<endl;
                break;
            default:
                cout<< "Unknown Error Code"<<endl;
            }
        }
        
    };






int main()
{
    cout<<" ################################"<<endl;
    cout<<" Enter instructions for Toy Robot"<<endl;
    cout<<" ################################"<<endl;
    
    Robot toy_robs;
    string instruction;
    
    while (true)
    {
        getline(cin, instruction);
        toy_robs.process_command(instruction);
        
    }
    
    return 0;
}
