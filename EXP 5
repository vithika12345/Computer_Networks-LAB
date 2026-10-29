#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <arpa/inet.h>

#define PORT 10290
#define BUF_SIZE 1024

int main(int argc, char *argv[]) {
    int sock;
    struct sockaddr_in servaddr;
    char buffer[BUF_SIZE];
    char message[BUF_SIZE];
    socklen_t len;
    int n;

    if (argc != 2) {
        printf("Usage: %s <Server IP>\n", argv[0]);
        return -1;
    }

    // 1. Socket Creation
    if ((sock = socket(AF_INET, SOCK_DGRAM, 0)) < 0) {
        perror("socket creation failed");
        exit(EXIT_FAILURE);
    }

    memset(&servaddr, 0, sizeof(servaddr));

    // 2. Server Address Configuration
    servaddr.sin_family = AF_INET;
    servaddr.sin_port = htons(PORT);
    if (inet_pton(AF_INET, argv[1], &servaddr.sin_addr) <= 0) {
        printf("\nInvalid address/ Address not supported \n");
        return -1;
    }

    printf("Enter message to send: ");
    while (fgets(message, BUF_SIZE, stdin) != NULL) {
        // 3. Data Transmission
        sendto(sock, (const char *)message, strlen(message), MSG_CONFIRM, (const struct sockaddr *)&servaddr, sizeof(servaddr));
        
        len = sizeof(servaddr);
        memset(buffer, 0, BUF_SIZE);
        
        // 4. Receiving Response
        n = recvfrom(sock, (char *)buffer, BUF_SIZE, MSG_WAITALL, (struct sockaddr *)&servaddr, &len);
        buffer[n] = '\0';
        printf("Echo from server: %s", buffer);
        
        printf("Enter message to send: ");
    }

    // 5. Socket Closure
    close(sock);
    return 0;
}
