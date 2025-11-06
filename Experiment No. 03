#include <iostream>
#include <vector>
using namespace std;
int knapsack(int W, vector<int>& profit, vector<int>& cost, int n) {
    vector<vector<int> > dp(n + 1, vector<int>(W + 1, 0));
    for (int i = 1; i <= n; i++) {
        for (int w = 1; w <= W; w++) {
            if (cost[i - 1] <= w)
                dp[i][w] = max(profit[i - 1] + dp[i - 1][w - cost[i - 1]], dp[i - 1][w]);
            else
                dp[i][w] = dp[i - 1][w];
        }
    }
    return dp[n][W];
}
int main() {
    int n;
    cout << "Enter number of projects: ";
    cin >> n;
    vector<int> profit(n), cost(n);
    cout << "Enter profit and investment cost of each project:\n";
    for (int i = 0; i < n; i++) {
        cin >> profit[i] >> cost[i];
    }
    int budget;
    cout << "Enter total available budget: ";
    cin >> budget;
    int maxProfit = knapsack(budget, profit, cost, n);
    cout << "\nMaximum profit that can be achieved = " << maxProfit << endl;
    return 0;
}
