#include <stdio.h>

int main() {
    int bucket_size, output_rate, n, packet_size;
    int current_bucket = 0;

    printf("Enter bucket size: ");
    scanf("%d", &bucket_size);

    printf("Enter output rate (leak rate): ");
    scanf("%d", &output_rate);

    printf("Enter number of packets to incoming queue: ");
    scanf("%d", &n);

    printf("\n--- Simulation ---\n");
    for (int i = 1; i <= n; i++) {
        printf("Enter packet size for packet %d: ", i);
        scanf("%d", &packet_size);

        if (current_bucket + packet_size <= bucket_size) {
            current_bucket += packet_size;
            printf("Incoming packet of size %d. Bucket status: %d/%d\n", packet_size, current_bucket, bucket_size);
        } else {
            printf("Incoming packet of size %d. Bucket overflow! Dropped packet of size %d.\n", packet_size, packet_size);
        }
    }

    printf("\nLeaking packets...\n");
    while (current_bucket > 0) {
        if (current_bucket >= output_rate) {
            current_bucket -= output_rate;
        } else {
            current_bucket = 0;
        }
        printf("Leaked %d packets. Remaining in bucket: %d\n", output_rate, current_bucket);
    }

    return 0;
}
