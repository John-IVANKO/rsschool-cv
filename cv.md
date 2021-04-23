# **Curriculum Vitae**


Personal Data: |
------------|  
  Name    Ivan| 
  Surname     Mokhovikov | 
  Tel. +375445395242 | 
  Telegram:  john_ivanko | 
  e-mail:  iimohovikov@gmail.com | 



## About me

#### I'm first year student of the BSUIR. Initially, I want get new skills&experience from this course. 
#### What can I tell u about myself??? Hmmm, I'm a friendly person, who always come to help, nevermind U are my friend or stranger. I love codin', I often lost in time, when do labworks in university, because I I want to know something new.

## **My skills**

#### I know the basics of 3 programming languages: _C, JavaScript and Python_. Most of all I have coded in C, below are my best works, in my opinion:

### **P.S.** All works adapted by Russian. because they are made for teacher in university

`/*1.	Структура «Вокзал»: номер поезда, пункт назначения,
дни следования, время прибытия, время стоянки.*/




#pragma warning(disable : 4996)
#include <iostream>
#include <stdio.h>
#include <string.h>
#include <windows.h>
using namespace std;

struct vokzal
{
	int num;
	char punct[30];
	char days[30];
	float come_time;
	float stay_time;
};

struct vokzal train[10];//обявляем глобальный массив

int u=0, counter = 0;// счетчик записей
int er;//переключатель
FILE* F1;
void print();
int menu();
void find();
void formir();
void vvod();


int main()
{

	setlocale(LC_ALL, "Russian");  
	      
	while (1)
	{
		switch (menu())
		{
		case 1:
			formir();
			break;
		case 2: vvod();
			break;
		case 3: print();
			break;
		case 4: find();
			break;
		case 5:
			
			return 0;
		default: cout << "Неверный выбор\n";
			
		}

	}
	return 0;
}
int menu()
{
	int menuChoice;
	cout << "Введите: \n";
	cout << "1-для формирования файла \n";
	cout << "2-для ввода данных о поезде-\n";
	cout << "3-для печати данных о поезде в файл \n";
	cout << "4-для поиска данных о поезде \n";
	cout << "5-для выхода \n";
	cin >> menuChoice;
	return menuChoice;
}

		void formir()
		{
			u++;
			if (!(F1 = fopen("VOKZAL.dat", "wb")))
			{
				printf("Ошибка создания файла\n");
			}
			else
				printf("Файл успешно создан\n");
		}
		void print()
		{

			if (u == 0)
				cout << "Создайте файл\n";
			else
			{
				if (counter == 0)
					cout << "\n Записей нет\n";
				else
				{
					F1 = fopen("VOKZAL.dat", "a");
					for (int i = 0; i < counter; i++)
					{
						fprintf(F1, "%d-ый поезд Номер поезда %d %s %s %f %f", i + 1, train[i].num, train[i].punct, train[i].days, train[i].come_time, train[i].stay_time);

					}
					cout << "Данные введены\n";
					fclose(F1);
				}
			}
		}
		void vvod()
		{
			if (u == 0)
				cout << "Создайте файл\n";
			else
			{
				if (counter < 10)// вводим новую запись пока не введено 10
				{
					F1 = fopen("VOKZAL.dat", "wb");
					cout << counter + 1 << "-ый поезд: \n";
					cout << "Введите номер поезда: \n";
					cin >> train[counter].num;
					cout << "Введите пункт назначения(ENGLISH): \n";
					cin >> train[counter].punct;
					cout << "Введите дни следования(например,\"mon-tue-wed-...\"): \n";
					cin >> train[counter].days;
					cout << "Введите время прибытия: \n";
					cin >> train[counter].come_time; ;
					cout << "Введите время стоянки: \n";
					cin >> train[counter].stay_time;
					counter++;
					fclose(F1);
				}
				else cout << "Введено максимальное количество поездов(10)\n";
			}
		}
		




void find()
{
	int sw, n;
	char punct1[30], * p;
	if (counter == 0)
		cout << "\nНет поездов\n";
	else
	{
		cout << "\nВведите:\n";
		cout << "\n1-для поиска по номеру\n";
		cout << "\n2-для поиска поезда по пункту назначения\n";
		cout << "\n3-для выхода\n";
		cin >> sw;
		switch (sw)
		{
		case 1:
			int i;
			cout << "Введите номер поезда";
			cin >> n;
			for (i = 0; i < counter; i++)
			{
				if (train[i].num == n)

				{
					cout << "Номер поезда:" << train[i].num << endl;
					cout << "Пункт назначения:" << train[i].punct << endl;
					cout << "Дни следования:" << train[i].days << endl;
					cout << "Время прибытия:" << train[i].come_time << endl;
					cout << "Время стоянки:" << train[i].stay_time << endl;
					cout << "_______________" << endl;
				}
				else cout << "Нет подходящих поездов" << endl;
			}
			break;
		case 2:

			cout << "Введите пункт назначения:";
			cin >> punct1;
			for (i = 0; i < counter; i++)//в цикле просматриваем все структуры из массива структур
			{
				p = strstr(train[i].punct, punct1);//strstr указатель на строку с пунктом назначения
				if (p)
				{
					cout << "Номер поезда:" << train[i].num << endl;
					cout << "Пункт назначения:" << train[i].punct << endl;
					cout << "Дни следования:" << train[i].days << endl;
					cout << "Время прибытия:" << train[i].come_time << endl;
					cout << "Время стоянки:" << train[i].stay_time << endl;
					cout << "_______________" << endl;
				}
				else cout << "Нет подходящих поездов" << endl;
			}
			break;
		case 3: return;
		}
	}
}



/*
Создать двунаправленный список с числами в диапазоне от –50 до + 50.
После создания списка выполнить индивидуальное задание и вывести результат.
Написать программу сортировки и поиска в двунаправленном списке.
Отсортировать список и вывести его на экран.
Найти элемент списка, равный номеру варианта, и вывести его порядковый номер либо сообщение о том, что такого элемента нет :
Удалить первый и последний элементы списка
*/

#include <iostream>
#include <stdio.h>
#include <conio.h>
struct Spis { // Описание структуры
	int info;
	Spis* Previous, * Next;
} *Head, * end;
void View(void);
void Sort(void);
void Del_Spis(void);
void main(void) {
	Spis* t, * key;
	int i, k;
	while (1) {
		printf("\n 1. Creat Doubly Linked List\n 2. View Doubly Linked List\n 3. Find elements in Doubly Linked List \n 4. Delete element in Doubly Linked List\n 5. Add elements in Doubly Linked List\n 6. Sort Doubly Linked list\n\n 0. EXIT\n"); 
			
			switch (_getch()) {
				//============== Формирование первого элемента ===============
			case '1': i = 0;
				t = new Spis;
				printf(" Input info 1 : "); scanf_s("%d", &t->info);
				t->Next = t->Previous = NULL;
				Head = end = t;
				//========== Формирование списка со второго ===================
				while (2) {
					t = new Spis;
					printf(" Input info : "); scanf_s("%d", &t->info);
					t->Next = NULL;
					t->Previous = end;
					end->Next = t;
					end = t;
					printf("\n Repeat - y ");
					if (_getch() != 'y') break; // Продолжение - 'y', иначе - выход
				}
				break;
				//=================== Просмотр списка ======================
			case '2': View(); break;
				//================== Поиск элемента ========================
			case '3': t = Head;
				printf("\n Find Info : "); scanf_s("%d", &i);
				k = 1;
				while (t != NULL) {
					if (t->info == i) {
						printf("\n Element = %d - number = %d", t->info, k);
						_getch(); break;
					}
					t = t->Next;
					k++;
				}
				if (t == NULL) {
					puts("\n Not Found !");
					_getch();
				}
				break;
				//======== Поиск элемента для удаления =======================
			case '4': t = Head;
				key = NULL;
				k = 1;
				printf("\n Delete Info : "); scanf_s("%d", &i);
				while (t != NULL) {
					
						if (t->info == i) {
							printf("\n Delete element = %d - number = %d", t->info, k);
							_getch();
							key = t; // Запомнили адрес удаляемого элемента
							break;
						}
					t = t->Next;
					k++;
				}
				if (key == NULL) {
					puts("\n NO Element !");
					_getch();
					break;
				}
				//================= Удаляем найденный =====================
				if (key == Head) {
					Head = Head->Next;
					Head->Previous = NULL;
				}
				else if (key == end) {
					end = end->Previous;
					end->Next = NULL;
				}
				else {
					(key->Previous)->Next = key->Next;
					(key->Next)->Previous = key->Previous;
				}
				delete key;
				break;
				//======== Вставка элемента по порядковому номеру (после) ========
			case '5': t = Head;
				printf("\n Ins Nom : "); scanf_s("%d", &k);
				for (i = 1; i < k; i++)
					if (t != NULL) t = t->Next;
				key = t;
				if (key == NULL) {
					printf("\n NO element ");
					_getch(); break;
				}
				t = new Spis;
				printf("\n Input info "); scanf_s("%d", &t->info);
				t->Previous = key;
				t->Next = key->Next;
				key->Next = t;
				if (key != end) (t->Next)->Previous = t;
				else end = t;
				break;
			case '6': Sort(); break;
			case '0': Del_Spis(); return;
			} 
	} 
}
//=================== Просмотр списка c начала ===============
void View() {
	int k = 1;
	Spis* t = Head;
	if (t == NULL) {
		printf("\n NO elements !"); return;
	}
	while (t != NULL) {
		printf("\n %d element - %d", k, t->info);
		t = t->Next;
		k++;
	}
}
//=================== Освобождение памяти =================
void Del_Spis(void) {
	Spis* t = Head;
	while (t != NULL) {
		Head = Head->Next;
		delete t;
		t = Head;
	}
	puts(" Delete!");
}
void Sort() {
	Spis* t = Head, * t1 = new Spis;
	printf("\n Input info ");
	scanf_s("%d", &t1->info); // Добавляем новый элемент
	while (t != NULL) {
		if (t1->info < t->info) { // Поставить перед текущим
			t1->Next = t;
			if (t == Head) { // В начало списка
				t1->Previous = NULL;
				Head = t1;
			}
			else { // В середину списка
				
					(t->Previous)->Next = t1;
				t1->Previous = t->Previous;
			}
			t->Previous = t1;
			puts("\n Insert! "); // Выводим сообщение
			return;
		}
		t = t->Next;
	}
	t1->Next = NULL; // В конец списка
	t1->Previous = end;
	end->Next = t1;
	end = t1;
	puts("\n Insert End! "); // Сообщение - вставили в конец
	return;
}


/*Создать стек с числами в диапазоне от –50 до +50.
После создания стека выполнить индивидуальное задание:
Определить, сколько элементов стека, начиная от вершины,
находится до элемента с минимальным значением.*/
#include <stdio.h>
#include <stdlib.h>
#include <locale>
#define NMAX 100
using namespace std;


struct Stack {
  int elem[NMAX];
  int top;
};



void init(struct Stack* stk) {
  stk->top = 0;
}

void push(struct Stack* stk, int f) {
  if (stk->top < NMAX) {
    stk->elem[stk->top] = f;
    stk->top++;
  }
  else
    printf("Стек полон, количество элементов: %d !\n", stk->top);
}


int pop(struct Stack* stk) {
  int elem;
  if ((stk->top) > 0)
  {
    stk->top--;
    elem = stk->elem[stk->top];
    return elem;
  }
  else
  {
    printf("Стек пуст!\n");
    return 0;
  }
}


int stkTop(struct Stack* stk) {
  if ((stk->top) > 0) {
    return stk->elem[stk->top - 1];
  }
  else {
    printf("Стек пуст!\n");
    return 0;
  }
}


int getcount(struct Stack* stk) {
  return stk->top;
}


int isempty(struct Stack* stk) {
  if (stk->top == 0)    return 1;
  else return 0;
}


void stkPrint(struct Stack* stk) {
  int i;
  i = stk->top; // i - количество элементов в стеке
  if (isempty(stk) == 1) return; // стек пуст
  do {
    i--;
    printf("%d\n", stk->elem[i]);
  } while (i > 0);
}





int main() {
  setlocale(LC_ALL, "ru");
  struct Stack* stk;
  int i, n;
  int elem;
  stk = (struct Stack*)malloc(sizeof(struct Stack));
  init(stk);
  printf("Введите количество элементов в стеке: ");
  scanf_s("%d", &n);
  for (i = 0; i < n; i++) {

    printf("Введите элемент %d:", i);
    scanf_s("%d", &elem);
    push(stk, elem);

  }
  int result = 0;
  int currentMin = 50;
  for (i = 0; i < n; ++i)
  {
    if (stk->elem[i] < currentMin)
    {
      currentMin = stk->elem[i];
      result = i;
    }
    
  }
  printf("\nЭлементов стека, начиная от вершины, находится до элемента с минимальным значением: %d\n", result);
  printf("\nВ стеке %d элементов\n\n", getcount(stk));
  stkPrint(stk);
  
  return 0;

}`

