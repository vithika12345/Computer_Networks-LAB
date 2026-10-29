#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <arpa/inet.h>

#define PORT 10298
#define BUF_SIZE 1024

int main(int argc, char *argv[]) {
    int sock = 0;
    struct sockaddr_in serv_addr;
    char buffer[BUF_SIZE] = {0};
    char message[BUF_SIZE];

    if (argc != 2) {
        printf("Usage: %s <Server IP>\n", argv[0]);
        return -1;
    }

    sock = socket(AF_INET, SOCK_STREAM, 0);
    if (sock < 0) {
        printf("\n Socket creation error \n");
        return -1;
    }

    serv_addr.sin_family = AF_INET;
    serv_addr.sin_port = htons(PORT);

    if (inet_pton(AF_INET, argv[1], &serv_addr.sin_addr) <= 0) {
        printf("\nInvalid address/ Address not supported \n");
        return -1;
    }

    if (connect(sock, (struct sockaddr *)&serv_addr, sizeof(serv_addr)) < 0) {
        printf("\nConnection Failed \n");
        return -1;
    }
    printf("Connected to server. Enter message: ");

    while (fgets(message, BUF_SIZE, stdin) != NULL) {
        send(sock, message, strlen(message), 0);
        int valread = read(sock, buffer, BUF_SIZE);
        printf("Echo from server: %s", buffer);
        memset(buffer, 0, BUF_SIZE);
        printf("Enter message: ");
    }

    close(sock);
    return 0;
}
