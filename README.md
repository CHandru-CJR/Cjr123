
Yes. I’ll keep them as simple as possible, while still demonstrating the exact C++ concept required for each set. I’ll also keep the output format close to the question bank.

> Tip for your mid-sem: Don’t just memorize the code. For each one, understand what the variables, if, function, class, constructor, inheritance, and virtual are doing. You may be asked to explain it.




---

SET 1 — MOBILE DATA BILL

Concept: Basic input, arithmetic, conditions

#include <iostream>
#include <iomanip>
using namespace std;

int main()
{
    double data, bill = 0, surcharge = 0, finalBill;

    cin >> data;

    if (data <= 2)
        bill = data * 100;
    else if (data <= 5)
        bill = 2 * 100 + (data - 2) * 75;
    else
        bill = 2 * 100 + 3 * 75 + (data - 5) * 50;

    if (bill > 500)
        surcharge = bill * 0.05;

    finalBill = bill + surcharge;

    cout << "Data Used: " << data << " GB" << endl;
    cout << "Base Bill: ₹" << bill << endl;
    cout << "Surcharge: ₹" << surcharge << endl;
    cout << "Final Bill: ₹" << finalBill << endl;

    return 0;
}

Sample input

6

Output

Data Used: 6 GB
Base Bill: ₹525
Surcharge: ₹26.25
Final Bill: ₹551.25


---

SET 2 — ATM WITHDRAWAL

Concept: Conditions, arithmetic, loops

The easiest way to get the minimum number of notes is to take the biggest notes first.

#include <iostream>
using namespace std;

int main()
{
    int amount;
    int notes500, notes200, notes100;

    cin >> amount;

    if (amount > 20000)
    {
        cout << "Withdrawal Limit Exceeded";
        return 0;
    }

    notes500 = amount / 500;
    amount = amount % 500;

    notes200 = amount / 200;
    amount = amount % 200;

    notes100 = amount / 100;

    cout << "₹500 notes: " << notes500 << endl;
    cout << "₹200 notes: " << notes200 << endl;
    cout << "₹100 notes: " << notes100 << endl;
    cout << "Total Notes: "
         << notes500 + notes200 + notes100 << endl;

    return 0;
}

Input

7800

Output

₹500 notes: 15
₹200 notes: 1
₹100 notes: 1
Total Notes: 17


---

SET 3 — STUDENT RESULT ANALYSER

Concept: Functions and conditions

#include <iostream>
#include <iomanip>
using namespace std;

char calculateGrade(float average)
{
    if (average >= 90)
        return 'A';
    else if (average >= 80)
        return 'B';
    else if (average >= 70)
        return 'C';
    else if (average >= 60)
        return 'D';
    else if (average >= 50)
        return 'E';
    else
        return 'F';
}

int main()
{
    float marks[5];
    float sum = 0, average;
    bool pass = true;

    for (int i = 0; i < 5; i++)
    {
        cin >> marks[i];
        sum = sum + marks[i];

        if (marks[i] < 40)
            pass = false;
    }

    average = sum / 5;

    cout << fixed << setprecision(2);
    cout << "Average: " << average << endl;
    cout << "Grade: " << calculateGrade(average) << endl;

    if (pass)
        cout << "Result: PASS";
    else
        cout << "Result: FAIL";

    return 0;
}

Input

78 82 91 69 85

Output

Average: 81.00
Grade: B
Result: PASS

Remember

The important part here is:

char calculateGrade(float average)

That's the function the question specifically asks you to create.


---

SET 4 — LIBRARY BOOK MANAGEMENT

Concept: Classes and objects

#include <iostream>
using namespace std;

class Book
{
public:
    int id;
    string title;
    string author;
    float price;

    void displayDetails()
    {
        cout << "ID: " << id << endl;
        cout << "Title: " << title << endl;
        cout << "Author: " << author << endl;
        cout << "Price: ₹" << price << endl;
    }
};

