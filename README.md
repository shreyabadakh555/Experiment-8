# Experiment-8
#include <stdio.h>
int main() {
FILE *fp;
int choice;
char filename[] = "data.txt";
char text[200];
char ch;
while (1)
{
printf("\n===== MENU =====");
printf("\n1. Write to data.txt (fprintf)");
printf("\n2. Read from data.txt (fscanf)");
printf("\n3. Display data.txt (fgetc - char by char)");
printf("\n4. Exit");
printf("\nEnter your choice: ");
scanf("%d", &choice);
switch (choice) {
     case 1 :
fp = fopen("filename", "w");
if (fp == NULL) {
printf("Error opening file!\n");
break;
}
printf("Enter text to write: ");
getchar();
fgets(text, 200, stdin);
fprintf(fp, "%s", text); 
fclose(fp);
printf("Data written to data.txt\n");
case 2:
fp = fopen("filename", "r");
if (fp == NULL) {
printf("data.txt not found!\n"); 
break;
}
printf("\n--- Reading using fscanf ---\n");
while (fscanf(fp, "%199[^\n]\n", text) != EOF) {
printf("%s\n", text);
}
fclose(fp);
break;
case 3:
fp = fopen("filename", "r");
if (fp == NULL)
{ printf("data.txt not found!\n");
break;
}printf("\n--- Displaying character by character ---\n");
while ((ch = fgetc(fp)) != EOF)
{ 
    putchar(ch);
}
fclose(fp);
break;
 case 4 :
 printf("exiting....\n");
 return 0;
 default:
 printf("invalid choice!\n");
}
}
return 0;
}
