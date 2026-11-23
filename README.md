<h1>ExpNo 9: Solve Wumpus World Problem using Python demonstrating Inferences from Propositional Logic</h1> 
<h3>Name: Bhuvaneshwaran TU                      </h3>
<h3>Register Number/Staff Id:  212224040049         </h3>
<H3>Aim:</H3>
<p>
    To solve  Wumpus World Problem using Python demonstrating Inferences from Propositional Logic
</p>
<h1>Problem Description</h1>
<hr>
<h2>Wumpus World</h2>
<hr>
The Wumpus world is a simple world example to illustrate the worth of a knowledge-based agent and to represent knowledge representation.

The figure below shows a Wumpus world containing one pit and one Wumpus. There is an agent in room [1,1]. The goal of the agent is to exit the Wumpus world alive. The agent can exit the Wumpus world by reaching room [4,4]. The wumpus world contains exactly one Wumpus and one pit. There will be a breeze in the rooms adjacent to the pit, and there will be a stench in the rooms adjacent to Wumpus.

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/cd6b68dc-c79f-4dcb-8126-04da90d65912)

<center>Wumpus World Representation</center>
<p>
This is a python program that uses propositional logic sentences to check which rooms are safe. 

It is assumed that there will always be a safe path that the agent can take to exit the Wumpus world. The logical agent can take four actions: Up, Down, Left and Right. These actions help the agent move from one room to an adjacent room. The agent can perceive two things: Breeze and Stench.
</p>

<hr>
<h1>Sample Input and Output:</h1>
<hr>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8696111a-a4a7-47cb-ba4b-43a4ef88573f)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/4be5bf06-79fa-4fa0-9334-38a33f06060b)

<h2>Program : </h2>

```

# WUMPUS WORLD

wumpus = [
    ["Save", "Breeze", "PIT", "Breeze"],
    ["Smell", "Save", "Breeze", "Save"],
    ["WUMPUS", "GOLD", "PIT", "Breeze"],
    ["Smell", "Save", "Breeze", "PIT"]
]

# Initial Variables
row = 0
column = 0
arrow = True
player = True
score = 0

print("WELCOME TO WUMPUS WORLD")
print("Starting position:", row, column)
print("Current location:", wumpus[row][column])

while player:

    choice = input(
        "\nPress u to move up"
        "\nPress d to move down"
        "\nPress l to move left"
        "\nPress r to move right"
        "\nEnter your choice: "
    ).lower()

    # Player Movement
    if choice == "u":
        if row != 0:
            row -= 1
        else:
            print("Move denied")

    elif choice == "d":
        if row != 3:
            row += 1
        else:
            print("Move denied")

    elif choice == "l":
        if column != 0:
            column -= 1
        else:
            print("Move denied")

    elif choice == "r":
        if column != 3:
            column += 1
        else:
            print("Move denied")

    else:
        print("Invalid choice")
        continue

    print("Current location:", wumpus[row][column])

    # Throwing Arrow
    if wumpus[row][column] == "Smell" and arrow:

        arrow_choice = input(
            "Do you want to throw an arrow?\n"
            "Press y to throw\n"
            "Press n to save your arrow\n"
        ).lower()

        if arrow_choice == "y":

            arrow_throw = input(
                "Press u to throw up\n"
                "Press d to throw down\n"
                "Press l to throw left\n"
                "Press r to throw right\n"
            ).lower()

            # Calculate target position
            target_row = row
            target_column = column

            if arrow_throw == "u":
                target_row -= 1
            elif arrow_throw == "d":
                target_row += 1
            elif arrow_throw == "l":
                target_column -= 1
            elif arrow_throw == "r":
                target_column += 1
            else:
                print("Invalid direction")

            # Check arrow target
            if arrow_throw in ["u", "d", "l", "r"]:

                if (0 <= target_row < 4 and
                    0 <= target_column < 4):

                    if wumpus[target_row][target_column] == "WUMPUS":

                        print("Wumpus killed!")
                        score += 1000

                        wumpus[target_row][target_column] = "Save"
                        wumpus[1][0] = "Save"
                        wumpus[3][0] = "Save"

                    else:
                        print("Arrow wasted...")
                        score -= 10

                else:
                    print("Arrow went outside the world!")
                    score -= 10

                arrow = False

                print("Score:", score)

    # Check Wumpus
    if wumpus[row][column] == "WUMPUS":

        score -= 1000
        print("\nWumpus here!!")
        print("You Die")
        print("Your score is:", score)
        break

    # Check Gold
    if wumpus[row][column] == "GOLD":

        score += 1000
        print("\nCongratulations!")
        print("You found the GOLD!")
        print("You Win!")
        print("Your score is:", score)
        break

    # Check Pit
    if wumpus[row][column] == "PIT":

        score -= 1000
        print("\nAhhhhh!!!!")
        print("You fell in pit.")
        print("Your score is:", score)
        break

    print("Current Score:", score)

print("\nGAME OVER")

```

<h2>Output : </h2>

<img width="1411" height="745" alt="Screenshot 2026-11-23 134411" src="https://github.com/user-attachments/assets/94d7021b-8ec6-4ffd-936e-a9e4be500de5" />





<h2>Result : </h2>

Therefore, Wumpus World Problem using Python demonstrating Inferences from Propositional Logic solved successfully.






