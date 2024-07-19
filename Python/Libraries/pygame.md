Cheatsheet for Pygame
---------------------
A collection of Notes for the Pygame module in Python  


Initial Setup
-------------
```
pygame.init()
screen = pygame.display.set_mode((x,y))
pygame.display.set_caption('Super Tux Python World')
clock = pygame.time.Clock()
test_font = pygame.font.Font('font type, leave None for default', fontsize)
```

Add Music
---------
```
pygame.mixer.music.load('freesoftwaresong.mp3')
pygame.mixer.music.play()
```

Adding Images and Setting Them in The Grid
------------------------------------------
```
bg_surface = pygame.image.load('gamebackground.png').convert()
text_surface = test_font.render('Super Tux: The Python Adventures', False, 'Yellow')
tux_surface = pygame.image.load('yourimage.png').convert_alpha()
enemy_surface = pygame.image.load('enemyimage.png').convert_alpha()

while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            exit()

    screen.blit(bg_surface,(0,0))
    screen.blit(tux_surface,(tux_x_pos,tux_y_pos))
    screen.blit(text_surface,(250,150))
    screen.blit(enemy_surface,(enemy_x_pos, 742))
```

Add WASD Character Movements
----------------------------
```
    keys = pygame.key.get_pressed()
    if keys[pygame.K_w]:
        #tux_y_pos -= 4
    if keys[pygame.K_s]:
        #tux_y_pos += 4
    if keys[pygame.K_a]:
        tux_x_pos -= 4
    if keys[pygame.K_d]:
        tux_x_pos += 4
```

Run Game at 60 FPS
------------------
```
    pygame.display.update()
    clock.tick(60)
```
