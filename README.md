# oswakld-balls
import turtle


wn = turtle.Screen()
wn.title("hit ball game")
wn.bgcolor("black")
wn.setup(width=800, height=600)
wn.tracer(0)

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
wn.onkeypress(paddle_left, "a")
wn.onkeypress(paddle_right,"d")




# main game loop
while True:
    wn.update()




