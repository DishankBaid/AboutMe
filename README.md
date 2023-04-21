# AboutMe

👋 Hi, I'm Dishank, a competitive programmer and front-end developer with a passion for building fast, responsive, and user-friendly web applications.

🚀 I've been programming since 2019 and have competed in numerous programming contests, including codechef starters and codeforces contests. My experience in competitive programming has improved my problem-solving skills and made me better in writing efficient and maintainable code.

💻 In my day-to-day work, I specialize in front-end development using React, Redux, and other modern web technologies. I have experience building scalable and modular web applications, designing user interfaces, and optimizing performance.

🤝 I'm always open to collaborating on interesting projects and contributing to open-source software. Feel free to reach out to me on LinkedIn or via email at dishankbaid9783@gmail.com.


```python


import pygame
import random

# Initialize Pygame
pygame.init()

# Set up the game window
WINDOW_WIDTH = 640
WINDOW_HEIGHT = 480
WINDOW_TITLE = "Snake Game"
GAME_SPEED = 10
FONT_SIZE = 30
FONT_COLOR = (255, 255, 255)
SCORE_POS = (10, 10)
FONT_STYLE = pygame.font.SysFont(None, FONT_SIZE)
screen = pygame.display.set_mode((WINDOW_WIDTH, WINDOW_HEIGHT))
pygame.display.set_caption(WINDOW_TITLE)

# Set up the game objects
snake_color = (0, 255, 0)
food_color = (255, 0, 0)
block_size = 10
snake_x = WINDOW_WIDTH / 2
snake_y = WINDOW_HEIGHT / 2
snake_speed = block_size
snake_length = 1
snake_segments = [(snake_x, snake_y)]
food_x = random.randrange(0, WINDOW_WIDTH - block_size, block_size)
food_y = random.randrange(0, WINDOW_HEIGHT - block_size, block_size)

# Set up the game loop
game_over = False
clock = pygame.time.Clock()

while not game_over:
    # Handle events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game_over = True

    # Handle keyboard input
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        snake_x -= snake_speed
    elif keys[pygame.K_RIGHT]:
        snake_x += snake_speed
    elif keys[pygame.K_UP]:
        snake_y -= snake_speed
    elif keys[pygame.K_DOWN]:
        snake_y += snake_speed

    # Check if the snake has hit the food
    if snake_x == food_x and snake_y == food_y:
        food_x = random.randrange(0, WINDOW_WIDTH - block_size, block_size)
        food_y = random.randrange(0, WINDOW_HEIGHT - block_size, block_size)
        snake_length += 1
        snake_segments.append((snake_x, snake_y))

    # Update the snake's position and length
    snake_segments.append((snake_x, snake_y))
    if len(snake_segments) > snake_length:
        del snake_segments[0]

    # Check if the snake has hit itself
    for segment in snake_segments[:-1]:
        if segment == (snake_x, snake_y):
            game_over = True

    # Draw the game objects
    screen.fill((0, 0, 0))
    for segment in snake_segments:
        pygame.draw.rect(screen, snake_color, (segment[0], segment[1], block_size, block_size))
    pygame.draw.rect(screen, food_color, (food_x, food_y, block_size, block_size))

    # Draw the score
    score_text = FONT_STYLE.render(f"Score: {snake_length-1}", True, FONT_COLOR)
    screen.blit(score_text, SCORE_POS)

    # Update the display and wait
    pygame.display.update()
    clock.tick(GAME_SPEED)

# Clean up
pygame.quit()


```

