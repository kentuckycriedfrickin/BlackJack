# BlackJack
#This is my garbage code I wrote for mr degelders stupid computer class
# Give instructions

# This is a function for my card values
def valuefunction(card):
    if card[:1] == "2" or card[:1] == "3" or card[:1] == "4" or card[:1] == "5" or card[
                                                                                   :1] == "6" or card[
                                                                                                 :1] == "7" or card[
                                                                                                               :1] == "8" or card[
                                                                                                                             :1] == "9":
        # The function only reads the first character of the names of the cards and based on that it will assign
        # a value to it
        return int(card[:1])
    elif card[:1] == "J" or "K" or "Q":
        return int(10)
    elif card[:1] == "1":
        return int(10)
    # This is where an ace can equal either 1 or 11
    elif card[:1] == 'A':
        AceNumber = input("Do you want this to be 1 or 11?\n>")
        if AceNumber == '1':
            return int(1)
        elif AceNumber == '11':
            return int(11)
        else:
            return
    else:
        return


# This is the function that creates the deck itself
# It assigns a suit and a number
def deckfunc():
    list1 = ["Hearts", "Diamonds", "Spades", "Clubs"]  # : These are my lists of suits and numbers to create the deck)
    list2 = ["Ace", "King", "Queen", "Jack", "10", "9", "8", "7", "6", "5", "4", "3", "2"]
    newdeck = []
    for i in list1:  # : i and j are just random names for an item in each list
        for j in list2:
            x = j + " of " + i
            newdeck.append(x)
    return newdeck


# This is the function for my computer player
def ComPlayer():
    global TotalValue
    global ComTotalValue
    while ComTotalValue < 18:  # The computer will hit until the value is 18 or over
        newcard = random.choice(deckfunc())
        newcardvalue = valuefunction(newcard)
        ComTotalValue = newcardvalue + ComTotalValue
        print(ComTotalValue)
        ComPlayer()
    if 21 > ComTotalValue > 17:  # The computer will stand if the number is greater than 17 and less than 21
        print(ComTotalValue)
        print("The computer stands.")
        print("You got: " + str(TotalValue) + " The computer got: " + str(
            ComTotalValue))  # This compares the values of the player and the computer
    if ComTotalValue > 21:  # lose condition
        print("The computer loses, you win!")
    elif ComTotalValue < TotalValue < 21:  # If your value is larger than the computer value, you win
        print("YOU WIN BIG WOO WOO! ")
    elif ComTotalValue == 21:  # winning condition   #If the computer gets 21, they win
        print("The computer wins! Better luck next time!")
    elif ComTotalValue > TotalValue < 21:  # If the computer's value is greater than the players, the computer wins
        print("The computer wins! Better luck next time!")
        return
# This is the player function to hit or stand
def HitStand():
    global TotalValue  # This makes it so I can call on TotalValue, which is in the main program
    global UserRules  # Dito lmao
    while int(TotalValue) < 21:
        hitstand = input("Would you like to hit or stand? (h/s): ")
        if hitstand == 'h':
            newcard = random.choice(deckfunc())  # If you hit you get another card and the assigned value
            newcardvalue = valuefunction(newcard)
            TotalValue = newcardvalue + int(TotalValue)  # This adds your new card's value to your current value
            print(TotalValue)
            HitStand()  # This makes the program loop until you get the desired amount of cards or you lose
            if TotalValue > 21:  # lose condition
                print("You LOSE!")
            elif TotalValue == 21:  # winning condition
                print("You WIN BIG WIN WOO WOO")
            else:
                play_again = input("Would you like to continue? Type yes or no (y/n) to leave\n")
                if play_again == "n":
                    UserRules = 4
                    UserRules = 4
                elif play_again == "y":
                    HitStand()
        elif hitstand == 's':
            print("You have chosen to stand. Your total is: " + str(TotalValue))
            return

# main program

UserRules = input("Let's play Blackjack! Press 1 to see the rules. Press 2 to play the game: ")
UserRules = int(UserRules)
if UserRules == 1:
    print('''
        Here are the rules! 
        The objective is to close to 21 as possible, without going over 21.
        It is up to each individual player if an ace is worth 1 or 11. 
        Face cards are 10 and any other card is its pip value.
        Before the deal begins, each player places a bet, in chips, 
        in front of them in the designated area.
        Minimum and maximum limits are established on the betting,
        and the general limits are from $2 to $500.
        You go first and must decide whether to
        "stand" (not ask for another card) or "hit" 
        (ask for another card in an attempt to get closer to a count of 21, 
        or even hit 21 exactly). Thus, a player may stand on the two cards
        originally dealt to them, or they may ask the dealer for additional 
        cards, one at a time, until deciding to stand on the total 
        (if it is 21 or under), or goes "bust" (if it is over 21). 
        In the latter case, the player loses and the dealer collects 
        the bet wagered. The dealer then turns to the next player to 
        their left and serves them in the same manner.
        If the player and dealer have equal unbusted totals the
        hand is considered a push and the player’s bet is returned.
        If a player wins a hand they are paid out at 1:1 on the total bet wagered
        on that hand. For example if the player wagered $10 and then doubled down
        placing a further bet of $10 on the hand and won, they would be paid a 
        total of $40, their $20 bet back and $20 winnings.
        If the player has Blackjack they are paid at 3:2, so that a wager of $10
        the player would be paid a total of $25, their $10 bet back plus $15 winnings.
    ''')
    UserRules = 2

while UserRules == 2:
    print("You have chosen to play Blackjack.")
    import random


    # This function creates the deck of cards
    def deckfunc():
        list1 = ["Hearts", "Diamonds", "Spades",
                 "Clubs"]  # : These are my lists of suits and numbers to create the deck)
        list2 = ["Ace", "King", "Queen", "Jack", "10", "9", "8", "7", "6", "5", "4", "3", "2"]
        newdeck = []
        for i in list1:  # : i and j are just random names for an item in each list
            for j in list2:
                x = j + " of " + i  # This make a random card
                newdeck.append(x)
        return newdeck


    newdeck = deckfunc()  # This gives the deck to the main program
    playercard1 = random.choice(newdeck)
    newdeck.remove(playercard1)  # This makes it so the card can't repeat itself
    playercard2 = random.choice(newdeck)
    newdeck.remove(playercard2)
    print(playercard1)
    print(playercard2)
    PlayerValue1 = valuefunction(playercard1)  # This assigns the card a value
    PlayerValue2 = valuefunction(playercard2)  # Ditto
    TotalValue = PlayerValue1 + PlayerValue2  # This combines the two values
    print(str(TotalValue))
    HitStand()  # This allows the player to hit or stand

    computercard1 = random.choice(newdeck)  # This gives the computer cards
    newdeck.remove(computercard1)
    computercard2 = random.choice(newdeck)
    newdeck.remove(computercard2)
    print(computercard1)
    print(computercard2)
    computercardvalue1 = valuefunction(computercard1)
    computercardvalue2 = valuefunction(computercard2)
    ComTotalValue = computercardvalue1 + computercardvalue2
    print(str(ComTotalValue))
    ComPlayer()
    #This code is basically the same as the player code
