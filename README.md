```
import pygame
import time
 
pygame.init()
 
white = (255, 255, 255)
blue = (0, 0, 125)
black = (0, 0, 0)
red = (255, 0, 0)

dis = pygame.display.set_mode((800, 600))
pygame.display.set_caption('Space Invaders')

cooldown = 2

game_over = False
 
x1 = 800 / 2
y1 = 600 / 2

x1e = 800 / 2
y1e = 100

xb = x1
yb = y1 - 30

x1_change = 0       
y1_change = 0

clock = pygame.time.Clock()

while not game_over:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_LEFT:
                x1_change = -25
                y1_change = 0
                x1 += x1_change
                y1 += y1_change
            elif event.key == pygame.K_RIGHT:
                x1_change = 25
                y1_change = 0
                x1 += x1_change
                y1 += y1_change
            elif event.key == pygame.K_UP:
                y1_change = -25
                x1_change = 0
                x1 += x1_change
                y1 += y1_change
            elif event.key == pygame.K_DOWN:
                y1_change = 25
                x1_change = 0
                x1 += x1_change
                y1 += y1_change
            elif event.key == pygame.K_k:
                out = False
                run = True
                print("Bullet out of the screen.")
                if out == True:
                            time.sleep(cooldown)
                while run == True:
                    if yb >= 0:
                        pygame.draw.rect(dis, black, [xb + 10, yb, 10, 30])
                        yb = yb - 40
                        pygame.display.update()
                        print("Shoot. " + str(yb))
                    else:
                        break
                        out = True
                        run = False
    if x1e >= 800:
        print("Enemy out of the screen")
        x1e = 0
    else:
        x1e = x1e + 20
    if yb <= y1e and xb == x1e:
        print("Target Shot.")
        yb = y1 - 30
        xb = x1
        y1e = 1000
        x1e = 1000
        print("Game Won.")
        game_over = True
    dis.fill(blue)
    pygame.draw.rect(dis, white, [x1, y1, 30, 30])
    pygame.draw.rect(dis, black, [x1e, y1e, 30, 30])
 
    pygame.display.update()
 
    clock.tick(30)
 
pygame.quit()
quit()
                
```
