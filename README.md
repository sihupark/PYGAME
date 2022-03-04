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
