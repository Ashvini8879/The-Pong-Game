# The-Pong-Game

1. Create the screen
2. Create and move a paddle
3. Create another paddle
4. Create the ball and make it move
5. Detect collision with wall and bounce
6. Detect collision with paddle
7. Detect when paddle misses
8. keep score

PongGame.py
_____________________________________________________________________________
      
        from turtle import Screen 
        from paddle import Paddle
        from ball import Ball
        import time
        
        screen = Screen()
        
        l_paddle = Paddle((350,0))
        r_paddle = Paddle((-350,0))
        
        ball = Ball()
        
        screen.tracer(0)  # to turn off the animation but if you turn off then 
        nothing will display therefore we have to call update method.
        
        # Create the screen
        screen.title("The Pong Game")
        screen.setup(width=800,height=600)
        screen.bgcolor("black")
        
        # Create and move a paddle
        screen.listen()
        screen.onkey(r_paddle.Up,"Up")
        screen.onkey(r_paddle.Down,"Down")
        
        screen.onkey(l_paddle.Up,"w")  #to go up
        screen.onkey(l_paddle.Down,"s") #to go down
        
        game_is_on = True
        
        while game_is_on:
            time.sleep(0.1) #to slow down the ball animation
            screen.update()
            ball.move()
        
        screen.exitonclick()

paddle.py
____________________________________________________________________________
      from turtle import Turtle
      class Paddle(Turtle):
    
        def __init__(self,position):
            super().__init__()
            self.shape("square")
            self.color("white")
            self.shapesize(stretch_wid=5,stretch_len=1)
            self.penup()
            self.goto(position)
    
        def Up(self):
            new_y = self.ycor() + 20
            self.goto(self.xcor(),new_y)
    
        def Down(self):
            new_y = self.ycor() - 20
            self.goto(self.xcor(),new_y)

ball.py
____________________________________________________________________________
      from turtle import Turtle
      class Ball(Turtle):
    
        def __init__(self):
            super().__init__()
            self.shape("circle")   
            self.color("white")
            self.penup()
            
    
        def move(self):
            new_x = self.xcor() + 10
            new_y = self.ycor()  +10
            self.goto(new_x,new_y)




       
