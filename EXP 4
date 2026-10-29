#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <arpa/inet.h>

#define PORT 10290
#define BUF_SIZE 1024

int main() {
    int server_fd;
    struct sockaddr_in servaddr, cliaddr;
    char buffer[BUF_SIZE];
    socklen_t len;
    int n;

    // 1. Socket Creation
    if ((server_fd = socket(AF_INET, SOCK_DGRAM, 0)) < 0) {
        perror("socket creation failed");
        exit(EXIT_FAILURE);
    }

    memset(&servaddr, 0, sizeof(servaddr));
    memset(&cliaddr, 0, sizeof(cliaddr));

    servaddr.sin_family = AF_INET;
    servaddr.sin_addr.s_addr = INADDR_ANY;
    servaddr.sin_port = htons(PORT);

    // 2. Binding
    if (bind(server_fd, (const struct sockaddr *)&servaddr, sizeof(servaddr)) < 0) {
        perror("bind failed");
        exit(EXIT_FAILURE);
    }

    printf("UDP Echo Server listening on port %d...\n", PORT);

    len = sizeof(cliaddr);

    while (1) {
        memset(buffer, 0, BUF_SIZE);
        // 3. Receiving Data
        n = recvfrom(server_fd, (char *)buffer, BUF_SIZE, MSG_WAITALL, (struct sockaddr *)&cliaddr, &len);
        buffer[n] = '\0';
        printf("Received from client: %s", buffer);

        // 4. Sending Data (Echo back)
        sendto(server_fd, (const char *)buffer, strlen(buffer), MSG_CONFIRM, (const struct sockaddr *)&cliaddr, len);
        printf("Sent back to client: %s", buffer);
    }

    // 5. Closing Socket
    close(server_fd);
    return 0;
}
