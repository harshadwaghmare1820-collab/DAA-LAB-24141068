#include <bits/stdc++.h>
using namespace std;
int main() {
    int V;
    cout << "Enter number of cities: ";
    cin >> V;
    vector<string> cityNames(V);
    cout << "Enter city names:\n";
    for (int i = 0; i < V; i++) {
        cin >> cityNames[i];
    }
    vector<vector<int>> cost(V, vector<int>(V));
    cout << "\nEnter road construction cost matrix (0 if no direct road):\n";
    for (int i = 0; i < V; i++) {
        for (int j = 0; j < V; j++) {
            cin >> cost[i][j];
        }
    }
    vector<int> key(V, INT_MAX);
    vector<int> parent(V, -1);
    vector<bool> inMST(V, false);
    key[0] = 0; // start from first city
    for (int count = 0; count < V - 1; count++) {
        int u = -1;
        // Find city with minimum key value not in MST
        for (int i = 0; i < V; i++) {
            if (!inMST[i] && (u == -1 || key[i] < key[u]))
                u = i;
        }
        inMST[u] = true;
        // Update key and parent for adjacent cities
        for (int v = 0; v < V; v++) {
            if (cost[u][v] && !inMST[v] && cost[u][v] < key[v]) {
                key[v] = cost[u][v];
                parent[v] = u;
            }
        }
    }
    cout << "\n Minimum Cost Road Network:\n";
    cout << "Road (City1 - City2) : Cost\n";
    int totalCost = 0;
    for (int i = 1; i < V; i++) {
        cout << cityNames[parent[i]] << " - " 
             << cityNames[i] << " : " 
             << cost[i][parent[i]] << "\n";
        totalCost += cost[i][parent[i]];
    }
    cout << "\nTotal Minimum Construction Cost = " << totalCost << endl;
    return 0;
}
