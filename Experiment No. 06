#include <bits/stdc++.h>
using namespace std;
// Function to find the vertex with the minimum distance
int findMinDistance(vector<int>& dist, vector<bool>& visited, int V) {
    int minVal = INT_MAX, minIndex = -1;
    for (int i = 0; i < V; i++) {
        if (!visited[i] && dist[i] < minVal) {
            minVal = dist[i];
            minIndex = i;
        }
    }
    return minIndex;
}
// Function to print the actual shortest path
void printPath(int j, vector<int>& parent, vector<string>& routers) {
    if (parent[j] == -1)
        return;
    printPath(parent[j], parent, routers);
    cout << " -> " << routers[j];
}
int main() {
    int V;
    cout << "Enter number of routers in the network: ";
    cin >> V;
    vector<string> routers(V);
    cout << "Enter router names:\n";
    for (int i = 0; i < V; i++)
        cin >> routers[i];
    vector<vector<int>> delay(V, vector<int>(V));
    cout << "\nEnter network delay matrix (0 if no direct connection):\n";
    for (int i = 0; i < V; i++)
        for (int j = 0; j < V; j++)
            cin >> delay[i][j];
    int src;
    cout << "\nEnter source router index (0 to " << V - 1 << "): ";
    cin >> src;
    vector<int> dist(V, INT_MAX);
    vector<bool> visited(V, false);
    vector<int> parent(V, -1);
    dist[src] = 0;
    // Dijkstra’s algorithm
    for (int count = 0; count < V - 1; count++) {
        int u = findMinDistance(dist, visited, V);
        visited[u] = true;
        for (int v = 0; v < V; v++) {
            if (!visited[v] && delay[u][v] && dist[u] + delay[u][v] < dist[v]) {
                dist[v] = dist[u] + delay[u][v];
                parent[v] = u;
            }
        }
    }
    cout << "\n Fastest Data Transfer from Router " << routers[src] << ":\n";
    cout << "Destination\tDelay (ms)\tPath\n";
    for (int i = 0; i < V; i++) {
        cout << routers[i] << "\t\t" << dist[i] << " ms\t\t";
        cout << routers[src];
        printPath(i, parent, routers);
        cout << endl;
    }
    return 0;
}
