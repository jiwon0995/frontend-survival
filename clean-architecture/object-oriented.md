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

C++ 컴파일러는 클래스의 인스턴스 크기를 알 수 있어야 하기 때문에 다음과 같이 코드를 작성한다.

```c++
// point.h
class Point {
public:
    Point(double x, double y);
    double distance(const Point& p) const;

private:
    double x;
    double y;
};

// point.cc
#include "point.h"
#include <math.h>

Point::Point(double x, double y) : x(x), y(y) {}

double Point::distance(const Point& p) const {
    double dx = x-p.x;
    double dy = y-p.y;
    return sqrt(dx*dx + dy*dy)
}
```

C++ 코드에서는 point.h 헤더 파일을 사용하는 측에서 멤버 변수 x, y를 알게 된다. 멤버 변수 이름이 바뀌면 사용하는 측에서도 변경해야 한다. 이는 캡슐화가 깨진 것이다. 많은 객체 지향 언어가 캡슐화를 강제하지 않는다.

***상속(Inheritance)***
상속은 변수와 함수를 하나의 유효 범위로 묶어서 재정의 하는 것을 말한다.

namedPoint.h

```c
// namedPoint.h
struct NamedPoint;

struct NamedPoint* makeNamedPoint(double x, double y, const char* name);
void setName(struct NamedPoint* np, const char* name);
char* getName(struct NamedPoint* np);

// namedPoint.c
#include "namedPoint.h"
#include <stdlib.h>

struct NamedPoint {
   double x, y;
    char* name;
};

struct NamedPoint* makeNamedPoint(double x, double y, const char* name) {
    struct NamedPoint* p = malloc(sizeof(struct NamedPoint));
    p->x = x;
    p->y = y;
   p->name = name;
   return p;
}

void setName(struct NamedPoint* np, char* name) {
    np->name = name
}

char* getName(struct namedPoint* np) {
    return np->name;
}

// main.c
#include "point.h"
#include "namedPoint.h"
#include <stdio.h>

int main(int ac, char** av) {
    struct NamedPoint* origin = makeNamedPoint(0.0, 0.0, "origin");
    struct NamedPoint* upperRight = makeNamedPoint(1.0, 1.0, "upper right");
    printf("distance = %f\n", distance(origin, upperRight));
}
```

NamedPoint 데이터 구조가 Point 데이터 구조로부터 파생된 구조처럼 동작한다.
NamedPoint가 Point를 포함하는 상위 집합으로, NamedPoint는 Point의 모든 멤버를 포함한다.
이 방법으로 단일 상속을 구현할 수 있지만 다중 상속을 구현하기는 어렵다.

***다형성***

객체 지향 언어에서 다형성은 안전하고 편리하게 제공한다는 것은 소스 코드 의존성을 역전시킨다는 것이다.
호출하는 모듈이든 호출되는 모듈이든 관계없이 소스 코드 의존성을 원하는 방향으로 설정할 수 있다.

다형성 너무 어려워서 반복 학습 필요
[참고](https://www.codestates.com/blog/content/%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%8A%B9%EC%A7%95)
