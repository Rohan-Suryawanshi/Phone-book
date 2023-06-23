#include <stdio.h>
#include <stdlib.h>
#include <windows.h>
struct data
{
	char name_[20];
	char number_[12];
	char x;
} a[10], temp;
void menue();
void clear()
{
	system("cls");
	menue();
}
int compare(char string1[20], char string2[20])
{
	int i;
	for (i = 0; string1[i] && string2[i]; ++i)
	{
		if (string1[i] == string2[i] || (string1[i] ^ 32) == string2[i])
			continue;
		else
			break;
	}
	if (string1[i] == string2[i])
	{
		return 0;
	}
	if ((string1[i] | 32) < (string2[i] | 32))
	{
		return -1;
	}
	return 1;
}

int integer(char number[])
{
	int count = 0;
	for (int i = 0; i < 10; i++)
	{
		if (number[i] >= '0' && number[i] <= '9')
		{
			count++;
		}
	}
	if (count == 10)
	{
		return 1;
	}
	return 0;
}
void colour(char ch)
{
	/*0 = Black
1 = Blue	
2 = Green	
3 = Aqua	
4 = Red	
5 = Purple
6 = Yellow	
7 = White	
 8 = Gray
 9 = Light Blue
 A = Light Green
 B = Light Aqua
 C = Light Red
 D = Light Purple
 E = Light Yellow
F = Bright White*/

	switch (ch)
	{
	case '0':
		system("color 0");
		break;
	case '1':
		system("color 1");
		break;
	case '2':
		system("color 2");
		break;
	case '3':
		system("color 3");
		break;
	case '4':
		system("color 4");
		break;
	case '5':
		system("color 5");
		break;
	case '6':
		system("color 6");
		break;
	case '7':
		system("color 7");
		break;
	case '8':
		system("color 8");
		break;
	case '9':
		system("color 9");
		break;
	case 'A':
		system("color A");
		break;
	case 'B':
		system("color B");
		break;
	case 'C':
		system("color C");
		break;
	case 'D':
		system("color D");
		break;
	case 'E':
		system("color E");
		break;
	case 'F':
		system("color F");
		break;
	}
}
void logo()
{
	colour('6');
	gotoxy(20, 0);
	printf("=============================\n");
	gotoxy(20, 2);
	printf("||");
	gotoxy(30, 2);
	printf("PHONE BOOK");
	gotoxy(47, 2);
	printf("||");
	gotoxy(20, 3);
	printf("=============================\n");
	colour('7');
}
void menue()
{
	logo();
	colour('3');
	gotoxy(20, 5);
	printf("1] Add Contact :\n");
	gotoxy(20, 6);
	printf("2] Edit Contact :\n");
	gotoxy(20, 7);
	printf("3] Delete Contact :\n");
	gotoxy(20, 8);
	printf("4] Search Contact :\n");
	gotoxy(20, 9);
	printf("5] Sort Contact :\n");
	gotoxy(20, 10);
	printf("6] Favorite list :\n");
	gotoxy(20, 11);
	printf("7] Display all Contact :\n");
	gotoxy(20, 12);
	printf("8] Delete Batch Contact :\n");
	gotoxy(20, 13);
	printf("9] Backup Contact :\n");
	gotoxy(20, 14);
	printf("10] About me:\n");
	colour('7');
}
void add_contact()
{
	char name[20];
	char number[12];
	char category;
	FILE *fp;
	colour('4');
	printf("\t\t   Name :");
	fflush(stdin);
	scanf("%s", name);
	printf("\n\t\t   Mobile number :");
start:
	fflush(stdin);
	scanf("%s", &number);
	fp = fopen("contact.txt", "a+");
	if (strlen(number) == 10 && integer(number))
	{
		printf("\n\t\t  You need this friend in Best friends list [y/n]");
		fflush(stdin);
		scanf("%c", &category);
		fprintf(fp, "%s %s %c\n", name, number, category);
		clear();
		colour('5');
		printf("\n\t\t\tContact save :\n\n");
		colour('7');
	}
	else
	{
		printf("\n\t\t   Please enter 10 Digit number :\n");
		printf("\n\t\t   Enter [10 digit] number :");
		goto start;
	}
	fclose(fp);
	colour('7');
}
int name_present(char tempname[])
{
	char name[20];
	FILE *fp;
	fp = fopen("contact.txt", "r");
	if (fp == NULL)
	{
		printf("\n\t\t   No contact Found\n");
		return 0;
	}
	else
	{
		while ((fscanf(fp, "%s %*s %*c", name)) != -1)
		{
			if ((strcmp(tempname, name)) == 0)
			{
				return 1;
			}
		}
	}
	return 0;
	fclose(fp);
}
void edit_name(char tempname[])
{
	FILE *fp, *fp1;
	char name[20];
	char num[12];
	char newname[20];
	char ch;
	int count = 0;
	fp = fopen("contact.txt", "r");
	fp1 = fopen("temp99.txt", "a+");
	colour('B');
	printf("\n\t\tNew Name :");
	scanf("%s", newname);
	if (fp == NULL)
	{
		colour('4');
		printf("\n\t\t   No contact Found\n");
		colour('7');
	}
	else
	{
		colour('D');
		while ((fscanf(fp, "%s %s %c", name, num, &ch)) != -1)
		{
			if ((strcmp(name, tempname)) == 0)
			{
				fprintf(fp1, "%s %s %c \n", newname, num, ch);
				count = 1;
			}
			else
			{
				fprintf(fp1, "%s %s %c\n", name, num, ch);
			}
		}
		if (count == 1)
		{
			printf("\n\t\tChange successful\n");
		}
		colour('7');
	}
	remove("contact.txt");
	rename("temp99.txt", "contact.txt");
	fclose(fp);
	fclose(fp1);
}
void edit_number(char tempname[])
{
	FILE *fp, *fp1;
	char name[20];
	char num[12];
	char ch;
	char newnumber[12];
	int count = 0;
	fp = fopen("contact.txt", "r");
	fp1 = fopen("temp99.txt", "a+");
	colour('B');
	printf("\n\t\tNew Number:");
	scanf("%s", newnumber);
	if (integer(newnumber))
	{
		if (fp == NULL)
		{
			colour('4');
			printf("\nNo contact Found");
			colour('7');
		}
		else
		{
			colour('D');
			while ((fscanf(fp, "%s %s %c", name, num, &ch)) != -1)
			{
				if (((strcmp(name, tempname)) == 0) && integer(newnumber))
				{
					fprintf(fp1, "%s %s %c\n", name, newnumber, ch);
					count = 1;
				}
				else
				{
					fprintf(fp1, "%s %s %c\n", name, num, ch);
				}
			}
			colour('7');
		}
		if (count != 0)
		{
			colour('E');
			printf("\n\t\tChange successful\n");
			colour('7');
		}
		remove("contact.txt");
		rename("temp99.txt", "contact.txt");
		fclose(fp);
		fclose(fp1);
	}
	else
	{
		printf("\t\tEnter the valid number\n");
	}
}
void edit_friend(char tempname[])
{
	FILE *fp, *fp1;
	char name[20];
	char num[12];
	char ch, ch1;
	int count = 0;
	fp = fopen("contact.txt", "r");
	fp1 = fopen("temp99.txt", "a+");
	fflush(stdin);
	colour('B');
	printf("\n\t\tAdd or Remove best friend :");
	scanf("%c", &ch1);
	if (fp == NULL||fp1==NULL)
	{
		colour('4');
		printf("\n\t\t   No contact Found\n");
		colour('7');
	}
	else
	{
		colour('D');
		while ((fscanf(fp, "%s %s %c", name, num, &ch)) != -1)
		{
			if (((strcmp(name, tempname)) == 0))
			{
				fprintf(fp1, "%s %s %c\n", name, num, ch1);
				count = 1;
			}
			else
			{
				fprintf(fp1, "%s %s %c\n", name, num, ch);
			}
		}
		colour('7');
	}
	if (count != 0)
	{
		colour('E');
		printf("\n\t\tChange successful\n");
		colour('7');
	}
	remove("contact.txt");
	rename("temp99.txt", "contact.txt");
	fclose(fp);
	fclose(fp1);
}
void delete_contact()
{
	FILE *fp, *fp1;
	char name[20];
	char num[12];
	char newname[20];
	char ch;
	int count = 0;
	fp = fopen("contact.txt", "r");
	fp1 = fopen("temp99.txt", "a+");
	colour('E');
	printf("\n\t\tDelete Name :");
	scanf("%s", newname);
	colour('7');
	if (fp == NULL)
	{
		colour('4');
		printf("\n\t\t   No contact Found\n");
		colour('7');
	}
	else
	{
		colour('D');
		while ((fscanf(fp, "%s %s %c", name, num, &ch)) != -1)
		{
			if ((strcmp(name, newname)) == 0)
			{
				count = 1;
			}
			else
			{
				fprintf(fp1, "%s %s %c\n", name, num, ch);
			}
		}
		if (count == 1)
		{
			printf("\t\tChange successful\n");
		}
		else
		{
			printf("\t\tContact not found\n");
		}
		colour('7');
	}
	remove("contact.txt");
	rename("temp99.txt", "contact.txt");
	fclose(fp);
	fclose(fp1);
}
void edit()
{
	int choice;
	char tempname[20];
	colour('D');
	printf("\t\tName to search :");
	scanf("%s", tempname);
	if (name_present(tempname) == 1)
	{
		printf("\n\t\tDetails to change :\n");
		printf("\t\t  1] Name :\n");
		printf("\t\t  2] Mobile number :\n");
		printf("\t\t  3] Favorite :\n");
		printf("\t\tEnter choice :");
		scanf("%d", &choice);
		switch (choice)
		{
		case 1:
			clear();
			edit_name(tempname);
			break;
		case 2:
			clear();
			edit_number(tempname);
			break;
		case 3:
			clear();
			edit_friend(tempname);
			break;
		}
	}
	else
	{
		printf("\n\t\tContact not found\n");
	}
}
void display()
{
	char name[20];
	char num[12];
	int i = 1,count=0;
	char ch;
	FILE *fp;
	fp = fopen("contact.txt", "r");
	if (fp == NULL)
	{
		colour('4');
		printf("\n\t\t   No contact Found\n");
		colour('7');
	}
	else
	{
		colour('D');
		printf("\t\t   No\tName\t  Mobile no\n");
		colour('E');
		while ((fscanf(fp, "%s %s %c ", name, num, &ch)) != -1)
		{
			printf("\t\t   %d\t%-10s%s\n", i, name, num);
			count=1;
			i++;
		}
		if(count==0)
		{
			printf("\n\t\t   No contact Found\n");
		}
		colour('7');
	}
	fclose(fp);
}
void display_bestfriend()
{
	char name[20];
	char num[12];
	int i = 1,count=0;
	char ch;
	FILE *fp;
	fp = fopen("contact.txt", "r");
	if (fp == NULL)
	{
		colour('4');
		printf("\nNo contact Found");
		colour('7');
	}
	else
	{
		colour('D');
		printf("\t\t   No\tName\t  Mobile no\n");
		colour('E');
		while ((fscanf(fp, "%s %s %c ", name, num, &ch)) != -1)
		{
			if (ch == 'Y' || ch == 'y')
			{
				printf("\t\t   %d\t%-10s%s\n", i, name, num);
				i++;
				count=1;
			}
		}
		if(count==0)
		{
			printf("\n\t\t   No contact Found\n");
		}
		colour('7');
	}
	fclose(fp);
}
void serch_name(int n)
{
	char tname[20];
	char name[20];
	char num[12];
	char ch;
	char newnumber[12];
	int count = 0;
	FILE *fp;
	fp = fopen("contact.txt", "r");
	switch (n)
	{
	case 1:
		printf("\n\t\t   Enter Name to search :");
		scanf("%s", tname);
		if (fp == NULL)
		{
			colour('4');
			printf("\n\t\t  No contact Found");
			colour('7');
		}
		else
		{
			colour('D');
			printf("\t\t   Name\t     Mobile no\n");
			colour('E');
			while ((fscanf(fp, "%s %s %c ", name, num, &ch)) != -1)
			{
				if (strcmp(tname, name) == 0)
				{
					printf("\t\t   %-10s%s\n", name, num);
					count=1;
				}
			}
				if (count == 0)
			{
				printf("\n\t\t   Contact not found\n");
			}
			colour('7');
		}
		fclose(fp);
		break;
	case 2:

		colour('B');
		printf("\n\t\t   Contact Number:");
		scanf("%s", newnumber);
		if (integer(newnumber))
		{
			if (fp == NULL)
			{
				colour('4');
				printf("\nNo contact Found");
				colour('7');
			}
			else
			{
				colour('D');
				printf("\t\t   Name\t     Mobile no\n");
				while ((fscanf(fp, "%s %s %c", name, num, &ch)) != -1)
				{
					if (((strcmp(newnumber, num)) == 0) && integer(newnumber))
					{
						printf("\t\t   %-10s%s\n", name, num);
						count = 1;
					}
				}
				
			}
			if (count == 0)
			{
				printf("\n\t\t   Contact not found\n");
			}

			fclose(fp);
		}
		else
		{
			printf("\t\tEnter the valid number\n");
		}
		break;
		colour('7');
	}
}
void serch()
{
	int choice;
	colour('8');
	printf("\t\t   Search by\n\t\t   1]Contact name\n\t\t   2]Contact number\n");
	gotoxy(20,18);
	scanf("%d", &choice);
	switch (choice)
	{
	case 1:
		serch_name(1);
		break;
	case 2:
		serch_name(2);
		break;
	}
}
void sort()
{
	char name[20];
	char num[12];
	int i = 0, count=0,n;
	char ch;
	FILE *fp, *fp1;
	fp = fopen("contact.txt", "r");
	if (fp == NULL)
	{
		colour('4');
		printf("\n\t\t   No contact Found\n");
		colour('7');
	}
	else
	{
		while ((fscanf(fp, "%s %s %c ", name, num, &ch)) != -1)
		{
			strcpy(a[i].name_, name);
			strcpy(a[i].number_, num);
			a[i].x = ch;
			i++;
		}
		colour('7');
	}
	n = i;
	fclose(fp);
	for (i = 0; i < n - 1; i++)
	{
		for (int j = i + 1; j < n; j++)
		{
			if (compare(a[i].name_, a[j].name_) > 0)
			{
				temp = a[i];
				a[i] = a[j];
				a[j] = temp;
				count=1;
			}
		}
	}
	fp1 = fopen("contact.txt", "w");
	for (i = 0; i < n; i++)
	{
		fprintf(fp1, "%s %s %c\n", a[i].name_, a[i].number_, a[i].x);
	}
	fclose(fp1);
	colour('B');
	if(count==1)
		{
			printf("\n\t\t   Contact sorted successfully\n");
		}
		else
		{
			printf("\n\t\t Contact already sorted\n");
		}
		colour('7');
}
void delete_contact_batch()
{
	char name[20];
	char num[12];
	int i = 0, n, j, k,count=0;
	char ch;
	FILE *fp, *fp1;
	fp = fopen("contact.txt", "r");
	if (fp == NULL)
	{
		colour('4');
		printf("\n\t\t   No contact Found\n");
		colour('7');
	}
	else
	{
		while ((fscanf(fp, "%s %s %c ", name, num, &ch)) != -1)
		{
			strcpy(a[i].name_, name);
			strcpy(a[i].number_, num);
			a[i].x = ch;
			i++;
		}
		colour('7');
	}
	n = i;
	fclose(fp);
	for (i = 0; i < n; i++)
	{
		for (j = i + 1; j < n; j++)
		{
			if (compare(a[i].number_, a[j].number_) == 0)
			{
				for (k = j; k < n - 1; k++)
				{
					a[k] = a[k + 1];
				}
				j--;
				n--;
				count=1;
			}
		}
	}
	fp1 = fopen("contact.txt", "w");
	for (i = 0; i < n; i++)
	{
		fprintf(fp1, "%s %s %c\n", a[i].name_, a[i].number_, a[i].x);
	}
	fclose(fp1);
	if(count==1)
		{
			printf("\n\t\t   Batch delete successfully\n");
		}
}
void backup()
{
	char name[20];
	char num[12];
	int i = 0, n,count=0;
	char ch;
	FILE *fp, *fp1;
	fp = fopen("contact.txt", "r");
	if (fp == NULL)
	{
		colour('4');
		printf("\n\t\t   No contact Found\n");
		colour('7');
	}
	else
	{
		while ((fscanf(fp, "%s %s %c ", name, num, &ch)) != -1)
		{
			strcpy(a[i].name_, name);
			strcpy(a[i].number_, num);
			a[i].x = ch;
			i++;
			count++;
		}
		colour('7');
	}
	n = i;
	fclose(fp);
	fp1 = fopen("Backup.txt", "w+");
	for (i = 0; i < n; i++)
	{
		fprintf(fp1, "%s %s %c\n", a[i].name_, a[i].number_, a[i].x);
	}
	fclose(fp1);
	colour('B');
	if(count==0)
	{
	printf("\n\t\t   File is Empty\n");
	}
	else
	{
		printf("\n\t\t   Backup successfully\n");
	}
	colour('7');
}
void about()
{
	colour('6');
	gotoxy(20, 0);
	printf("=============================\n");
	gotoxy(20, 2);
	printf("||");
	gotoxy(30, 2);
	printf("ABOUT ME");
	gotoxy(47, 2);
	printf("||");
	gotoxy(20, 3);
	printf("=============================\n");
	printf("\v\t\t  Created by:Rohan Suryawanshi\n");
	printf("\n\t\t   Version :1\n");
	printf("\n \t\t GitHub link :https://github.com/Rohan9834\n");
	colour('C');
	printf("\n\t\t   Enter [11] to go main menu\n");	colour('7');
}

void request()
{
	int choice;
	menue();
	do
	{
		colour('8');
		printf("\t\tEnter the choice :");
		scanf("%d", &choice);
		colour('7');
		printf("\n");
		switch (choice)
		{
		case 1:
			clear();
			add_contact();
			break;
		case 2:
			clear();
			edit();
			break;
		case 3:
			clear();
			delete_contact();
			break;
		case 4:
			clear();
			serch();
			break;
		case 5:
			clear();
			sort();
			break;
		case 6:
			clear();
			display_bestfriend();
			break;
		case 7:
			clear();
			display();
			break;
		case 8:
			clear();
			delete_contact_batch();
			break;
			case 9:
			clear();
			backup();
			break;
			case 10:
			system("cls");
			about();
			break;
			case 11:
			clear();
			break;
		default:
			exit(1);
		}
	} while (choice != 12);
}
int main()
{
	FILE *fp;
	fp=fopen("contact.txt","ab");
	fclose(fp);
	request();
}
