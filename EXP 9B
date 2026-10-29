#include <stdio.h>

int main() {
    int max_capacity, tokens, token_rate, n, packet_tokens;

    printf("Enter maximum capacity of token bucket: ");
    scanf("%d", &max_capacity);

    printf("Enter initial tokens in bucket: ");
    scanf("%d", &tokens);

    printf("Enter token generation rate per interval: ");
    scanf("%d", &token_rate);

    printf("Enter number of incoming packets: ");
    scanf("%d", &n);

    printf("\n");
    for (int i = 1; i <= n; i++) {
        printf("Packet %d requires tokens: ", i);
        scanf("%d", &packet_tokens);

        if (tokens >= packet_tokens) {
            tokens -= packet_tokens;
            printf("Tokens available: %d + generated (%d). Packet transmitted successfully! Remaining tokens: %d\n\n", 
                   tokens + packet_tokens, 0, tokens);
        } else {
            printf("Not enough tokens! Adding generated tokens...\n");
            tokens += token_rate;
            if (tokens > max_capacity) tokens = max_capacity;

            if (tokens >= packet_tokens) {
                tokens -= packet_tokens;
                printf("Current tokens after refill: %d. Packet transmitted successfully! Remaining tokens: %d\n\n", 
                       tokens + packet_tokens, tokens);
            } else {
                printf("Current tokens: %d. Still insufficient tokens. Packet delayed/dropped.\n\n", tokens);
            }
        }
    }

    return 0;
}
