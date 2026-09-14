#include <iostream>
#include <string>
using namespace std;

class Account
{
private:
    string owner;
    double balance;

public:

    // Constructor
    Account(string name, double initialBalance)
    {
        owner = name;
        balance = initialBalance;
    }

    // Deposit
    void deposit(double amount)
    {
        if (amount > 0)
        {
            balance += amount;
            cout << "Deposited " << amount << " EGP." << endl;
            cout << "New balance: " << balance << " EGP" << endl;
        }
        else
        {
            cout << "Invalid amount!" << endl;
        }
    }

    // Withdraw
    void withdraw(double amount)
    {
        if (amount <= 0)
        {
            cout << "Invalid amount!" << endl;
        }
        else if (amount > balance)
        {
            cout << "Error: insufficient funds." << endl;
            cout << "Current balance: " << balance << " EGP" << endl;
        }
        else
        {
            balance -= amount;
            cout << "Withdrawn " << amount << " EGP." << endl;
            cout << "New balance: " << balance << " EGP" << endl;
        }
    }

    // Check Balance
    void checkBalance()
    {
        cout << "Current balance: " << balance << " EGP" << endl;
    }
};

int main()
{
    Account account("Ahmed", 1000);

    int choice;
    double amount;

    do
    {
        cout << "\n=== Bank System ===" << endl;
        cout << "1. Deposit" << endl;
        cout << "2. Withdraw" << endl;
        cout << "3. Check Balance" << endl;
        cout << "4. Exit" << endl;

        cout << "Choose an option: ";
        cin >> choice;

        switch (choice)
        {
        case 1:
            cout << "Enter amount to deposit: ";
            cin >> amount;
            account.deposit(amount);
            break;

        case 2:
            cout << "Enter amount to withdraw: ";
            cin >> amount;
            account.withdraw(amount);
            break;

        case 3:
            account.checkBalance();
            break;

        case 4:
            cout << "Goodbye!" << endl;
            break;

        default:
            cout << "Invalid choice!" << endl;
        }

    } while (choice != 4);

    return 0;
}
