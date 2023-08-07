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
## 6. Anonymous unions in C
```c
typedef struct CustomFloat
{
	bool isExtended; // caso Extended seja verdadeiro
	union { // Os variaveis encontram-se no mesmo endereco
		float value;
		double valueExtended;
	};
} CostomFloat;

int	main(void)
{
	CustomFloat cf, cf2;
	cf.isExtended = false;
	cf.value = 12.5f;

	cf2.isExtended = true;
	cf2.valueExtended = 0.25;

	printf("%f %lf\n", cf.value, cf2.valueExtended); // 12.500000 0.250000
	printf("%f %lf\n", cf.value, cf2.valueExtended); // 023FE48 023FE48
	printf("%llu\n", sizeof(CustomFloat)); // 16 (4 bytes float + 8 bytes double)
	return (0);
}
