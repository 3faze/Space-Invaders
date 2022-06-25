```
import pygame
import time
import random
import os

pygame.init()

backgroundcolor = (18, 41, 77)#Dark Blue

#Screen Size
WIDTH = 750
HEIGHT = 750

#Setting up the screen
SC = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Space Invaders by 3faze")

clock = pygame.time.Clock()

def main():
    gameover = False
    while not gameover:
        SC.fill(backgroundcolor)
        pygame.display.update()


        for event in pygame.event.get():
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_a:
                    
```
