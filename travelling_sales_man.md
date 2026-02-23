# Travelling Salesman Problem (TSP)

Definition:
The Travelling Salesman Problem (TSP) is a problem where a salesman must visit all cities exactly once and return to the starting city, minimizing the total travel cost.

Below is a simple brute-force recursive solution (good for small number of cities).

---------------------------

#include <iostream>
#include <climits>
using namespace std;

#define MAX 10

int n;  // Number of cities
int cost[MAX][MAX];
bool visited[MAX];
int minCost = INT_MAX;

// TSP Recursive Function
void tsp(int currentCity, int count, int currentCost) {
    // If all cities visited and back to start
    if (count == n && cost[currentCity][0]) {
        minCost = min(minCost, currentCost + cost[currentCity][0]);
        return;
    }

    for (int i = 0; i < n; i++) {
        if (!visited[i] && cost[currentCity][i]) {
            visited[i] = true;
            tsp(i, count + 1, currentCost + cost[currentCity][i]);
            visited[i] = false;  // Backtrack
        }
    }
}

int main() {
    cout << "Enter number of cities: ";
    cin >> n;

    cout << "Enter cost matrix:\n";
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cin >> cost[i][j];
        }
    }

    for (int i = 0; i < n; i++)
        visited[i] = false;

    visited[0] = true;  // Start from city 0

    tsp(0, 1, 0);

    cout << "Minimum travelling cost: " << minCost;

    return 0;
}
