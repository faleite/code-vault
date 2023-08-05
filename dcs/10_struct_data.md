## 3. How to return and pass a struct to a function
```c
#include <stdio.h>
#include <stdlib.h>

// 2. Simples data type (tipo de dados)
typedef struct point
{
	double x, y;
} point;

// 2. Passando a struct para uma função
/*
point	*getMiddlePoint(const point *a, const point *b)
{
	point *m; // declarção de variavel struct m

	m = malloc(sizeof(point));
	m->x = (a->x + b->x) / 2;
	m->y = (a->y + b->y) / 2;
	return (m);
}
*/

void	getMiddlePoint(const point *a, const point *b, point *out)
{
	out->x = (a->x + b->x) / 2;
	out->y = (a->y + b->y) / 2;
}
// 1.
int	main(int argc, char *argv[])
{
	point p1 = {
		.x = 1,
		.y = 1
	};
	point p2 = {
		.x = 3,
		.y = 2
	};
	/*
	point *middle; // declarção de variavel struct
	middle = getMiddlePoint(&p1, &p2);
	printf("%lf, %lf\n", middle->x, middle->y);
	free(middle);
	*/
	point middle; // declarção de variavel struct
	getMiddlePoint(&p1, &p2, &middle);
	printf("%lf, %lf\n", middle.x, middle.y);
	return (0);
}
```
