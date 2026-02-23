# Binary Search

Definition:
Binary Search is an efficient searching algorithm that finds the position of a target element
in a sorted array by repeatedly dividing the search range into half.

#include <iostream>
using namespace std;

// Binary Search Function
int binarySearch(int arr[], int n, int target) {
    int left = 0;
    int right = n - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target)
            return mid;  // Element found

        else if (arr[mid] < target)
            left = mid + 1;  // Search right half

        else
            right = mid - 1; // Search left half
    }

    return -1;  // Element not found
}

int main() {
    int n;

    cout << "Enter number of elements: ";
    cin >> n;

    int arr[n];

    cout << "Enter elements (sorted order):\n";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    int target;
    cout << "Enter element to search: ";
    cin >> target;

    int result = binarySearch(arr, n, target);

    if (result != -1)
        cout << "Element found at index: " << result;
    else
        cout << "Element not found";

    return 0;
}
