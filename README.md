# PYGAME

## 타이머 만들기
```PYTHON
import sys
import pygame
from pygame.locals import QUIT

pygame.init()
SURFACE = pygame.display.set_mode((400, 300))
FPSCLOCK = pygame.time.Clock()

def main():
    sysfont = pygame.font.SysFont(None, 36)
    counter = 0
    while True:
        for event in pygame.event.get():
            if event.type == QUIT:
                pygame.quit()
                sys.exit()

        counter += 1
        SURFACE.fill((0, 0, 0))
        count_image = sysfont.render("count is {}".format(counter), True, (225, 225, 225))
        SURFACE.blit(count_image, (50, 50))
        pygame.display.update()
        FPSCLOCK.tick(10)

if __name__== '__main__':
    main()

- SURFACE = pygame.display.set_mode((400, 300))에 set_mode는 윈도우 화면 크기
- set_caption은 화면 타이틀을 정해주는 것
- .fill은 화면의 RGB를 나타냄
- event는 하나의 어떤 event이다. 마우스 클릭도 event, 마우스 움직이는 것도 event인 것처럼
```

## Rect
```
- PyGame에서 직사각형(위치와 크기)을 지정할 때 사용하는 클래스이다.
(다른 언어 라이브러리에서도 직사각형을 다루는 클래스는 많이 있지만 PyGame의 Rect 클래스가 기본적으로 사용하기 쉬움)

***** Rect 객체 만드는 방법 *****
다음의 방법으로 생성
- Rect(left, top, width, height)
- Rect((left, top), (width, height))
left는 왼쪽 가장자리의 x 좌표, top은 위쪽 끝의 y 좌표, width는 폭, height는 높이 이다.
********************************

****** Rect 클래스에서 사용할 수 있는 프로퍼터 ******
x, y, top, left, bottom, right
topleft, bottomleft, topright, bottomright
midtop, midleft, midbottom, midright
center, centerx, centery
size, , width, height, w, h
**************************************************
```

## Rect클래스의 주요 메서드
```
copy()  =  Rect 객체를 복제한다.
move(x, y)  =  (x, y) 이동한 Rect를 반환한다. 자신은 이동X
move_ip(x, y)  =  자신(Rect)을 (x, y)  이동
inflate(x, y)  =  현재값에서 (x, y)만큼 크기를 변경한 Rect를 반환.
inflate_ip(x, y)  =  자신의 사이즈를 (x, y)만큼 변경
union(Rect)  =  자신의 인수의 Rect를 포함하는 최소 Rect를 반환
contains(Rect)  =  인수의 Rect를 포함하는지 아닌지 여부를 반환
collidepoint(x, y)  =  (x,y)라는점이 자신에게 포함되는지 아닌지 여부를 반환
colliderect(Rect) Rect와 자신에게 겹침이 있는지 없는지(충돌)를 반환
```

## 직사각형
```
화면에 그리려면 draw클래스의 메서드를 사용한다. 직사각형을 그리는 메서드 rect의 정의는 다음과 같다. 직사각형을 나타내는 Rect, 직사각형을 그리는 rect, 헷갈리기 쉽기 때문에 주의

rect(Surface, color, Rect, width=0) -> Rect
Surface: 그리는 대상이 되는 화면(Surface객체)
color:색
Rect: 직사각형의 위치와 크기
width: 선 폭(생략할 때는 빈틈없이 칠한다.)
```
```PYTHON
import sys
import pygame
from pygame.locals import QUIT, Rect

pygame.init()
SURFACE = pygame.display.set_mode((400, 300))
FPSCLOCK = pygame.time.Clock()

def main():
    while True:
        for event in pygame.event.get():
            if event.type == QUIT:
                pygame.quit()
                sys.exit()

        SURFACE.fill((255, 255, 255))

        pygame.draw.rect(SURFACE, (255, 0, 0), (10, 20, 100, 50))

        pygame.draw.rect(SURFACE, (255, 0, 0), (150, 10, 100, 30), 3)

        pygame.draw.rect(SURFACE, (0, 255, 0), ((100, 80), (80, 50)))

        rect0 = Rect(200, 60, 140, 80)
        pygame.draw.rect(SURFACE, (0, 0, 255), rect0)

        rect1 = Rect((30, 160), (100, 50))
        pygame.draw.rect(SURFACE, (255, 255, 0), rect1)

        pygame.display.update()
        FPSCLOCK.tick(3)

if __name__ == '__main__':
    main()
```
