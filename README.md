# Finalskateshop
import pandas as pd
import random as ran
from PIL import Image


board = r"D:\harddrive\skateboards.png"
tuck = r"D:\harddrive\trucks.png"
wphoto = r"D:\harddrive\wheels.png"
bear = r"D:\harddrive\bearings.png"
grip = r"D:\harddrive\griptape.png"
skateboard = Image.open(board)
truckphoto = Image.open(tuck)
wheelpho = Image.open(wphoto)
bearphoto = Image.open(bear)
gripphoto = Image.open(grip)



userinputdeck = "--"
decksize = "--"
userinputtruck = "--"
trucksize = "--"
userinputwheels = "--"
userinputbearins = "--"
userinputgrip = "--"



decks = {"Plan B": [64.95, 7.5, 7.75, 8.00, 8.25, 8.5], "Santa Cruz": [41.15, 7.5, 7.75, 8.00, 8.25, 8.5], "Girl": [65.00, 7.5, 7.75, 8.00, 8.25, 8.5], "Chocolate": [65.00, 7.5, 7.75, 8.00, 8.25, 8.5], "Primitive": [35.00, 7.5, 7.75, 8.00, 8.25, 8.5]}
trucks = {"Krux": [47.90, 7.5, 7.75, 8.00, 8.25, 8.5], "Thunder": [70.00, 7.5, 7.75, 8.00, 8.25, 8.5], "Royal": [52.00, 7.5, 7.75, 8.00, 8.25, 8.5]}
wheels = {"Bones": [40.00, "97a"], "Spitfire": [43.00, "97"], "Ricta": [40.00, "86a"], "OJ": [40.00, "99a"]}
bearings = {"Bones Reds": 15.00, "Bones Ceramic": 96.00, "Broson Romaro": 34.00}
griptape = {"Alien Workshop Griptape": 15.00, "Grizzly Griptape": 13.00, "Shake Junt Griptape": 14.00, "Mob Griptape": 7}
sponsor = {"Board": 0, "Truck": 0, "Wheel": 0, "Bearing": 0, "griptape": 0, "nothing": 0, "nothing1": 0, "nothing2": 0}

totalAmount = 0
updatedprice = 0
skateSponsor = []

print("\nHello, Welcome to my shop!")
print("\nHere are the current products and sizes that we have in stock")
main = {"Option 1": ["Plan B Deck", "Krux Trucks", "Bones Wheeles", "Bones Reds Bearings", "Alien Workshop Griptape"], "Option 2": ["Santa Cruz Deck", "Thunder Trucks", "Spitfire Wheels", "Bones Ceramic Bearings", "Grizzly Griptape"], "Option 3": ["Girl Deck", "Royal Trucks", "Ricta Wheels", "Broson Romaro Bearings", "Shake Junt Griptape"], "Option 4": ["Chocolate Deck", "N/A", "OJ Wheels", "N/A", "Mob Griptape"], "Option 5": ["Primitive Deck", "N/A", "N/A", "N/A", "N/A"]}
d = {"Decks": ["Plan B", "Santa Cruz", "Girl", "Chocolate", "Primitive"], "Sizes": [7.5, 7.75, 8, 8.25, 8.5], "Prices": ["$64.95", "$41.15", "$65.00", "$65.00", "$35.00"]}
t = {"Trucks": ["Krux", "Thunder", "Royal"], "Sizes": [7.75, 8, 8.25,], "Prices": ["$47.90", "$70", "$52"], "Benefits": ["Light/strong", "Heavy/strong", "Light/improved turning"]}
w = {"Wheels": ["Bones", "Spitfire", "Ricta", "OJ"], "Sizes/Types": ["97a", 97, "86a", "99a"], "Prices": ["$40.00", "$43.00", "$40.00", "$40.00"], "Benefits": ["Soft(78-87a) = Better for rough surfaces", "Medium(90a-97a) = Best mix of speed/control", "Hard(99a and up) = street/trick skating", "--"]}
b = {"Bearings": ["Bones Reds", "Bones Ceramic", "Broson Romaro"], "Prices": ["$15", "$96", "$34"], "Benefits": ["Cheep/Fast", "Expensive/Fast", "improved durability"]}
g = {"griptape": ["Alien Workshop Griptape", "Grizzly Griptape", "Shake Junt Griptape", "Mob Griptape"], "Prices": ["$15.00", "$13.00", "$14.00", "$7.00"]}
userboard = {"Product": ["N/A", "N/A", "N/A", "N/A", "N/A"], "Size": ["N/A", "N/A", "N/A", "N/A", "N/A"], "Price": [0,0,0,0,0]}
mainMenu = pd.DataFrame(main, index = ["Decks", "Trucks", "Wheels", "Bearings", "Griptape"])

print(mainMenu)
userinput1 = int(input("\ndo you want to build a skateboard from scratch?  \n1) Yes:  \n2) No: "))
    

