# 1SI16CS405_SIT_CSE_OOPLAB


#include<iostream>
using namespace std;
class loc{
	int longitude,latitude;
	public:
		loc(){};
		loc(int lg,int lt)
		{
			longitude=lg;
			latitude=lt;
		}
		
		void fnShow()
		{
			cout<<longitude<<"	";
			cout<<latitude<<"\n";
		}
		loc operator+(loc op2);
		loc operator,(loc op2);
};

//overload comma (,)
loc loc::operator,(loc op2)
{
	loc temp;
	temp.longitude=op2.longitude;
	temp.latitude=op2.latitude;
	
	cout<<longitude<< "	"<<latitude<<endl;
	cout<< op2.longitude<< "	"<<op2.latitude<<endl;
	
	return temp;
}

//overload + for loc
loc loc:: operator+(loc op2)
{
	loc temp;
	temp.longitude=op2.longitude + longitude;
	temp.latitude=op2.latitude + latitude;
	
	return temp;
}
int main()
{
	loc ob1(10,20),ob2(5,30),ob3(1,1);
	
	ob1.fnShow();
	ob2.fnShow();
	ob3.fnShow();
	
	cout<< "\n";
	ob1=(ob1,ob2+ob2,ob3);//first is ob2+ob2=temp, 1st call is ob1.operator(temp),2nd call is return value of objt.operator(ob3)	
	ob1.fnShow();			//after returned objt is assign(=) to ob1
	
	return 0;
}
