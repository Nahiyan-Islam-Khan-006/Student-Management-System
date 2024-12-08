#include <stdio.h>

struct Student {
    int id;
    char name[50];
    int age;
    float grades[3];
    float average;
};
float calculateAverage(float grades[]) {
    return (grades[0] + grades[1] + grades[2]) / 3;
}
int main() {
    struct Student students[100];
    int count = 0, choice;

    while (1) {
        printf("\n=== Student Management System ===\n");
        printf("1. Add Student\n2. View All Students\n3. Exit\nEnter your choice: ");
        scanf("%d", &choice);

        if (choice == 1) {
            if (count >= 100) {
                printf("Student list is full!\n");
                continue;
            }

            printf("\nEnter Student ID, Name, Age, and 3 Grades: ");
            scanf("%d %s %d %f %f %f", &students[count].id, students[count].name,
                                       &students[count].age,
                                       &students[count].grades[0],
                                       &students[count].grades[1],
                                       &students[count].grades[2]),
                                       students[count].average = calculateAverage(students[count].grades);
            printf("Student added successfully!\n");
            count++;
        }
        else if (choice == 2) {
            if (count == 0) {
                printf("No students in the system yet!\n");
            } else {
                for (int i = 0; i < count; i++) {
                    printf("\nStudent %d:\n", i + 1);
                    printf("ID: %d\nName: %s\nAge: %d\nGrades: %.2f, %.2f, %.2f\nAverage: %.2f\n",
                           students[i].id, students[i].name, students[i].age,
                           students[i].grades[0], students[i].grades[1], students[i].grades[2],
                           students[i].average);
                }
            }
        }
        else if (choice == 3) {
            printf("Exiting program.\n");
            break;
        }
        else {
            printf("Invalid choice. Try again.\n");
        }
    }

    return 0;
}
