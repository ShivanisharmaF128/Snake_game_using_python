# 🐍 Snake Game Using Python (Pygame)
A classic Snake Game built using Python and the Pygame library. Simple, addictive, and fun — this project is perfect for Python beginners to learn about game development, logic building, and using graphics libraries.

![snake game](https://github.com/ShivanisharmaF128/Snake_game_using_python/blob/main/snake%20game.png)

---

---

## 📌 Objective
To recreate the traditional Snake Game using Python and Pygame, providing a fun way to learn about game loops, event handling, and real-time graphics.

---

## 📝 Overview
-🎮 Arrow-key controlled snake movement
-🍎 Randomly spawning food
-🧠 Score tracking and game over logic
-💥 Self-collision detection
-🔁 Easy to restart and play again
-📦 Beginner-friendly and fully customizable

---
## Code
```sh
import pygame
import time
import random

pygame.init()

# Define colors
colour_black = (0, 0, 0)
colour_white = (255, 255, 255)
colour_red = (255, 0, 0)
colour_green = (0, 255, 0)

# Screen dimensions
box_len = 800
box_height = 600

add_caption = pygame.display.set_mode((box_len, box_height))
pygame.display.set_caption("SNAKE GAME")

timer = pygame.time.Clock()

snake_block = 10
snake_speed = 15

display_style = pygame.font.SysFont("Elephant", 30, bold=True)
score_font = pygame.font.SysFont("Elephant", 35, bold=True)

def final_score(score):
    value = score_font.render(f"Score: {score}", True, colour_white)
    add_caption.blit(value, [10, 10])

def make_snake(snake_block, list_snake):
    for x in list_snake:
        pygame.draw.rect(add_caption, colour_green, [x[0], x[1], snake_block, snake_block])

def display_msg(msg, colour):
    mssg = display_style.render(msg, True, colour)
    text_rect = mssg.get_rect(center=(box_len / 2, box_height / 2))
    add_caption.blit(mssg, text_rect)

def game_start():
    global snake_block  # Fix for UnboundLocalError
    
    game_over = False
    game_close = False

    value_x1 = box_len / 2
    value_y1 = box_height / 2

    new_x1 = 0
    new_y1 = 0

    list_snake = []
    snake_len = 1

    foodx_pos = round(random.randrange(0, box_len - snake_block) / 10.0) * 10.0
    foody_pos = round(random.randrange(0, box_height - snake_block) / 10.0) * 10.0

    while not game_over:
        while game_close:
            add_caption.fill(colour_black)
            display_msg("YOU LOST! Press C to Play Again or Q to Quit", colour_white)
            pygame.display.update()

            for event in pygame.event.get():
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_q:
                        game_over = True
                        game_close = False
                    if event.key == pygame.K_c:
                        game_start()

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over = True
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_LEFT:
                    new_x1 = -snake_block
                    new_y1 = 0
                elif event.key == pygame.K_RIGHT:
                    new_x1 = snake_block
                    new_y1 = 0
                elif event.key == pygame.K_UP:
                    new_y1 = -snake_block
                    new_x1 = 0
                elif event.key == pygame.K_DOWN:
                    new_y1 = snake_block
                    new_x1 = 0

        if value_x1 >= box_len or value_x1 < 0 or value_y1 >= box_height or value_y1 < 0:
            game_close = True

        value_x1 += new_x1
        value_y1 += new_y1
        add_caption.fill(colour_black)
        pygame.draw.rect(add_caption, colour_red, [foodx_pos, foody_pos, snake_block, snake_block])

        snake_head = [value_x1, value_y1]
        list_snake.append(snake_head)
        if len(list_snake) > snake_len:
            del list_snake[0]

        for x in list_snake[:-1]:
            if x == snake_head:
                game_close = True

        make_snake(snake_block, list_snake)
        final_score(snake_len - 1)
        pygame.display.update()

        if value_x1 == foodx_pos and value_y1 == foody_pos:
            foodx_pos = round(random.randrange(0, box_len - snake_block) / 10.0) * 10.0
            foody_pos = round(random.randrange(0, box_height - snake_block) / 10.0) * 10.0
            snake_len += 1
            snake_block += 1  # Increase the snake size

        timer.tick(snake_speed)

    pygame.quit()
    quit()

game_start()

```
---
## 📜 Code Explanation

-Game loops and screen updates
-Keyboard event handling
-Drawing shapes and objects
-Collision detection
-score tracking and logic
-Restarting the game on death

---

## 📢 Conclusion

This project is a fun and interactive way to learn game development in Python using Pygame. It reinforces important programming concepts and provides a solid foundation for building more advanced games.

🌟 If you found this useful, don’t forget to star the repo!
---
### 🤝 Contribution
Contributions are always welcome!
If you want to improve the UI or add new features, follow these steps:

- Fork this repository 📌
- Make necessary changes 🛠️
- Create a pull request 🔄

----


## 👨‍💻 Author

  Shivani Sharma
  
📌 Passionate about Python, Data Science, and GUI Development.

🌐 Connectact : shivanisharmaf128@gail.com 
