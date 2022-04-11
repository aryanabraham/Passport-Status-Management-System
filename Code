#include<iostream>
#include<string>
#include<fstream>
#include<windows.h>
using namespace std;

class UserData //class used in project
{
    public:
        char gender;
        string name;
        string dob;
        string fname;
        string address;
        string pass;
        string stat = "PENDING";
        string secQ;

};  //class ends here



//global declaration of stream

fstream fp;

//global declaration of object

UserData user;

//function to add record of new user in file

void user_new()
{
    //changes background color and font of console
    
    system("color 4F");
    
    string rep;
    fp.open("C:\\Users\\Aryan\\Desktop\\Mini Project\\data.txt", ios :: out | ios :: app | ios :: binary);

    //condition to return to main function if file not found

    if(!fp)
    {
        cout<<"\nUNABLE TO OPEN FILE\n\n"<<endl;
        return;
    }

    cin.ignore();
    cout<<"\nEnter your name: ";
	getline(cin, user.name);
	cout<<"Enter your dob (DD/MM/YYYY): ";
	getline(cin, user.dob);
	cout<<"Enter your gender (M/F): ";
	cin>>user.gender;
	cin.ignore();
	cout<<"Enter your father's name: ";
	getline(cin, user.fname);
	cout<<"Enter your address: ";
	getline(cin, user.address);
	cout<<"Enter new password: ";
	getline(cin, user.pass);

	//loop to double-check password

	while(1)
	{
		cout<<"Re-enter password: ";
		getline(cin, rep);

		if(!(user.pass).compare(rep))
			break;

		cout<<"\nPASSWORDS DO NOT MATCH\n\n";
	}

	//data member to revive account in case of forgotten password

    cout<<"\nEnter your pet name [SECURITY QUESTION]: ";
	getline(cin, user.secQ);

	cout<<"\nProcessing...";

	//adds delay of 3000 milliseconds before next output

	Sleep(3000);

	cout<<"\n\n<<REQUEST FOR NEW PASSPORT SUCCESSFULLY SUBMITTED>>\n\n";
    fp.write((char*)&user, sizeof(user));
    fp.close();
    cin.ignore();
}

//function to read record of existing user

void user_ex()
{
    //changes background color and font of console
    
    system("color 4F");
    
    string name;
    string secQ;
    string pass;

    fp.open("C:\\Users\\Aryan\\Desktop\\Mini Project\\data.txt", ios :: in | ios :: binary);

    //condition to return to main function if file not found

    if(!fp)
    {
        cout<<"\nUNABLE TO OPEN FILE\n\n"<<endl;
        return;
    }

    cin.ignore();

    //logging in existing account

    cout<<"\nEnter your name: ";
    getline(cin, name);

    while(fp.read((char*)&user, sizeof(user)))
    {

        //loop to find user in file

        if(!((name).compare(user.name)))
            {
                cout<<"\nWelcome back, "<<user.name<<"!";
                cout<<"\n\nPlease enter your password: ";
                getline(cin, pass);

                //condition to check if password corresponds to user

                if(!(pass.compare(user.pass)))
                {
                    cout<<"\nRECORD FOUND"<<endl;
                    cout<<"\nNAME: "<<user.name<<endl;
                    cout<<"DOB: "<<user.dob<<endl;
                    cout<<"GENDER: "<<user.gender<<endl;
                    cout<<"FATHER'S NAME: "<<user.fname<<endl;
                    cout<<"ADDRESS: "<<user.address<<endl;
                    cout<<"\nSTATUS: "<<user.stat<<"\n\n";
                    fp.close();
                    return;
                }
                cout<<"\nINCORRECT PASSWORD\n";

                //retrieving account when incorrect password is entered

                cout<<"\nEnter your pet name [SECURITY QUESTION]: ";
                getline(cin, secQ);

                //condition to check if security question corresponds to user

                if(!(secQ.compare(user.secQ)))
                {
                    cout<<"\nRECORD FOUND"<<endl;
                    cout<<"\nNAME: "<<user.name<<endl;
                    cout<<"DOB: "<<user.dob<<endl;
                    cout<<"GENDER: "<<user.gender<<endl;
                    cout<<"FATHER'S NAME: "<<user.fname<<endl;
                    cout<<"ADDRESS: "<<user.address<<endl;
                    cout<<"\nSTATUS: "<<user.stat<<"\n\n";
                    fp.close();
                    return;
                }
                cout<<"\nINCORRECT ANSWER\n\n";
                fp.close();
                return;
            }
    }
    cout<<"\nUSER NOT FOUND\n\n";
   fp.close();
}

