```
import pygame
import time
 
pygame.init()
 
white = (255, 255, 255)
blue = (0, 0, 125)
black = (0, 0, 0)
red = (255, 0, 0)
yellow = (255, 179, 0)

dis_height = 600
dis_width = 800

dis = pygame.display.set_mode((dis_width, dis_height))
pygame.display.set_caption('Space Invaders')
font_style = pygame.font.SysFont(None, 100)

cooldown = 2

game_finished = False
 
x1 = 800 / 2
y1 = 600 / 2

x1e = 800 / 2
y1e = 100

xb = x1
yb = y1 - 30

x1_change = 0       
y1_change = 0

clock = pygame.time.Clock()

def message_render(msg, color):
    mesg = font_style.render(msg, True, color)
    dis.blit(mesg, [dis_width / 2 - 150, dis_height / 2 - 50])

while not game_finished:
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
        y1, x1, x1e, y1e = 1000, 1000, 1000, 1000
        print("Game Won.")
        game_finished = True
    dis.fill(blue)
    pygame.draw.rect(dis, white, [x1, y1, 30, 30])
    pygame.draw.rect(dis, black, [x1e, y1e, 30, 30])
 
    pygame.display.update()
 
    clock.tick(30)

message_render("You Won!", yellow)
pygame.display.update()
time.sleep(4)
 
pygame.quit()
quit()        
```
