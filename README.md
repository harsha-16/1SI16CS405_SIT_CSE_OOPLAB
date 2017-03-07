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



#include<iostream>
using namespace std;

class FRACTION_TYPE
{
	private:
		int iNum,iDen;
	public:
		void fnSetFraction(int,int);
		void fnShowFraction();
		void fnAddFraction(FRACTION_TYPE);
		void fnReduceFraction();
};
int gcd(int ,int );

void FRACTION_TYPE::fnSetFraction(int iN,int iD)
{
	iNum=iN;
	iDen=iD;
}

void FRACTION_TYPE::fnShowFraction()
{
	cout<<iNum<<"/"<<iDen<<endl;
}


void FRACTION_TYPE::fnAddFraction(FRACTION_TYPE f2)
{
	FRACTION_TYPE f3;
	
	f3.iNum=(iNum*f2.iDen) + (iDen*f2.iNum);
	f3.iDen=iDen*f2.iDen;
	
	f3.fnShowFraction();
	
	cout<<"\n simplified form=";
	f3.fnReduceFraction();
}

void FRACTION_TYPE::fnReduceFraction()
{
	int d;
	d=gcd(iNum,iDen);
	iNum=iNum/d;
	iDen=iDen/d;	
	
	fnShowFraction();
}

int gcd(int m,int n)
{
	if(n==0)
		return m;
	else
		return (gcd(n,m%n));
}

int main()
{
	FRACTION_TYPE f1,f2;
	
	int iN,iD;
	
	cout<<"\nenter numenator and denaminator of the Fraction1"<<endl;
	cin>>iN>>iD;
	f1.fnSetFraction(iN,iD);
	
	cout<<"\nenter numenator and denaminator of the Fraction2"<<endl;
	cin>>iN>>iD;
	f2.fnSetFraction(iN,iD);
	
	cout<<"Fraction 1 is =";
	f1.fnShowFraction();
	
	cout<<"Fraction 2 is =";
	f2.fnShowFraction();
	
	cout<<"sum of two  Fraction is=";	
	f1.fnAddFraction(f2);	
	
	return 0;
}
