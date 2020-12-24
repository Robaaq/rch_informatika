#Вариант 8, методичка 2, задание 9
#include <iostream>
#include <fstream>
#include <fstream> 
#include <locale>
using namespace std;
struct person
{
    char n[15];
    char f[15];
    char o[15];
    char a[15];
    int t;
    int k;
};

int main()
{
    setlocale(LC_ALL, "Russian");
    person *mas;
    fstream f("f.dat", ios::out);
    int n, i, k1;
    cout << "Введите кол-во покупателей n = ";
    cin >> n;
    mas = new person[n];
    for (i = 0; i < n; i++)
    {
        cout << "Введите имя, фамилия, отчество, адрес, номер телефона, номер кредитной карточки" << "\n";
        cin >> mas[i].n;
        cin >> mas[i].f;
        cin >> mas[i].o;
        cin >> mas[i].a;
        cin >> mas[i].t;
        cin >> mas[i].k;
    }
    for (i = 0; i < n; i++)
    {
        f << mas[i].n; f << "\n";
        f << mas[i].f; f << "\n";
        f << mas[i].o; f << "\n";
        f << mas[i].a; f << "\n";
        f << mas[i].t; f << "\n";
        f << mas[i].k; f << "\n";
    }
    f.close();
    person p;
    f.open("f.dat", ios::in);
    do
    {
        f >> p.n;
        f >> p.f;   
        f >> p.o;
        f >> p.a;
        f >> p.t;
        f >> p.k;
        if (f.eof())
        {
            break;
        }
        setlocale(LC_ALL, "russian_russia.866");
        cout << p.n << " " << p.f << " " << p.o << " " << p.a << " " << p.t << " " << p.k << "\n";
    } 
    while (!f.eof());
    f.close();
    delete[] mas;
    return 0;
}
