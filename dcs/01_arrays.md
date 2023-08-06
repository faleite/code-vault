## 4. Iterating over main parts of a matrix
```c
#include <stdio.h>

int	main(void)
{
	int	matrix[5][5] = {
	//Col 0  1  2  3  4
		{ 1, 1, 1, 1, 1}, //lin 0
		{ 2, 2, 2, 2, 2}, //    1
		{ 3, 3, 3, 3, 3}, //    2
		{ 1, 2, 3, 4, 5}, //    3
		{ 1, 2, 3, 4, 5}, //    4
	};
	int	i;
	int j;
	int n = 5;

	/* Diagonal impressão*/
	// i = 0;
	// while (i < n)
	// {
	// 	printf("%d ", matrix[i][i]); // print Col0, Lin0, Col1 Lin1, Col2 Lin2...
	// 	i++;
	// }

	/* Diagonal impressão e outras formas */
	i = 0;
	while (i < n)
	{
		j = 0;
		while (j < n)
		{
			if (i + j == n - 1) // print Col4, Lin0, Col3 Lin1, Col2 Lin2...
			/*          1
                      2
					3
				  2
			    1 */
			// if (i == j) // print Col0, Lin0, Col1 Lin1, Col2 Lin2...
			/* 1
			     2
		   		   3
				     4
			   		   5 */
			/* then try this */
			// if (i < j)
			/*
			1 1 1 1
			2 2 2
			3 3
			5
			 */
			// if (i > j)
			/*
			2
			3 3
			1 2 3
			1 2 3 4
			*/
			// if (j > i && j < n - i - 1)
			/*
			1 1 1
			2
			*/
			// if (j < i && j > n - i - 1)
				printf("%d ", matrix[i][j]);
			j++;
		}
		i++;
		printf("\n");
	}
	return (0);
}
```
