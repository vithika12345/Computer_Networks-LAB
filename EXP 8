#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_FRAMES 50

void sender(int frames[], int size, int window_size);
void receiver(int frames[], int start, int window_size);

int main() {
    int n, window_size;
    int frames[MAX_FRAMES];

    printf("Sliding Window Protocol Simulation (Go-Back-N)\n");
    printf("Enter number of frames to send (max %d): ", MAX_FRAMES);
    scanf("%d", &n);

    if (n > MAX_FRAMES || n <= 0) {
        printf("Invalid number of frames \n");
        return 0;
    }

    printf("Enter window size: ");
    scanf("%d", &window_size);

    for (int i = 0; i < n; i++) {
        frames[i] = i;
    }

    int i = 0;
    char choice;

    while (i < n) {
        printf("\nSender window: ");
        for (int j = i; j < i + window_size && j < n; j++) {
            printf("[%d] ", frames[j]);
        }
        printf("\n");

        printf("Sending frames...\n");
        int sent_count = 0;
        for (int j = i; j < i + window_size && j < n; j++) {
            printf("Sent frame: %d\n", frames[j]);
            sent_count++;
        }

        printf("\nSimulating receiver...\n");
        int ack = i;
        for (int j = i; j < i + window_size && j < n; j++) {
            printf("Received frame: %d, sending ACK: %d\n", frames[j], frames[j] + 1);
            ack = j + 1;
        }

        printf("\nDid all frames receive correctly? (y/n): ");
        scanf(" %c", &choice);

        if (choice == 'y' || choice == 'Y') {
            i += sent_count;
        } else {
            printf("Error detected! Resending window (Go-Back-N)...\n");
        }
    }

    printf("All frames sent successfully!\n");
    return 0;
}
