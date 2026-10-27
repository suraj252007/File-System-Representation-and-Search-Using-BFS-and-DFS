
#include <stdio.h>
#include <string.h>

#define MAX 50

int graph[MAX][MAX];
char files[MAX][50];
int visited[MAX];
int n, found;

// Breadth-First Search
void BFS(int start, int target) {
    int queue[MAX], front = 0, rear = 0;
    int seen[MAX] = {0};

    queue[rear++] = start;
    seen[start] = 1;

    printf("\nBFS Traversal: ");

    while (front < rear) {
        int current = queue[front++];

        printf("%s ", files[current]);

        if (current == target)
            found = 1;

        for (int i = 0; i < n; i++) {
            if (graph[current][i] && !seen[i]) {
                seen[i] = 1;
                queue[rear++] = i;
            }
        }
    }

    printf("\nBFS Search: %s\n",
           found ? "File Found" : "File Not Found");
}

// Depth-First Search
void DFS(int current, int target) {
    visited[current] = 1;

    printf("%s ", files[current]);

    if (current == target)
        found = 1;

    for (int i = 0; i < n; i++) {
        if (graph[current][i] && !visited[i])
            DFS(i, target);
    }
}

int main() {
    int start, target = -1;
    char targetName[50];

    printf("Enter number of files/directories: ");
    scanf("%d", &n);

    if (n < 1 || n > MAX) {
        printf("Invalid number of nodes.\n");
        return 1;
    }

    printf("Enter file/directory names:\n");
    for (int i = 0; i < n; i++)
        scanf("%49s", files[i]);

    printf("Enter adjacency matrix (%d x %d):\n", n, n);
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++)
            scanf("%d", &graph[i][j]);
    }

    printf("Enter starting node index (0 to %d): ", n - 1);
    scanf("%d", &start);

    if (start < 0 || start >= n) {
        printf("Invalid starting node.\n");
        return 1;
    }

    printf("Enter file name to search: ");
    scanf("%49s", targetName);

    for (int i = 0; i < n; i++) {
        if (strcmp(files[i], targetName) == 0) {
            target = i;
            break;
        }
    }

    found = 0;
    BFS(start, target);

    found = 0;
    for (int i = 0; i < n; i++)
        visited[i] = 0;

    printf("\nDFS Traversal: ");
    DFS(start, target);

    printf("\nDFS Search: %s\n",
           found ? "File Found" : "File Not Found");

    return 0;
}
