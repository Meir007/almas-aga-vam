import random
from graphics import*
def main():

    board=[-1,1,1,-2,4,-3,0,1,0,2,-2,1,0,1,-4,3,0,0,0,2,0,-1,0,4,0,-3,0,-2,0,1,0,3]
    
    
    win=GraphWin("Monopoly",300,300)
    win.setCoords(0.0,0.0,3.0,4.0)
    Text(Point(1,5)," Positions:").draw(win)
    Text(Point(1,3)," Player 1").draw(win)
    Text(Point(1,1)," Player 2").draw(win)
    input=Entry(Point(2,3),5)
    input.setText("0.0")

    posA=0
    posB=0
    
    input.draw(win)
    input=Entry(Point(2,1),5)
    input.setText("0.0")
    input.draw(win)

    output=Text(Point(2,1),"")
    output.draw(win)
    button=Text(Point(1.5,2.0),"Throw dices")
    button.draw(win)
    #Rectangle(Point(0.75,1.5),Point(2.25,2.5)).draw(win)
    Rectangle(Point(1,1.5),Point(2,2.5)).draw(win)
    win.getMouse()

    while posA < 20 or posB < 20:
        #Brosanie kostei,slushainoe shislo ot 1 do 12
        p1=random.randint(2,12)
        random.seed(100)

        button.setText("%0.1d"%p1)
        p2=random.randint(2,12)
        random.seed(100)
        
        posA = p1 + posA + board[posA+p1]
        posB = p2+ posB + board[posB+p2]
        
        if posA<0:
           posA=0
        if posA>20:
           print "Igrok 1 Vigral"

        if posB<0:
           posB=0
        if posB>20:
           print "Igrok 2 Vigral"
        
        button.setText("%0.1d"%p2)
    
        input.setText(p1)
        print posA
        print posB

        win.getMouse()
    win.close()
main()    


