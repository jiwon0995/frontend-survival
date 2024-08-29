# 객체 지향

프로그래밍을 배우면서 '객체 지향 프로그래밍' 이란 말을 정말 많이 들었다.
여전히 어려운 개념이지만 해당 글을 읽고 조금은 이해 할 수 있었다.
객체 지향 프로그래밍이 나온 흐름과 왜 중요한지 쉽게 설명해주는 글이니 한번 읽어보는걸 추천한다.

👉 [추천글 | 객체 지향 프로그래밍](https://velog.io/@teo/oop)

그렇다면 클린 아키텍처에 설명된 객체 지향 프로그래밍에 대해 정리를 해보자.

## 객체 지향 프로그래밍의 요소

***캡슐화(Encapsulation)***
캡슐화는 객체의 일부 함수나 변수를 외부에서 접근하지 못하도록 구분하는 것을 말한다.
객체 지향 언어에서는 캡슐화 개념을 클래스의 private 멤버 데이터와와 public 멤버 함수로 표현한다.

간단한 C 언어 예제

```c
// point.h
struct Point;
struct Point* makePoint(double x, double y);
double distance (struct Point *p1, struct Point *p2);
```

```c
#include "point.h"
#include <stdlib.h>
#include <math.h>

struct Point {
    double x, y;
};

struct Point* makepoint(double x, double y) {
    strict Point* p = malloc(sizeof(struct Point));
    p->x = x;
    p->y = y;
    return p;
}

double distance(struct Point* p1, struct Point* p2) {
    double dx = p1->x - p2->x;
    double dy = p1->y - p2->y;
    return sqrt(dx*dx+dy*dy);
}
```
