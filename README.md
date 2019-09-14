# oop_lab1
#include "pch.h"
#include <iostream>
#define size 30  
#define str_len 50
int choice;
using namespace std;
struct Bank
{
	char name[str_len];
	char type_of_ba[20];
	int number_of_ba;
	int sum;
	int date;
};

struct Bank list_of_clients[size];
int current_size = 0;

void enter_new()
{
	cout << "Ввод информации" << endl;
	if (current_size < size)
	{
		cout << "Номер клиента ";
		cout << current_size + 1;
		cout << endl << "Фамилия " << endl;
		cin >> list_of_clients[current_size].name;
		cout << "Тип счёта " << endl;
		cin >> list_of_clients[current_size].type_of_ba;
		cout << "Номер счёта " << endl;
		cin >> list_of_clients[current_size].number_of_ba;
		cout << "Сумма на счету " << endl;
		cin >> list_of_clients[current_size].sum;
		cout << "Дата изменения " << endl;
		cin >> list_of_clients[current_size].date;
		current_size++;
	}
	else
		cout << "Введено максимальное кол-во строк";
	cout << "Что дальше?" << endl;
	cin >> choice;
}
void change()
{
	int n, per;
	cout << "\nВведите номер строки" << endl; 	cin >> n;
	do
	{
		cout << "Введите: " << endl;
		cout << "1-для изменения Фамилии" << endl;
		cout << "2-для изменения типа счёта" << endl;
		cout << "3-для изменения номера счёта" << endl;
		cout << "4-для изменения суммы на счету" << endl;
		cout << "5-конец\n";
		cin >> per;
		switch (per)
		{
		case 1: cout << "Новая Фамилия";
			cin >> list_of_clients[n - 1].name;   break;
		case 2: cout << "Новый тип счёта";
			cin >> list_of_clients[n - 1].type_of_ba; break;
		case 3: cout << "Новый номер счёта ";
			cin >> list_of_clients[n - 1].number_of_ba; break;
		case 4: cout << "Новая сумма на счету ";
			cin >> list_of_clients[n - 1].sum; break;
		}
	} while (per != 5);
	cout << "Что дальше?" << endl;
	cin >> choice;
}
void out()
{
	int sw, n;
	cout << "1-вывод 1 строки" << endl;
	cout << "2-вывод всех строк" << endl;
	cin >> sw;
	if (sw == 1)
	{
		cout << "Номер выводимой строки " << endl;   cin >> n;  cout << endl;
		cout << "ФИО ";
		cout << list_of_clients[n - 1].name << endl;
		cout << "Тип счёта ";
		cout << list_of_clients[n - 1].type_of_ba << endl;
		cout << "Номер счёта ";
		cout << list_of_clients[n - 1].number_of_ba << endl;
		cout << "Сумма счёта ";
		cout << list_of_clients[n - 1].sum << endl;
		cout << "Последняя дата изменения ";
		cout << list_of_clients[n - 1].date << endl;
	}
	if (sw == 2)
	{
		for (int i = 0; i < current_size; i++)
		{
			cout << "Фамилию ";
			cout << list_of_clients[i].name << endl;
			cout << "Тип счёта ";
			cout << list_of_clients[i].type_of_ba << endl;
			cout << "Номер счёта ";
			cout << list_of_clients[i].number_of_ba << endl;
			cout << "Сумма счёта ";
			cout << list_of_clients[i].sum << endl;
			cout << "Последняя дата изменения ";
			cout << list_of_clients[i].date << endl;
		}
	}
	cout << "Что дальше?" << endl;
	cin >> choice;
}
void search() {
	int d;
	cout << "Выберите следующее: " << endl;
	cout << "1 - Для поиска имени" << endl;
	cout << "2 - Для поиска по сумме" << endl;
	cout << "3 - Для выхода" << endl;
	cin >> d;
	do{
	switch (d) {
	case 1: {
		char n[str_len];
		cout << "Vved im" << endl;
		cin >> n;
		for (int i = 0; i < size; i++)
		{
			if (strcmp(list_of_clients[i].name, n) == 0) {
				cout << "Результаты поиска: " << n << endl;
				cout << "Тип счёта ";
				cout << list_of_clients[i].type_of_ba << endl;
				cout << "Номер счёта ";
				cout << list_of_clients[i].number_of_ba << endl;
				cout << "Сумма счёта ";
				cout << list_of_clients[i].sum << endl;
				cout << "Последняя дата изменения ";
				cout << list_of_clients[i].date << endl;
				

			}
			if (strcmp(list_of_clients[i].name, n) == 1) {
				cout << "Нету";
				

			}

		}
		d = 3;

	}break;
	case 2: {
		int summa;
		cout << "Vved sum" << endl;
		cin >> summa;
		for (int i = 0; i < size; i++)
		{
			if (list_of_clients[i].sum >= summa && summa >= 100) {
				cout << "Фамилию ";
				cout << list_of_clients[i].name << endl;
				cout << "Тип счёта ";
				cout << list_of_clients[i].type_of_ba << endl;
				cout << "Номер счёта ";
				cout << list_of_clients[i].number_of_ba << endl;
				cout << "Сумма счёта ";
				cout << list_of_clients[i].sum << endl;
				cout << "Последняя дата изменения ";
				cout << list_of_clients[i].date << endl;

			}
			if (list_of_clients[i].sum < summa&&summa < 100) {
				cout << "Фамилию ";
				cout << list_of_clients[i].name << endl;
				cout << "Тип счёта ";
				cout << list_of_clients[i].type_of_ba << endl;
				cout << "Номер счёта ";
				cout << list_of_clients[i].number_of_ba << endl;
				cout << "Сумма счёта ";
				cout << list_of_clients[i].sum << endl;
				cout << "Последняя дата изменения ";
				cout << list_of_clients[i].date << endl;
			}
		}
		d = 3;
	}break;
	}
	}while (d != 3);
	cout << "Что дальше?" << endl;
	cin >> choice;
}

int main()
{
	setlocale(LC_CTYPE, "Russian");
	cout << "Данных нет" << endl;
	cout << "Введите:" << endl;
	cout << "1-для ввода новой записи" << endl;
	cout << "2-для изменения записи" << endl;
	cout << "3-для вывода записи(ей)" << endl;
	cout << "4-для поиска" << endl;
	cout << "5-для выхода" << endl;
	cin >> choice;
	do
	{
		switch (choice)
		{
		case 1:  enter_new();  break;
		case 2:  change();  break;
		case 3:  out();	break;
		case 4:  search(); break;
		}
	} while (choice != 5);
}
