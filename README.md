#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main() {
 char *name = malloc(50);
 char grade[3];
 int marks[5], total = 0;
 float percentage;
 FILE *fp;
 if (name == NULL)
 return 1;
 printf("Enter Student Name: ");
 scanf("%49s", name);
 printf("Enter marks of 5 subjects:\n");
 for (int i = 0; i < 5; i++) {
 scanf("%d", &marks[i]);
 total += marks[i];
 }
 percentage = total / 5.0;
 if (percentage >= 90)
 strcpy(grade, "A+");
 else if (percentage >= 75)
 strcpy(grade, "A");
 else if (percentage >= 60)
 strcpy(grade, "B");
 else if (percentage >= 40)
 strcpy(grade, "C");
 else
 strcpy(grade, "F");
 printf("\nStudent: %s", name);
 printf("\nTotal: %d/500", total);
 printf("\nPercentage: %.2f%%", percentage);
 printf("\nGrade: %s", grade);
 if (strcmp(grade, "A+") == 0)
 printf("\nExcellent!");
 fp = fopen("result.txt", "a");
 if (fp != NULL) {
 fprintf(fp, "%s %d %.2f %s\n",
 name, total, percentage, grade);
 fclose(fp);
 }
 free(name);
 return 0;
}
