#include<iostream>
#include<sstream>
#include<string>

using namespace std;

class complx{
    private:
    int x, y, u, v;
    string s;
    void extract(string);
    int extract(string, int, int);
    void process(complx, complx);
    void input();
    
    public:
    void output();
};

void complx:: extract(string st){
    int i=0, val[2];
    int l=st.length();
    for( ; i<2; i++)
    val[i]=extract(st, i+i, l);
    
    x=val[0];
    y=val[1];
}
int complx:: extract(string str, int j, int n){
    string r,ar;
    int q=j;
    for( ; j<n; j++){
        ar=str.substr(j,j+1);
        if(ar=="i"||ar=="I")
        break;
        else if(j!=0&&(ar=="+"||ar=="-")&&q==0)
        break;
        
        r+=ar.substr(0,1);
        
    }
    stringstream m(r);
    
    int em=0;
    m>>em;
    return em;
}
void complx:: process(complx no_one, complx no_two){
    int a, b, c, d;
    a = no_one.x;
    b = no_one.y;
    c = no_two.x;
    d = no_two.y;
    u = (a*c) - (b*d);
    v = (a*d) + (b*c);
}
void complx:: input(){
    cout<<"Enter a complex no. in the form of 'a+bi':"<<endl;
    cin>>s;
    
}
void complx:: output(){
    complx com1;
    complx com2;
    com1.input();
    com2.input();
    com1.extract(com1.s);
    com2.extract(com2.s);
    process(com1,com2);
    cout<<"The product of ("<<com1.s<<") and ("<<com2.s<<") is: ("<<u<<"+("<<v<<")i)"<<endl;
}

int main(){
    complx obj;
    obj.output();
    return 0;
}

