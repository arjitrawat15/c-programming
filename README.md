#include<bits/stdc++.h>
using namespace std;

class ElectricityBill {
public:
    string name;
    int units;
    double charges;

    void setData(string userName, int userUnits) {
        name = userName;
        units = userUnits;
        calculateCharges();
    }
    void calculateCharges() {
        charges = 0;

        if (units <= 100) {
            charges = units * 0.60;
        } else if (units <= 300) {
            charges = (100 * 0.60) + (units - 100) * 0.80;
        } else {
            charges = (100 * 0.60) + (200 * 0.80) + (units - 300) * 0.90;
        }
        if (charges < 50) {
            charges = 50;
        }

        if (charges > 300) {
            charges += charges * 0.15;
        }
    }

    void displayBill() {
        cout << fixed << setprecision(2); 
        cout << "The total charges for " << name << " are: Rs " << charges << endl;
    }
};

int main() {
    int numUsers;
    cout << "Enter the number of users: ";
    cin >> numUsers;

    ElectricityBill users[numUsers];

    string name;
    int units;

for (int i = 0; i < numUsers; ++i) {
        cout << "Enter the name of user " << i + 1 << ": ";
        cin >> ws;
        getline(cin, name);
        cout << "Enter the number of units consumed by " << name << ": ";
        cin >> units;
        users[i].name = name;
        users[i].units = units;
    
        users[i].charges = 0;

        if (users[i].units <= 100) {
            users[i].charges = users[i].units * 0.60;
        } else if (users[i].units <= 300) {
            users[i].charges = (100 * 0.60) + (users[i].units - 100) * 0.80;
        } else {
            users[i].charges = (100 * 0.60) + (200 * 0.80) + (users[i].units - 300) * 0.90;
        }

        
        if (users[i].charges < 50) {
            users[i].charges = 50;
        }

        if (users[i].charges > 300) {
            users[i].charges += users[i].charges * 0.15;
        }
    }
 cout << endl << "Electricity Bills:" << endl;
    for (int i = 0; i < numUsers; ++i) {
        cout << fixed << setprecision(2); 
        cout << "The total charges for " << users[i].name << " are: Rs " << users[i].charges << endl;
    }
