



#include <stdio.h>

int main() {
    int arr[100], ch, n = 0, i, value, index ;

    do {
        printf("1. Insert\n");
        printf("2. Update\n");
        printf("3. Delete\n");
        printf("4. Sort\n");
        printf("5. Search\n");
        printf("6. Display\n");
        printf("7. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &ch);

        switch (ch) {
        case 1:
            printf("How many numbers you want to insert: ");
            scanf("%d", &n);
            printf("Enter %d numbers:\n", n);
            for (i = 0; i < n; i++) {
                scanf("%d", &arr[i]);
            }
            break;

        case 2:
            printf("Enter index to update (0 to %d): ", n - 1);
            scanf("%d", &index);
            if (index >= 0 && index < n) {
                printf("Enter new value: ");
                scanf("%d", &value);
                arr[index] = value;
            } else {
                printf("Invalid index!\n");
            }
            break;

        case 3:
            printf("Enter value to delete: ");
            scanf("%d", &value);
            int found = 0;
            for (i = 0; i < n; i++) {
                if (arr[i] == value) {
                    found = 1;
                    for (int j = i; j < n - 1; j++) {
                        arr[j] = arr[j + 1];
                    }
                    n--;
                    break;
                }
            }
            if (!found)
                printf("Value not found!\n");
            else
                printf("Value deleted successfully.\n");
            break;

        case 4:
            for (i = 0; i < n - 1; i++) {
                for (int j = i + 1; j < n; j++) {
                    if (arr[i] > arr[j]) {
                        int temp = arr[i];
                        arr[i] = arr[j];
                        arr[j] = temp;
                    }
                }
            }
            printf(" Your is array sorted.\n");
            break;

        case 5:
            printf("Enter value to search: ");
            scanf("%d", &value);
            int foundIndex = -1;
            for (i = 0; i < n; i++) {
                if (arr[i] == value) {
                    foundIndex = i;
                    break;
                }
            }
            if (foundIndex != -1)
                printf("Value found at index %d\n", foundIndex);
            else
                printf("Value not found!\n");
            break;

        case 6:
            printf("Current array elements: ");
            for (i = 0; i < n; i++) {
                printf("%d ", arr[i]);
            }
            printf("\n");
            break;

        case 7:
            printf("Happy coding .bye\n");
            break;

        default:
            printf("Invalid choice! Please enter between 1-7.\n");
        }

    } while (ch != 7);

return 0;
}
