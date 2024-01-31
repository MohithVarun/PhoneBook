#include<stdio.h>
#include<stdlib.h>
#include<string.h>

#define Name_len_Max 30
#define phone_len_Max 15
#define email_len_Max 50
#define Max_contacts_Max 50
struct Contact
	{
		char Cname[Name_len_Max];
		char Cnumber[phone_len_Max];
		char Cemail[email_len_Max];
	};
void add_contacts(struct Contact *contacts, int *count)
{
	FILE *fp;
	for(int i=0;i<*count;i++)
	{
    printf("Enter name %d: ",i+1);
    scanf("%s", contacts[i].Cname); //please,use undescore' _ ' instead of space .
    printf("Enter phone %d: ",i+1);
    scanf("%s", contacts[i].Cnumber);
    printf("Enter email %d: ",i+1);
    scanf("%s", contacts[i].Cemail);
	}
	printf("Name\tM_number\tEmail\n");
}
void save_contacts(char *filename, struct Contact *contacts, int *count)
{
    FILE *fp;
    fp = fopen(filename, "w+");
    if (fp == NULL)
	{
        printf("Error opening file!\n");
        return;
    }
    for (int i = 0; i < *count; i++) 
	{
        fprintf(fp,"%s\t%s\t%s\n", contacts[i].Cname, contacts[i].Cnumber, contacts[i].Cemail);
        printf("%s\t%s\t%s\n",contacts[i].Cname, contacts[i].Cnumber, contacts[i].Cemail);
    }
    fclose(fp);
    printf("Contacts saved successfully!\n");
}

void edit_contact(char *filename,struct Contact *contacts, int count) 
{
    char name[Name_len_Max];
    printf("Enter the name of the contact to edit: ");
    scanf("%s", name);
    int index = -1;
    for(int i = 0; i < count; i++) 
	{
        if (strcmp(contacts[i].Cname,name) == 0) 
		{
            index = i;
            break;
        }
    }
    if (index == -1) 
	{
        printf("Contact not found!\n");
        return;
    }
    printf("Enter the new information for %s:\n", name);
    printf("Name: ");
    scanf("%s", contacts[index].Cname);
    printf("Phone: ");
    scanf("%s", contacts[index].Cnumber);
    printf("Email: ");
    scanf("%s", contacts[index].Cemail);
    save_contacts(filename,contacts,&count);
    printf("Contact edited successfully!\n");
}
void delete_contact(char *filename, struct Contact *contacts, int *count)
{
    char name[Name_len_Max];
    printf("Enter the name of the contact to delete: ");
    scanf("%s", name);
    int index = -1;
    for (int i = 0; i < *count; i++) 
	{
        if (strcmp(contacts[i].Cname,name)==0) 
		{
            index = i;
            break;
        }
    }
    if(index == -1) 
	{
        printf("Contact not found!\n");
        return;
    }
    struct Contact temp_contacts[*count];
    int temp_count = 0;
    for (int i = 0; i < *count; i++) 
	{
        if (i != index) 
		{
            temp_contacts[temp_count++] = contacts[i];
        }
    }
    *count = temp_count;
    for (int i = 0; i < *count; i++) 
	{
        contacts[i] = temp_contacts[i];
    }
    save_contacts(filename,contacts,count);
    printf("Contact deleted successfully!\n");
}
void display(void)
{
	printf("*\n");
	printf("[1].Edit contact\n");
	printf("[2].Delete contact\n");
	printf("*\n");
}
int main() 
{
	struct Contact contacts[100];
	char filename[]="phonebook.txt";
    int count,save,type;
    printf("\t\t*****************************  Welcome to Phonebook *****************************\n\t\t\t\t \3 here you can create contacts of your loved ones \3 \n\n");
     printf("Enter no:of contacts: ");
    scanf("%d",&count);
    printf("If you want to enter contact 1(enter) 2(ignore) : ");
    scanf("%d",&save);
    if(save==1)
    {
    add_contacts(contacts,&count);
    save_contacts(filename,contacts,&count);
	}
	display();
	printf("Select one option : ");
    scanf("%d",&type);
	if(type==1)
	{
    edit_contact(filename,contacts,count);
	}
	else if(type==2)
	{
    delete_contact(filename,contacts,&count);
	}
	else
	printf("Done \1 ");
	return 0;
}