int main()
{
    Book b1, b2;

    cin >> b1.id;
    cin.ignore();
    getline(cin, b1.title);
    getline(cin, b1.author);
    cin >> b1.price;

    cin >> b2.id;
    cin.ignore();
    getline(cin, b2.title);
    getline(cin, b2.author);
    cin >> b2.price;

    cout << "Book 1" << endl;
    b1.displayDetails();

    cout << endl;

    cout << "Book 2" << endl;
    b2.displayDetails();

    cout << endl;

    if (b1.price > b2.price)
        cout << "More Expensive Book: " << b1.title;
    else
        cout << "More Expensive Book: " << b2.title;

    return 0;
}

Input

101
The Alchemist
Paulo Coelho
399
102
Clean Code
Robert Martin
650

Output

Book 1
ID: 101
Title: The Alchemist
Author: Paulo Coelho
Price: ₹399

Book 2
ID: 102
Title: Clean Code
Author: Robert Martin
Price: ₹650

More Expensive Book: Clean Code


---

SET 5 — BANK ACCOUNT

Concept: Classes, objects and constructors

#include <iostream>
using namespace std;

class BankAccount
{
public:
    string name;
    int accountNumber;
    float balance;

    BankAccount(string n, int a, float b)
    {
        name = n;
        accountNumber = a;
        balance = b;
    }

    void deposit(float amount)
    {
        balance = balance + amount;
    }

    void withdraw(float amount)
    {
        if (amount <= balance)
        {
            balance = balance - amount;
            cout << "Withdrawal: ₹" << amount << endl;
            cout << "Remaining Balance: ₹" << balance << endl;
        }
        else
        {
            cout << "Insufficient Balance" << endl;
            cout << "Current Balance: ₹" << balance << endl;
        }
    }

    void displayBalance()
    {
        cout << "Account Holder: " << name << endl;
        cout << "Account Number: " << accountNumber << endl;
        cout << "Initial Balance: ₹" << balance << endl;
    }
};

int main()
{
    string name;
    int accountNumber;
    float balance, withdrawal;

    cin >> name;
    cin >> accountNumber;
    cin >> balance;
    cin >> withdrawal;

    BankAccount account(name, accountNumber, balance);

    account.displayBalance();
    cout << endl;

    account.withdraw(withdrawal);

    return 0;
}

Input

Arun
102345
25000
5000

Output

Account Holder: Arun
Account Number: 102345
Initial Balance: ₹25000

Withdrawal: ₹5000
Remaining Balance: ₹20000

For:

Arun
102345
25000
30000

Output:

Account Holder: Arun
Account Number: 102345
Initial Balance: ₹25000

Insufficient Balance
Current Balance: ₹25000


---

SET 6 — WEEKLY FITNESS TRACKER

Concept: Arrays and functions

#include <iostream>
#include <iomanip>
using namespace std;

int totalSteps(int steps[])
{
    int total = 0;

    for (int i = 0; i < 7; i++)
        total = total + steps[i];

    return total;
}

int highestDay(int steps[])
{
    int highest = 0;

    for (int i = 1; i < 7; i++)
    {
        if (steps[i] > steps[highest])
            highest = i;
    }

    return highest;
}

int main()
{
    int steps[7];
    string days[7] =
    {
        "Monday", "Tuesday", "Wednesday",
        "Thursday", "Friday", "Saturday", "Sunday"
    };

    for (int i = 0; i < 7; i++)
        cin >> steps[i];

    for (int i = 0; i < 7; i++)
        cout << days[i] << ": " << steps[i] << endl;

    int total = totalSteps(steps);
    int highest = highestDay(steps);

    cout << endl;
    cout << "Total Steps: " << total << endl;

    cout << fixed << setprecision(2);
    cout << "Average Steps: " << (float)total / 7 << endl;

    cout << "Most Active Day: " << days[highest];

    return 0;
}

Input

6500 7200 8100 5500 9200 7800 6000

