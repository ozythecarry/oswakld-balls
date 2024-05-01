

import turtle


wn = turtle.Screen()
wn.title("Keep the ball up")
wn.bgcolor("black")
wn.setup(width=800, height=600)
wn.tracer(0)

# Score
score = 0
def reset_score():
    global score
    score = 0
    turtle.clear()  # Clear previous score
    turtle.write("Score: {}".format(score), align="center", font=("Arial", 24, "normal"))



# Paddle at bottom
paddle = turtle.Turtle()
paddle.speed(0)
paddle.shape("square")
paddle.color("red")
paddle.shapesize(stretch_wid=1,stretch_len=5 )
paddle.penup()
paddle.goto(0,-250)

# Ball
ball = turtle.Turtle()
ball.speed(0)
ball.shape("circle")
ball.color("white")
ball.penup()
ball.goto(0, 0)
ball.dx = 0.15
ball.dy = -0.13


# Pen
pen = turtle.Turtle()
pen.speed(0)
pen.color("Yellow")
pen.penup()
pen.hideturtle()
pen.goto(0,260)
pen.write("Your score: 0", align="center",font=("Courier", 24, "normal"))


# Functions
def paddle_left():
    x = paddle.xcor()
    x -= 20
    paddle.setx(x)



def paddle_right():
    x = paddle.xcor()
    x += 20
    paddle.setx(x)



# Keyboard binding
wn.listen()
wn.onkeypress(paddle_left, "Left")
wn.onkeypress(paddle_right,"Right")




# main game loop
while True:
    wn.update()

    # Moving the ball
    ball.setx(ball.xcor() + ball.dx)
    ball.sety(ball.ycor() + ball.dy)

    # Border
    if ball.ycor() > 290:
        ball.sety(290)
        ball.dy *= -1

    if ball.ycor() < -270:
        ball.goto(0,0)
        ball.dy *= -1



    if ball.xcor() > 380:
        ball.setx(380)
        ball.dx *= -1


    if ball.xcor() < -380:
        ball.setx(-380)
        ball.dx *= -1

    # Paddle collisions
    if (ball.ycor() < -240 and ball.ycor() > -250) and (
            ball.xcor() < paddle.xcor() + 50 and ball.xcor() > paddle.xcor() - 50):
        ball.sety(-235)
        ball.dy *= -1
        score += 1
        pen.clear()
        pen.write("Your score: {}".format(score), align="center", font=("Courier", 24, "normal"))

    if ball.ycor() < -260:
        pen.clear()
        pen.write("Your score: 0", align="center",font=("Courier", 24, "normal"))

