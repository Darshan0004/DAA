# Dijkstra’s Algorithm

Definition:
Dijkstra’s Algorithm is used to find the shortest path from a source vertex to all other vertices in a weighted graph with non-negative edge weights.

-----------------

#include <iostream>
#include <climits>
using namespace std;

#define V 100

// Function to find the vertex with minimum distance
int minDistance(int dist[], bool visited[], int n) {
    int min = INT_MAX, minIndex;

    for (int v = 0; v < n; v++) {
        if (!visited[v] && dist[v] <= min) {
            min = dist[v];
            minIndex = v;
        }
    }
    return minIndex;
}

// Dijkstra's Algorithm
void dijkstra(int graph[V][V], int n, int src) {
    int dist[V];
    bool visited[V];

    for (int i = 0; i < n; i++) {
        dist[i] = INT_MAX;
        visited[i] = false;
    }

    dist[src] = 0;

    for (int count = 0; count < n - 1; count++) {
        int u = minDistance(dist, visited, n);
        visited[u] = true;

        for (int v = 0; v < n; v++) {
            if (!visited[v] && graph[u][v] &&
                dist[u] != INT_MAX &&
                dist[u] + graph[u][v] < dist[v]) {

                dist[v] = dist[u] + graph[u][v];
            }
        }
    }

    cout << "Vertex\tDistance from Source\n";
    for (int i = 0; i < n; i++)
        cout << i << "\t" << dist[i] << endl;
}

int main() {
    int n;

    cout << "Enter number of vertices: ";
    cin >> n;

    int graph[V][V];

    cout << "Enter adjacency matrix:\n";
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            cin >> graph[i][j];

    int src;
    cout << "Enter source vertex: ";
    cin >> src;

    dijkstra(graph, n, src);

    return 0;
}

