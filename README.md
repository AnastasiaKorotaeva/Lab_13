# Lab_13

#include "stdafx.h"
#include <iostream>
#include <iomanip> 
using namespace std;

int* newMatrix(int** matrix, int* N, int* M);
bool isAssimetriya(int* line, int* len);

int main()
{
	int N, M;
	cout << "N = ";
	cin >> N;
	cout << "M = ";
	cin >> M;

	int** matrix = new int*[N];
	for (int** i = matrix; i < matrix + N; i++)
	{
		*i = new int[M];
	}

	int kN = 0, kM = 0;
	for (int** i = matrix; i < matrix + N; i++)
	{
		kM = 0;
		for (int* j = *i; j < *i + M; j++)
		{
			cout << "a[" << kN << "][" << kM << "] = ";
			cin >> *j;
			kM++;
		}
		kN++;
	}
	cout << endl << "Matrix" << endl;
	for (int** i = matrix; i < matrix + N; i++)
	{
		for (int* j = *i; j < *i + M; j++)
		{
			cout << setw(3) << *j;
		}
		cout << endl;
	}

	int* array = newMatrix(matrix, &N, &M);
	cout << endl << "Array" << endl;
	for (int* i = array; i < array + N; i++)
	{
		cout << setw(3) << *i;
	}
	cout << endl;

	system("pause");
	return 0;
}

int* newMatrix(int** matrix, int* N, int* M)
{
	int* newMatrix = new int[*N];

	int k = 0;
	for (int** i = matrix; i < matrix + *N; i++)
	{
		newMatrix[k++] = isAssimetriya(*i, M);
	}

	return newMatrix;
}

bool isAssimetriya(int* line, int* len)
{
	for (int i = 0; i < *len / 2; i++)
	{
		if (line[i] != line[*len - i - 1])
		{
			return false;
		}
	}

	return true;
	system("pause");
}

