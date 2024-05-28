# The-Pong-Game

1. Create the screen
2. Create and move a paddle
3. Create another paddle
4. Create the ball and make it move
5. Detect collision with wall and bounce
6. Detect collision with paddle
7. Detect when paddle misses
8. keep score



Create the screen(main.py)
   
            from turtle import Screen 
            screen = Screen()
            screen.title("The Pong Game")
            screen.setup(width=800,height=600)
            screen.bgcolor("black")
            screen.exitonclick()
   
Create and move a paddle(paddle.py)
   
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

Create another paddle(main.py)
  
            screen.tracer(0)  # to turn off the animation but if you turn off then nothing will display therefore we have to call update method.
      
            l_paddle = Paddle((350,0))
            r_paddle = Paddle((-350,0))
      
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

Create the ball and make it move(ball.py)
    
                  from turtle import Turtle
                  class Ball(Turtle):
                  
                      def __init__(self):
                          super().__init__()
                          self.shape("circle")   
                          self.color("white")
                          self.penup()
                          self.x_move =10
                          self.y_move =10
                          
                  
                      def move(self):
                          new_x = self.xcor() + self.x_move 
                          new_y = self.ycor()  +self.y_move 
                          self.goto(new_x,new_y)

Detect collision with wall and bounce
       
              (ball.py) def bounce_y(self):
                          self.y_move *= -1 #Upward and Downward bounce
       
              (main.py)   #Detect collision with wall
                              if ball.ycor() > 280 or ball.ycor() < -280:
                                  #ball needs to bounce
                                  ball.bounce_y()

Detect collision with paddle

   
        (ball.py)     def bounce_x(self):
                          self.x_move *= -1 #left and right bounce
       
        (main.py)  #Detect the collision with paddle
                          if ball.distance(r_paddle) < 50 and ball.xcor() > 320 or ball.distance(l_paddle) < 50 and ball.xcor() < -320 :
                               ball.bounce_x()

Detect when paddle misses
   
               (ball.py) def reset_position(self):
                                self.goto(0,0)
                                self.bounce_x()

               #Detect when the  R paddle misses
                if ball.xcor() > 380:
                    ball.reset_position()
                    scoreboard.l_point()  # To increase score of left side player
                #Detect when the  L paddle misses
                if ball.xcor() < -380:
                    ball.reset_position()
                    scoreboard.r_point()  # To increase score of right side player

keep score(scoreboard.py)

            from turtle import Turtle
            
            class ScoreBoard(Turtle):
            
                def __init__(self):
                    super().__init__()
                    self.color("white")
                    self.penup()
                    self.hideturtle()
                    self.l_score = 0
                    self.r_score = 0
                    self.update_scoreboard()
                   
                def update_scoreboard(self):
                    self.clear()
                    self.goto(-100,200)
                    self.write(self.l_score,align="center", font=("Courier",80,"normal"))
                    self.goto(100,200)
                    self.write(self.r_score,align="center", font=("Courier",80,"normal"))
            
            
                def l_point(self):
                    self.l_score +=1
                    self.update_scoreboard()
            
                def r_point(self):
                    self.r_score +=1
                    self.update_scoreboard()

OUTPUTS:

![image](https://github.com/Ashvini8879/The-Pong-Game/assets/170402064/c84aac82-39bc-43b4-a6dd-b793c254d8d7)

![image](https://github.com/Ashvini8879/The-Pong-Game/assets/170402064/9c6b66d4-86ea-40c9-ab05-77b844a76f31)




   
