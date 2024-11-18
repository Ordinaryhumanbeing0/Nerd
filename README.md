#include <stdio.h>
#include <string.h>
 
void main()
{
   int ch;
   float a[100]; // Changed to float for precision
   float totalExpense = 0, salary = 0;
   char categories[100][20]; // Support up to 100 categorized expenses
   int expenseCount = 0; // Track the number of expenses
 
   while (1)
   {
       printf("\n EXPENSE TRACKER\n");
       printf("1. Enter Salary\n");
       printf("2. Add Expense\n");
       printf("3. View Total Expense\n");
       printf("4. Check Balance\n");
       printf("5. Exit\n");
 
       printf("Enter Your Choice: ");
       scanf("%d", &ch);
 
       switch (ch)
       {
           case 1:
               printf("Enter Salary: ");
               scanf("%f", &salary);
               printf("Salary recorded: ₹%.2f\n", salary);
               break;
 
           case 2:
               printf("How many expenses do you want to add (max 100)? ");
               int count;
               scanf("%d", &count);
 
               if (expenseCount + count > 100)
               {
                   printf("Cannot add more than 100 expenses in total.\n");
                   break;
               }
 
               for (int i = 0; i < count; i++)
               {
                   printf("Enter expense %d (amount and category): ", expenseCount + 1);
                   scanf("%f", &a[expenseCount]);
                   scanf("%s", categories[expenseCount]);
                   totalExpense += a[expenseCount];
                   expenseCount++;
               }
               printf("Expenses added successfully!\n");
               break;
 
           case 3:
               printf("Categorized Expenses:\n");
               for (int i = 0; i < expenseCount; i++)
               {
                   printf("%s: ₹%.2f\n", categories[i], a[i]);
               }
               printf("Total Expense: ₹%.2f\n", totalExpense);
               break;
 
           case 4:
               printf("Your Balance: ₹%.2f\n", salary - totalExpense);
               break;
 
           case 5:
               printf("EXITING PROGRAM!! GOODBYE!!!\n");
               return;
 
           default:
               printf("INVALID CHOICE! Please try again...\n");
       }
   }
}