Output

Monday: 6500
Tuesday: 7200
Wednesday: 8100
Thursday: 5500
Friday: 9200
Saturday: 7800
Sunday: 6000

Total Steps: 50300
Average Steps: 7185.71
Most Active Day: Friday


---

SET 7 — ONLINE SHOPPING DISCOUNT

Concept: Function overloading

This one is important because both functions have the same name.

#include <iostream>
using namespace std;

double calculateDiscount(double price)
{
    return price * 0.10;
}

double calculateDiscount(double price, double percentage)
{
    return price * percentage / 100;
}

int main()
{
    double price, percentage;

    cin >> price;

    if (cin.peek() == '\n')
    {
        double discount = calculateDiscount(price);

        cout << "Original Price: ₹" << price << endl;
        cout << "Discount: ₹" << discount << endl;
        cout << "Final Price: ₹" << price - discount << endl;
    }
    else
    {
        cin >> percentage;

        double discount = calculateDiscount(price, percentage);

        cout << "Original Price: ₹" << price << endl;
        cout << "Discount: ₹" << discount << endl;
        cout << "Final Price: ₹" << price - discount << endl;
    }

    return 0;
}

However, for an exam, I recommend a simpler version where you directly know which input is being given.

Default 10% version

#include <iostream>
using namespace std;

double calculateDiscount(double price)
{
    return price * 0.10;
}

int main()
{
    double price;
    cin >> price;

    double discount = calculateDiscount(price);

    cout << "Original Price: ₹" << price << endl;
    cout << "Discount: ₹" << discount << endl;
    cout << "Final Price: ₹" << price - discount << endl;

    return 0;
}

Custom discount version

#include <iostream>
using namespace std;

double calculateDiscount(double price)
{
    return price * 0.10;
}

double calculateDiscount(double price, double percentage)
{
    return price * percentage / 100;
}

int main()
{
    double price, percentage;
    cin >> price >> percentage;

    double discount = calculateDiscount(price, percentage);

    cout << "Original Price: ₹" << price << endl;
    cout << "Discount: ₹" << discount << endl;
    cout << "Final Price: ₹" << price - discount << endl;

    return 0;
}

Input

2000 15

Output

Original Price: ₹2000
Discount: ₹300
Final Price: ₹1700

For your exam, this second approach is much easier to explain.


---

SET 8 — VEHICLE RENTAL SYSTEM

Concept: Inheritance

#include <iostream>
using namespace std;

class Vehicle
{
public:
    string vehicleNumber;
    float rate;

    void displayVehicle()
    {
        cout << "Vehicle Number: " << vehicleNumber << endl;
        cout << "Daily Rate: ₹" << rate << endl;
    }
};

class Car : public Vehicle
{
public:
    int seats;

    void displayCar()
    {
        cout << "Vehicle Number: " << vehicleNumber << endl;
        cout << "Vehicle Type: Car" << endl;
        cout << "Number of Seats: " << seats << endl;
        cout << "Daily Rate: ₹" << rate << endl;
    }
};

int main()
{
    Car car;
    int days;

    cin >> car.vehicleNumber;
    cin >> car.rate;
    cin >> car.seats;
    cin >> days;

    car.displayCar();

    cout << "Rental Days: " << days << endl;
    cout << "Total Rental Cost: ₹" << car.rate * days;

    return 0;
}

Input

TN45AB1234
2500
5
3

Output

Vehicle Number: TN45AB1234
Vehicle Type: Car
Number of Seats: 5
Daily Rate: ₹2500
Rental Days: 3
Total Rental Cost: ₹7500

Main thing to remember

class Car : public Vehicle

means Car inherits Vehicle.


---

SET 9 — PAYMENT METHODS

Concept: Runtime polymorphism

This is one of the most important OOP questions.

#include <iostream>
using namespace std;

class Payment
{
public:
    virtual void makePayment()
    {
        cout << "Payment";
    }
};