if userinput1 == 1:
    guessSponsor = input("\nWould you like to spin the wheel for chance of a sponsor?: \nYes:  \nNo: ")
    while True:
        if guessSponsor in ["yes", "Yes", "yea", "Yea"]:
            guess = ran.choice(list(sponsor.keys()))
            if guess in ["nothing", "nothing1", "nothing2"]:
                print("\nSorry, But you did not win anything today. Come back tomorrow for better luck!")
                skateSponsor.append("nothing")
                break

            else:
                skateSponsor.append(guess)
                print(f"\nCongraulations! you won free {guess}'s on us!")
                if guess == "Board":
                    for key, value in decks.items():
                        decks[key][0] = 0
                        for i in range(len(d["Prices"])):
                            d["Prices"][i] = "Free!"

                    break
                elif guess == "Truck":
                    for key, value in trucks.items():
                        trucks[key][0] = 0
                        for i in range(len(t["Prices"])):
                            t["Prices"][i] = "Free!"
                    break

                elif guess == "Wheel":
                    for key, value in wheels.items():
                        wheels[key][0] = 0
                        for i in range(len(w["Prices"])):
                            w["Prices"][i] = "Free!"
                    break

                elif guess == "Bearing":
                    for key, value in bearings.items():
                        bearings[key] = 0
                        for i in range(len(b["Prices"])):
                            b["Prices"][i] = "Free!"
                    break

                else:
                    for key, value in griptape.items():
                        griptape[key] = 0
                        for i in range(len(g["Prices"])):
                            g["Prices"][i] = "Free!"
                    break

        else:
            break

    while True:
        print(f"\nYour current custom complete contains: ")
        skate = pd.DataFrame(userboard, index = ["Decks", "Trucks", "Wheels", "Bearings", "Griptape"])
        print(skate)
        totalAmount = sum(userboard["Price"])
        print(f"\nYou currently owe ${totalAmount}")
        print(f"\nYou currently have a {skateSponsor[0]} on us!")
        userinput2 = int(input("\nWhat do you want to purchase? \n1) Deck \n2) Trucks \n3) Wheels \n4) bearings \n5) Griptape \n6) Finish and checkout: "))
        if userinput2 == 1:
            skateboard.show()
            deckPick = pd.DataFrame(d, index = [1, 2, 3, 4, 5])
            print(deckPick)
            while True:
                userinputdeck = input("\nwhich deck would you like to purchase?: ")
                if userinputdeck in ["Plan B", "plan b","Santa Cruz", "santa cruz", "Girl", "girl", "Chocolate", "chocolate","Primitive", "primitive"]:
                    userboard["Product"][0] = userinputdeck
                    userboard["Price"][0] = decks[userinputdeck][0]
                    decksize = float(input("\nWhich deck size would you like your board to be?: "))
                    userboard["Size"][0] = decksize
                    break
                else:
                    print("\nSorry, we do not have that board in stock. Please pick another one")

        elif userinput2 == 2:
            truckphoto.show()
            truckPick = pd.DataFrame(t, index = [1, 2, 3])
            print(truckPick)
            while True:
                userinputtruck = (input("\nWhich trucks would you like to purchase?: "))
                if userinputtruck in ["Krux", "krux", "Thunder", "thunder", "Royal", "royal"]:    
                    userboard["Product"][1] = userinputtruck
                    userboard["Price"][1] = trucks[userinputtruck][0]
                    updatedprice = userboard["Price"][1]
                    trucksize = float(input("\nWhat size would you like your trucks to be?: "))
                    userboard["Size"][1] = trucksize
                    break
                else:
                    print("\nSorry, we do not have that Truck in stock right now. Please pick the Trucks in stock")
            
        elif userinput2 == 3:
            wheelpho.show()
            wheelsPick = pd.DataFrame(w, index = [1, 2, 3, 4])
            print(wheelsPick)
            while True:
                userinputwheels = (input("\nWhich Wheels would you like to purchase?: "))
                if userinputwheels in ["Bones", "bones", "Spitfire", "spitfire", "Ricta", "ricta", "OJ", "oj"]:
                    userboard["Product"][2] = userinputwheels
                    userboard["Price"][2] = wheels[userinputwheels][0]
                    userboard["Product"][2] = userinputwheels
                    if userinputwheels == "Bones":
                        userboard["Size"][2] = "97a"
                        break
                    elif userinputwheels == "Spitfire":
                        userboard["Size"][2] = "97"
                        break
                    elif userinputwheels == "Ricta":
                        userboard["Size"][2] = "86a"
                        break
                    else:
                        userboard["Size"][2] = "99a"
                        break
                else:
                    print("Sorry we currently don't have those wheels in stock. Please pick avaliable Wheels")

        elif userinput2 == 4:
            bearphoto.show()
            bearins = pd.DataFrame(b, index = [1, 2, 3])
            print(bearins)
            while True:
                userinputbearins = (input("\nWhich bearings would you like to purchase?: "))
                if userinputbearins in ["Bones Reds", "bones reds", "Bones Ceramic", "bones ceramic", "Broson Romaro", "broson romaro"]:
                    userboard["Product"][3] = userinputbearins
                    userboard["Price"][3] = bearings[userinputbearins]
                    break
                else:
                    print("\nSorry we currently don't have these Bearings in stock. Please pick avaliable Bearings")

        elif userinput2 == 5:
            gripphoto.show()
            gripPick = pd.DataFrame(g, index = [1, 2, 3, 4])
            print(gripPick)
            while True:
                userinputgrip = (input("\nWhich grip would you like purchase?: "))
                if userinputgrip in ["Alien Workshop", "Alien Workshop Griptape", "alien workshop", "alien workshop griptape", "Grizzly", "Grizzly Griptape", "grizzly","grizzly griptape", "Shake Junt", "Shake Junt Griptape", "shake junt", "shake junt griptape", "Mob", "Mob Griptape", "mob", "mob griptape"]:
                    userboard["Product"][4] = userinputgrip
                    userboard["Price"][4] = griptape[userinputgrip]
                    break
                else:
                    print("\nSorry we currently don't have that type of griptape in stock. Please pick an avaliable option")

        else:
            print(f"\nYour order consists of: \nDeck: {decksize} {userinputdeck} \nTruck: {trucksize} {userinputtruck} \nWheels: {userinputwheels} \nBearings: {userinputbearins} \nGriptape: {userinputgrip}")
            print(f"\nThank you for your purchase! Your total is ${totalAmount}")
            print("\nHave an amazing day!")
            break

else:
    print("\nHave an amazing day!")
