# Linear Search

Definition:
Linear Search is a simple searching algorithm that checks each element of the array one by one until the target element is found or the array ends.



#include <iostream>
using namespace std;

// Linear Search Function
int linearSearch(int arr[], int n, int target) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == target)
            return i;   // Element found
    }
    return -1;          // Element not found
}

int main() {
    int n;

    cout << "Enter number of elements: ";
    cin >> n;

    int arr[n];

    cout << "Enter elements:\n";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    int target;
    cout << "Enter element to search: ";
    cin >> target;

    int result = linearSearch(arr, n, target);

    if (result != -1)
        cout << "Element found at index: " << result;
    else
        cout << "Element not found";

    return 0;
}
