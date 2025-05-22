
#include <iostream>
using namespace std;

int ary[10][10], completed[10], n, cost;
int startNode;  // global startNode, 0-based index

void takeInput() {
    cout << "=============================================" << endl;
    cout << "           Traveling Salesman Problem        " << endl;

    do {
        cout << "=============================================" << endl;
        cout << "= Enter the number of villages (2-10): ";
        cin >> n;
        if (n < 2 || n > 10) {
            cout << "= Error: Number of villages must be between 2 and 10!" << endl;
        }
    } while (n < 2 || n > 10);

    cout << "\nEnter the Cost Matrix (enter 0 if no direct path):\n";

    for (int i = 0; i < n; i++) {
        cout << "\nEnter Elements of Row " << i + 1 << ": ";
        for (int j = 0; j < n; j++) {
            cin >> ary[i][j];
        }
        completed[i] = 0;
    }

    cout << "\n\nThe cost matrix is:" << endl;
    for (int i = 0; i < n; i++) {
        cout << "\t";
        for (int j = 0; j < n; j++) {
            cout << ary[i][j] << "\t";
        }
        cout << endl;
    }
}

int least(int c) {
    int nc = 999;
    int min = 999, kmin;

    for (int i = 0; i < n; i++) {
        if ((ary[c][i] != 0) && (completed[i] == 0)) {
            // biaya kembali ke startNode (titik awal) bukan 0 lagi
            if (ary[c][i] + ary[i][startNode] < min) {
                min = ary[c][i] + ary[i][startNode];
                kmin = ary[c][i];
                nc = i;
            }
        }
    }

    if (min != 999) {
        cost += kmin;
    }

    return nc;
}

void mincost(int city) {
    completed[city] = 1;
    cout << city + 1 << " ---> ";
    int ncity = least(city);

    if (ncity == 999) {
        ncity = startNode;  // kembali ke titik awal
        cout << ncity + 1 << endl;
        cost += ary[city][ncity];
        return;
    }

    mincost(ncity);
}

int main() {
    char choice;
    do {
        system("cls"); 
        cost = 0;
        for (int i = 0; i < 10; i++) completed[i] = 0;

        takeInput();

        do {
            cout << "\nEnter the starting village (1 to " << n << "): ";
            cin >> startNode;
            startNode--; // ubah jadi indeks 0-based
            if (startNode < 0 || startNode >= n) {
                cout << "= Error: Starting village must be between 1 and " << n << "!" << endl;
            }
        } while (startNode < 0 || startNode >= n);

        cout << "\n\nThe Path is:\n";
        mincost(startNode);

        cout << "\nMinimum cost is " << cost << endl;
        
        cout << "=============================================" << endl;
        cout << "\nDo you want to try again? (y/n): ";
        cin >> choice;
    } while (choice == 'y' || choice == 'Y');

    cout << "Thank you for using the program!" << endl;
    cout << "=============================================" << endl;

    return 0;
}