class CreditCard : public Payment
{
public:
    void makePayment()
    {
        cout << "Credit Card Payment" << endl;
        cout << "Payment processed successfully." << endl;
    }
};

class UPI : public Payment
{
public:
    void makePayment()
    {
        cout << "UPI Payment" << endl;
        cout << "UPI payment processed successfully." << endl;
    }
};

class Cash : public Payment
{
public:
    void makePayment()
    {
        cout << "Cash Payment" << endl;
        cout << "Cash payment received successfully." << endl;
    }
};

int main()
{
    Payment *p;

    CreditCard card;
    UPI upi;
    Cash cash;

    p = &card;
    p->makePayment();

    cout << endl;

    p = &upi;
    p->makePayment();

    cout << endl;

    p = &cash;
    p->makePayment();

    return 0;
}

Output

Credit Card Payment
Payment processed successfully.

UPI Payment
UPI payment processed successfully.

Cash Payment
Cash payment received successfully.

⭐ Most important line

Payment *p;

This is a base-class pointer.

Then:

p = &card;
p->makePayment();

calls the Credit Card version.

Then:

p = &upi;
p->makePayment();

calls the UPI version.

That's runtime polymorphism.


---

SET 10 — EMPLOYEE PAYROLL

Concept: Constructors + inheritance + runtime polymorphism

#include <iostream>
using namespace std;

class Employee
{
public:
    string name;
    int id;
    float salary;

    Employee(string n, int i, float s)
    {
        name = n;
        id = i;
        salary = s;
    }

    virtual void calculateSalary()
    {
        cout << "Employee: " << name << endl;
        cout << "ID: " << id << endl;
    }
};

class Manager : public Employee
{
public:
    Manager(string n, int i, float s)
        : Employee(n, i, s)
    {
    }

    void calculateSalary()
    {
        cout << "Employee: " << name << endl;
        cout << "ID: " << id << endl;
        cout << "Type: Manager" << endl;
        cout << "Basic Salary: ₹" << salary << endl;
        cout << "Final Salary: ₹" << salary * 1.20 << endl;
    }
};

class Developer : public Employee
{
public:
    Developer(string n, int i, float s)
        : Employee(n, i, s)
    {
    }

    void calculateSalary()
    {
        cout << "Employee: " << name << endl;
        cout << "ID: " << id << endl;
        cout << "Type: Developer" << endl;
        cout << "Basic Salary: ₹" << salary << endl;
        cout << "Final Salary: ₹" << salary * 1.10 << endl;
    }
};

int main()
{
    Manager manager("Anita", 101, 50000);
    Developer developer("Ravi", 102, 45000);

    Employee *e;

    e = &manager;
    e->calculateSalary();

    cout << endl;

    e = &developer;
    e->calculateSalary();

    return 0;
}

Output

Employee: Anita
ID: 101
Type: Manager
Basic Salary: ₹50000
Final Salary: ₹60000

Employee: Ravi
ID: 102
Type: Developer
Basic Salary: ₹45000
Final Salary: ₹49500


---

🧠 What you actually need to remember

If you get any one of these 10, identify the concept first:

Set	Question	Main thing to remember

1	Mobile Bill	if / else if / else
2	ATM	/ and %
3	Student Result	Function
4	Library	Class + Object
5	Bank	Constructor + class
6	Fitness	Array + functions
7	Discount	Function overloading
8	Vehicle	Inheritance
9	Payment	virtual + base pointer
10	Payroll	Constructor + inheritance + polymorphism


The OOP progression is especially easy to remember:

Set 4

Class → Object

Set 5

Class → Object → Constructor

Set 8

Base Class → Derived Class

Set 9

Base Class → Derived Classes → virtual → Base Pointer

Set 10

Constructor + Inheritance + virtual + Base Pointer

So if you understand Sets 4 → 5 → 8 → 9 → 10, you're essentially building OOP step-by-step rather than memorizing five unrelated programs.
