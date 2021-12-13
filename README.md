/# Project-5
/*
 * Class: CMSC140 CRN 20433_22867
 * Instructor: Grigoriy A. Grinberg
 * Project 5
 * Description:a program that simulates a magic square using 3 one
   dimensional parallel arrays of integer type.
 * Due Date: 12/06/21
 * I pledge that I have completed the programming assignment independently.
   I have not copied the code from a student or any source.
   I have not given my code to any student.
   Print your Full Name here: kirubel mogese
               */




#include <iostream>
using namespace std;

const int ROWS = 3;  // The number of rows in the array
const int COLS = 3;  // The number of columns in the array
const int MIN = 1;  // The value of the smallest number
const int MAX = 9;  // The value of the largest number



 // Function prototypes
bool isMagicSquare(int arrayRow1[], int arrayRow2[], int arrayRow3[], int size);
bool checkRange(int arrayRow1[], int arrayRow2[], int arrayRow3[], int size, int min, int max);
bool checkUnique(int arrayRow1[], int arrayRow2[], int arrayRow3[], int size);
bool checkRowSum(int arrayRow1[], int arrayRow2[], int arrayRow3[], int size);
bool checkColSum(int arrayRow1[], int arrayRow2[], int arrayRow3[], int size);
bool checkDiagSum(int arrayRow1[], int arrayRow2[], int arrayRow3[], int size);
void fillArray(int arrayRow1[], int arrayRow2[], int arrayRow3[], int size);
void showArray(int arrayRow1[], int arrayRow2[], int arrayRow3[], int size);



int main()
{

    int magicArrayRow1[COLS], magicArrayRow2[COLS], magicArrayRow3[COLS];

    char  yes = 'y';

    do {


        fillArray(magicArrayRow1, magicArrayRow2, magicArrayRow3, COLS);

        showArray(magicArrayRow1, magicArrayRow2, magicArrayRow3, COLS);

        if (isMagicSquare(magicArrayRow1, magicArrayRow2, magicArrayRow3, COLS))
        {
            cout << "This is a Lo Shu magic square" << endl;
        }
        else
            cout << "This is not a Lo Shu magic square" << endl;

        cout << "\nDo you want to try again?(Type y or n) ";

        cin >> yes;
        cout << "\n";
    } while (yes == 'y');

    cout << "Kirubel Mogese\n";
    cout << "Progest 5\n";
    cout << "Due:12/06/2021";


    return 0;
}


void fillArray(int arrayRow1[], int arrayRow2[], int intarrayRow3[], int size)
{
    int row_Num = 0;

    for (int column_Num = 0; column_Num < size; column_Num++)
    {

        cout << "Enter the number for row " << row_Num
            << " and for column " << column_Num << " :";
        cin >> arrayRow1[column_Num];
    }
    row_Num++;

    for (int colNum = 0; colNum < size; colNum++)
    {

        cout << "Enter the number for row " << row_Num
            << " and for column " << colNum << " :";
        cin >> arrayRow2[colNum];
    }
    row_Num++;

    for (int colNumber = 0; colNumber < size; colNumber++)
    {

        cout << "Enter the number for row " << row_Num
            << " and for column " << colNumber << " : ";
        cin >> intarrayRow3[colNumber];
    }

}


void showArray(int arrayrow1[], int arrayrow2[], int arrayrow3[], int size)
{
    int row_Num = 0;
    for (int col_Num = 0; col_Num < size; col_Num++)
    {
        cout << arrayrow1[col_Num] << " ";
    }
    cout << endl;
    row_Num++;

    for (int col_Num = 0; col_Num < size; col_Num++)
    {
        cout << arrayrow2[col_Num] << " ";
    }
    cout << endl;
    row_Num++;

    for (int col_Num = 0; col_Num < size; col_Num++)
    {
        cout << arrayrow3[col_Num] << " ";
    }
    cout << endl;
}



bool checkRange(int arrayRow1[], int arrayRow2[], int intarrayRow3[], int size, int min, int max)
{
    bool value = true;

    for (int colNum = 0; colNum < COLS; colNum++)
    {
        if (arrayRow1[colNum]< min || arrayRow1[colNum] > max)
        {
            value = false;
        }

        else if (arrayRow2[colNum] < min || arrayRow2[colNum] > max)
        {
            value = false;
        }

        else if (intarrayRow3[colNum] < min || intarrayRow3[colNum] > max)
        {
            value = false;
        }
    }
    return value;
}


bool checkUnique(int arrayRow1[], int arrayRow2[], int intarrayRow3[], int size)
{
    int x = 0, y = 0, z = 0;

    const int MIN = 1;
    bool value = true;

    while (x < (arrayRow1[0] / arrayRow1[0]) && y < (arrayRow2[0] / arrayRow2[0]) && z < (intarrayRow3[0] / intarrayRow3[0]))
    {
        if ((arrayRow1[x] == arrayRow2[y]) && (arrayRow2[y] == intarrayRow3[z]))
        {
            if (x > MIN)
            {
                value = false;
            }

            x++; y++; z++;
        }

        else if (arrayRow1[x] < arrayRow2[y])
            x++;

        else if (arrayRow2[y] < intarrayRow3[z])
            y++;

        else
            z++;
    }
    return value;
}

bool checkRowSum(int arrayrow1[], int arrayrow2[], int intarrayrow3[], int size)
{
    bool value = true;
    int sumRow1 = arrayrow1[0] + arrayrow1[1] + arrayrow1[2];

    int sumRow2 = arrayrow2[0] + arrayrow2[1] + arrayrow2[2];

    int sumRow3 = intarrayrow3[0] + intarrayrow3[1] + intarrayrow3[2];

    if ((sumRow1 != sumRow2) || (sumRow1 != sumRow3) || (sumRow3 != sumRow2))
    {
        value = false;
    }
    return value;
}



bool checkColSum(int arrayrow1[], int arrayrow2[], int intarrayrow3[], int size)
{
    bool value = true;
    int colsum1 = arrayrow1[0] + arrayrow2[0] + intarrayrow3[0];
    int colsum2 = arrayrow1[1] + arrayrow2[1] + intarrayrow3[1];

    int colsum3 = arrayrow1[2] + arrayrow2[2] + intarrayrow3[2];

    if ((colsum1 != colsum2) || (colsum1 != colsum3) || (colsum2 != colsum3))
    {
        value = false;
    }
    return value;

}

bool checkDiagSum(int arrayrow1[], int arrayrow2[], int arrayrow3[], int size)
{
    bool value = true;
    int diagsum1 = arrayrow1[0] + arrayrow2[1] + arrayrow3[2];

    int diagsum2 = arrayrow1[2] + arrayrow2[1] + arrayrow3[0];

    if (diagsum1 != diagsum2)
    {
        value = false;
    }
    return value;
}

bool isMagicSquare(int arrayRow1[], int arrayRow2[], int intarrayRow3[], int size)
{
    bool value = false;
    bool range = checkRange(arrayRow1, arrayRow2, intarrayRow3, size, MIN, MAX);

    bool unique = checkUnique(arrayRow1, arrayRow2, intarrayRow3, size);
    bool row = checkRowSum(arrayRow1, arrayRow2, intarrayRow3, size);

    bool col = checkColSum(arrayRow1, arrayRow2, intarrayRow3, size);

    bool diag = checkDiagSum(arrayRow1, arrayRow2, intarrayRow3, size);

    if (range && unique && row && col && diag)
    {
        value = true;
    }

    return value;
}
