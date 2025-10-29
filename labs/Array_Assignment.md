# 🧮 Assignment: Working with Arrays in C++

## 🎯 Objective
Practice working with arrays and basic control structures in C++. You will write a program that:
1. Accepts **unique integers** (no duplicates).  
2. Allows the user to **perform operations** on the array:
   - Sort the array (ascending or descending)  
   - Find the maximum number  

You will **not** use any library other than the ones specified.

---

## 🧠 Instructions

1. Create a C++ program that:
   - Declares a **fixed-size `std::array<int, N>`** (you can choose `N = 5` or any small number).
   - Prompts the user to **enter unique integers** (ensure no duplicates are allowed).
   - Displays a menu asking the user to perform one of the following operations:
     - **(a)** Sort the array in ascending order  
     - **(b)** Sort the array in descending order  
     - **(c)** Find the **maximum number**
   - Uses only **manual sorting logic** (e.g., nested loops).  
   - Displays the results clearly after the operation.

2. **Allowed headers only:**
   ```cpp
   #include <iostream>
   #include <array>
   ```

3. **Not allowed:**
   - `<algorithm>`
   - `<vector>`
   - `<set>` or any STL container other than `std::array`
   - Any other header files

---

## 🧩 Example Output

```
Enter 5 unique integers:
Element 1: 4
Element 2: 9
Element 3: 2
Element 4: 9
Duplicate found! Enter a different number.
Element 4: 6
Element 5: 3

Choose an operation:
1. Sort Ascending
2. Sort Descending
3. Find Maximum
Enter your choice: 1

Array sorted in ascending order:
2 3 4 6 9
```

---

## 💡 Hints
- Use **nested loops** for sorting (like bubble sort).
- Use a **`switch` statement** for menu selection.
- Keep your code modular and readable.

---

## 📦 Submission Requirements
- Submit the code in github in markdown format and share the link. No grading if the file is not formatted and uploaded correctly
- Make sure you add me as a collaborator in your repo. Add me with my email dkhan1010@gmail.com
- File name: `array_operations.md`
- Include your **name**, **course**, and **date** as comments at the top of the file.

```cpp
// Name: Kaeden Le
// Course: CISC 192 - C++ Programming
// Date: 10/28/2025
// Assignment: Non-Duplicated Integer Array Operations

#include <iostream>
#include <array>
using namespace std;

int main() {
    const int N = 5;
    array<int, N> nums{};
    int val;

    cout << "Enter " << N << " unique integers:\n";
    for (int i = 0; i < N; i++) {
        bool dup;
        do {
            dup = false;
            cout << "Element " << i + 1 << ": ";
            cin >> val;
            for (int j = 0; j < i; j++) {
                if (nums[j] == val) {
                    cout << "Duplicate found! Enter a different number.\n";
                    dup = true;
                    break;
                }
            }
        } while (dup);
        nums[i] = val;
    }

    cout << "\nChoose an operation:\n";
    cout << "1. Sort Ascending\n";
    cout << "2. Sort Descending\n";
    cout << "3. Find Maximum\n";
    cout << "Enter your choice: ";

    int choice;
    cin >> choice;

    if (choice == 1 || choice == 2) {
        for (int i = 0; i < N - 1; i++) {
            for (int j = 0; j < N - i - 1; j++) {
                bool doSwap = (choice == 1 && nums[j] > nums[j + 1]) ||
                              (choice == 2 && nums[j] < nums[j + 1]);
                if (doSwap) {
                    int t = nums[j];
                    nums[j] = nums[j + 1];
                    nums[j + 1] = t;
                }
            }
        }
    }

    switch (choice) {
        case 1:
            cout << "\nArray sorted in ascending order:\n";
            for (int i = 0; i < N; i++) cout << nums[i] << ' ';
            cout << '\n';
            break;
        case 2:
            cout << "\nArray sorted in descending order:\n";
            for (int i = 0; i < N; i++) cout << nums[i] << ' ';
            cout << '\n';
            break;
        case 3: {
            int m = nums[0];
            for (int i = 1; i < N; i++)
                if (nums[i] > m) m = nums[i];
            cout << "\nMaximum value: " << m << '\n';
            break;
        }
        default:
            cout << "\nInvalid choice!\n";
    }

    return 0;
}

```

---

## ✅ Grading Rubric

| Criteria | Points |
| :-- | --: |
| Correct implementation of unique array input | 20 |
| Sorting logic (ascending and descending) | 25 |
| Finding maximum element | 15 |
| Correct use of `<array>` and `<iostream>` only | 20 |
| Code readability and output clarity | 10 |
| Comments and documentation | 10 |
| **Total** | **100** |