//function to read records of all users from file

void admin_viewAll()
{
    //changes background color and font of console
    
    system("\ncolor 4F");
    
    string pass;

    fp.open("C:\\Users\\Aryan\\Desktop\\Mini Project\\data.txt", ios :: binary | ios :: in | ios :: out);

    //condition to return to main function if file not found

    if(!fp)
    {
        cout<<"\nUNABLE TO OPEN FILE\n\n"<<endl;
        return;
    }

    cin.ignore();

    //password to log into admin account

    cout<<"\nEnter admin password: ";
    getline(cin, pass);

    //condition to check if password entered corresponds to pre-set password

    if(!(pass.compare("password")))
    {

        //loop to display records of all users

        while(fp.read((char*)&user, sizeof(user)))
        {
            {
                cout<<"\nNAME: "<<user.name<<endl;
                cout<<"DOB: "<<user.dob<<endl;
                cout<<"GENDER: "<<user.gender<<endl;
                cout<<"FATHER'S NAME: "<<user.fname<<endl;
                cout<<"ADDRESS: "<<user.address<<endl;
                cout<<"\nSTATUS: "<<user.stat<<"\n\n";
            }
        }
    }
    fp.close();
}

//function to change status of a user from file

void admin_changeStat()
{
    //changes background color and font of console
    
    system("\ncolor 4F");
    
    string name;
    string pass;

    fp.open("C:\\Users\\Aryan\\Desktop\\Mini Project\\data.txt", ios :: binary | ios :: in | ios :: out);

    //condition to return to main function if file not found

    if(!fp)
    {
        cout<<"\nUNABLE TO OPEN FILE\n\n"<<endl;
        return;
    }

    cin.ignore();

    //password to log into admin account

    cout<<"\nEnter admin password: ";
    getline(cin, pass);

    if(!(pass.compare("password")))
    {

        //reading name of user whose status is to be changed

        cout<<"\nEnter user name: ";
        getline(cin, name);

        while(fp.read((char*)&user, sizeof(user)))
        {
            //condition to check if user is in record

            if(!((name).compare(user.name)))
            {
                cout<<"\nChanging status of "<<user.name<<"...\n";

                //adds delay of 3000 milliseconds before next output

                Sleep(3000);

                //changing status of user

                long long unsigned int position = (-1)*sizeof(UserData);
                user.stat = "APPROVED";
                fp.seekp(position, ios :: cur);
                fp.write((char*)&user,sizeof(user));
                cout<<"\nSTATUS CHANGED\n\n";
                fp.close();
                return;
            }
        }
        cout<<"\n<<RECORD NOT FOUND>>\n\n";
        fp.close();
        return;
    }
    cout<<"\nINCORRECT PASSWORD\n\n";
    fp.close();
}

//main function of program

int main()
{
    int choice;
    while(1)
    {
        //changes background color and font of console
        
        system("\ncolor 4F");

        cout<<"******* MAIN MENU ********"<<endl<<endl;
        cout<<"1. User Menu\n2. Admin Menu\n3. Exit"<<endl;
        cout<<"\nPlease enter your choice: ";
        cin>>choice;
        cout<<"\n**************************\n";

        switch(choice)
        {
            case 1:
                //shows user menu
                {
                    cout<<"\n******* USER MENU ********"<<endl<<endl;
                    cout<<"1. New User\n2. Existing User\n3. Go Back To Previous Menu"<<endl;
                    cout<<"\nPlease enter your choice: ";
                    cin>>choice;
                    cout<<"\n**************************\n";

                    switch(choice)
                    {
                        case 1: user_new();
                                break;

                        case 2: user_ex();
                                break;

                        case 3: break;

                        default: cout<<"Please enter correct input!"<<endl;
                    }
                    break;
                }

            case 2:
                //shows admin menu
                {
                    cout<<"\n******* ADMIN MENU ********"<<endl<<endl;
                    cout<<"1. View All Status\n2. Change Status\n3. Go Back To Previous Menu"<<endl;
                    cout<<"\nPlease enter your choice: ";
                    cin>>choice;
                    cout<<"\n***************************\n";

                    switch(choice)
                    {
                        case 1:
                            //shows records of all users
                                admin_viewAll();
                                break;

                        case 2:
                            //changes status of given user
                                admin_changeStat();
                                break;

                        case 3: break;
                    }
                    break;
                }

            case 3:
                //exits the program
                    cout<<"\nGoodbye!\n";
                    exit(0);

            default: cout<<"Please enter correct input!"<<endl;
        }
    }
    return 0;
}

//end of project
