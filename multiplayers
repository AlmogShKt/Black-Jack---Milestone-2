from random import shuffle #import random calss to shuffle the deck after each turn
from termcolor import colored #import termcolor to represent this chips
import time # import time to create delay between printouts
class Card(): #Card calss
    def __init__(self,suit=1,ranke=1): #the default is 1 and 1
        self.suit = suit #'♥', '♦', '♠', '♣'
        self.ranke = ranke #ranke - 1,2,3...10/11 (11 is Ace)
    def get_suit(self): #return the suit
        return self.suit
    def get_ranke(self):#return the ranke
        return self.ranke
    def set_ranke(self,ranke): #setting the rank for new one (1/11 in Ace)
        self.ranke = ranke
    def __str__(self): #printout the card (ex: '1 ♦')
        return f" {values[self.ranke]}  {self.suit}"
class Deck(Card):#Deck class - the deck is list of 52 card. 1-10,J,Q,K,A * ♥,♦,♣,♠)
    def __init__(self):
        Card.__init__(self)
        self.deck = [] #creating empty list
        for s in suits: #creating the deck.  1-10,J,Q,K,A * ♥,♦,♣,♠)
            for r in ranks:
                self.deck.append(Card(s,r)) #append etch card to the list (ex: rank: 5 suit: ♣
    def __str__(self): # Printout the deck in order
        deck_str = ""
        for card in self.deck:
            deck_str += '\n' + card.__str__()
        return deck_str
    def __len__(self): # Return the deck length (52-0)
        return len(self.deck)
    def shuffle(self):# Shuffle the deck, using the random library
        shuffle(self.deck)
    def draw_card(self,name):# Return the card in the end of the list. the pop fun' removing the card.
        card = self.deck.pop()
        if card.ranke == 'Ace': # checking if the card is a Ace - if yes - ask the player what value he want (1/11) and set is as the card ranke. then return the card.
            if name == dealer.name: # if its the dealer- check if the value is 10 - if yes - he will get 11 - winning else set as 1
                if dealer_value == 10:
                    card.set_ranke("Ace")
                else:
                    card.set_ranke("One")

            else: #If its not the dealer - ask the player what he want 1/11 and set it up
                ranke = int(input(f"{name} you got Ace, you want 11 or 1?"))
                if ranke == 1:
                    card.set_ranke("One")
                else:
                    card.set_ranke("Ace")

        return card # In the end return the card
class Player(): #Player class - setting up all the player information
    def __init__(self,bank_roll,name): #To crate up a player need: the player name and the amount of money to deposit into the bank roll
        self.bank_roll = bank_roll
        self.name = name
        print(f"Hello {self.name}, you can start play now! \n You have ${self.bank_roll} !") #printout that allset!
    def __str__(self):
        return f"Name: {self.name}| Bank roll status: ${self.bank_roll}" #printout thr name and the bank roll value
    def deposit_money(self,money_amount): #Deposit the first money amount / the bet after winning
        self.bank_roll += money_amount
    def withdraw(self,money_amount,p): #taking the players bet and withdraw this amount from the bank account
        while True:
            if self.bank_roll == 0 :#if the bank roll value is 0, ask for more money to keep playomg
                print("you cant withdraw! you lose all your money.")
                diposit = int(input("Diposit more now!►"))
                p.deposit_money(diposit)
                return True
            elif money_amount > self.bank_roll: #make sure that we withdraw only amount we have
                print("You can't withdraw more than you have!")
                money_amount = int(input(f"Try again other amount! \n REMINDER you have {self.bank_roll} Dollars"))
            else:
                self.bank_roll -= money_amount
                return True
class Player_Hand():
    def __init__(self):
        self.total_bet = 0
        self.cards = []
        self.value = 0
        self.bet = 0
        self.status = True
    def __len__(self):
        return len(self.cards)
    def __str__(self):
        return f"This is the bet: {self.total_bet}| This is the value: {self.value}| This is the cards: {self.cards[0],self.cards[1]}"
    def get_bet(self):
        return self.total_bet
    def set_bet(self,bet):
        self.bet = bet
    def set_status(self,status):
        self.status = status
    def print_cards_in_hand(self,p):
        hand_str = ""
        for card in self.cards:
            hand_str += '|' + card.__str__()
        print(f"{players[p].name} hand ► {hand_str}")
    def hit(self,p):
        card = deck.draw_card(players[p].name)
        self.cards.append(card)
        hands[p].sum_value()
    def sum_value(self):
        sum = 0
        for i in range(len(self.cards)):
            sum += values[self.cards[i].get_ranke()]
        self.value = sum
        return  sum
    def make_bet(self,bet,player):
            while True:
                if bet < 10 :
                    bet = int (input("The minimum bet is 10 Dollars!"))
                elif not player.withdraw(bet,player):
                    return False
                elif player.withdraw(bet,player):
                    self.bet = bet
                    self.total_bet += bet
                    return True

    def reset_hand_cards(self):
        self.cards = []
class Dealer_Hand():
    def __init__(self):
        self.cards = []
        self.value = 0
        self.name = "Dealer"
    def __len__(self):
        return len(self.cards)
    def print_cards_in_hand(self,status):

        hand_str =""
        if not status:
            if len(self.cards)>0:
                hand_str += '|' + self.cards[0].__str__()
            if len(self.cards)>1:
                    hand_str += '|' + (" █ "*(len(self.cards)-1))
            print(f"{self.name} hand ► {hand_str}")
        else:
            for card in self.cards:
                hand_str += '|' + card.__str__()
            print(f"{self.name} hand ► {hand_str}")
    def hit(self):
        card = deck.draw_card(self.name)
        self.cards.append(card)
        return dealer.sum_value()
    def sum_value(self):
        sum = 0
        for i in range(len(self.cards)):
            sum += values[self.cards[i].get_ranke()]
        self.value = sum
        return  self.value
    def reset_hand_cards(self):
        self.cards = []

def choose(p):
    c = input(f"{players[p].name} Hit or Stand ? ►")
    return c[0].lower() == 'h'
def check_bust(total_value,p):
    if total_value < 21:
        return True
    elif total_value > 21:
        return False
def dealer_choose(dealer_value):
    if dealer_value < 17:
        return True
    else:
        return False
def end_round():
    for i in range(players_num):
        hands[i].reset_hand_cards()
        hands[i].set_status(True)


    dealer.reset_hand_cards()
def replay():
    statistic()
    r = input("Play again? y/n►")
    return r[0].lower() == "y"
def statistic():
    for i in range(players_num):


        print(f"                                           ╔════════════════╗")
        print(f"                                           ║    {players[i].name}       ║")
        print(f"                                           ╠════════════════╣")
        print(f"                                           ║ Bank Roll: {players[i].bank_roll} ║")
        print(f"                                           ╠════════════════╣")
        print(f"                                           ║ total bet: {hands[i].total_bet}   ║")
        print(f"                                           ╚════════════════╝")
def take_bets():
    for i in range(players_num):
        while True:
            try:
                bet = int(input(f"{players[i].name} How many chips would you like to bet? "))
                print_cheps(int(bet))
                print("\n")

                while not hands[i].make_bet(bet,players[i]):
                    try:
                        bet = int(input(f"{players[i].name} try again, How many chips would you like to bet? "))
                        print_cheps(int(bet))
                        print("\n")
                    except ValueError:
                        print('Sorry, a bet must be an integer!')



            except ValueError:
                print('Sorry, a bet must be an integer!')
            else:
                break
def show_win_or_lose(score,i,bet_rate): #printing the detail's about the winning or losseing VS delaer - player mode: Stand
    if score: #True = the dealer won
        print("════════════════════════════════════════════════")
        print(f"{players[i].name}:")
        print(f"Your value: {hands[i].value}| Dealer value: {dealer_value} ► Dealer won!")
        print(f"you lose $ {hands[i].bet} ")
        print("════════════════════════════════════════════════")
    else: #False = the dealer lose
        print("════════════════════════════════════════════════")
        print(f"{players[i].name}:")
        print(f"Your value: {hands[i].value}| Dealer value: {dealer_value} ► you won!")
        print(f"you won $ {hands[i].bet*bet_rate} ")
        print_cheps(int(hands[i].bet*bet_rate))
        print("════════════════════════════════════════════════")
        players[i].deposit_money(hands[i].bet*bet_rate)
def show_win_or_lose_dealer_flip(score,i,bet_rate):#printing the detail's about the winning or losseing. delaer mode: flip - player mode: BUST or WIN 21
    if score: # False = the player pass the 21 value - lose
        print("════════════════════════════════════════════════")
        print(f"{players[i].name}:")
        print(f"Your value: {hands[i].value} ► BUST!")
        print(f"you lose $ {hands[i].bet} ")
        print("════════════════════════════════════════════════")
    else: #True = the player hit 21 value - win
        print("════════════════════════════════════════════════")
        print(f"{players[i].name}:")
        print(f"Your value: {hands[i].value} ► you won 21!")
        print(f"you won $ {hands[i].bet*bet_rate} ")
        print_cheps(int(hands[i].bet*bet_rate))
        print("════════════════════════════════════════════════")
        players[i].deposit_money(hands[i].bet*bet_rate)
def print_cheps(bet):
    def split_cheps(bet):
        bet = int(bet)
        cheps = []
        c50 = bet // 50
        c10 = (bet - c50 * 50) // 10
        c5 = (bet - c50 * 50 - c10 * 10) // 5
        c1 = (bet - c50 * 50 - c10 * 10-c5*5) // 1
        cheps.append(c50)
        cheps.append(c10)
        cheps.append(c5)
        cheps.append(c1)
        return cheps
    cheps = split_cheps(bet)
    print(f"{colored('©'*cheps[0], 'red')}|{colored('©'*cheps[1],'blue')}|{colored('©'*cheps[2],'grey')}|{colored('©'*cheps[3],'yellow')}")


suits = ('♥', '♦', '♠', '♣')
ranks = ('Two', 'Three', 'Four', 'Five', 'Six', 'Seven', 'Eight', 'Nine', 'Ten', 'Jack', 'Queen', 'King', 'Ace')
values = {'One':1,'Two':2, 'Three':3, 'Four':4, 'Five':5, 'Six':6, 'Seven':7, 'Eight':8, 'Nine':9, 'Ten':10, 'Jack':10,'Queen':10, 'King':10, 'Ace':11}

#Main gmae!##



game_on= True



#player = Player(bank_roll,name)
#player_hand = Player_Hand()
dealer = Dealer_Hand()

print('\n'*15)
players_num = int(input("How many players wants to play?►"))
players = []
hands = []
players_value = []


count_stands = 0
for i in range(players_num):#Createing the players and the hands
    name = input("Enter your name►")
    bank_roll = int(input("Deposit to bank roll►"))
    players.append(Player(bank_roll,name))
    hands.append(Player_Hand())
    print("\n")
while True:
    index = []
    deck = Deck()  # createing the deck
    deck.shuffle()  # shuffleing the deck
    #Setting all to defults
    dealer_turn = False  # chane to True when the player choose to Stand
    status = False  # the dealer show only one card

    end_round()

    game_on = True
    ####
    print("     ♥♦  Hello and welcome to Black Jack !  ♣♠")
    print("                      Our chips:")
    print(f"       {colored('©' , 'red')} - $50|{colored('©' , 'blue')} - $10 |{colored('©' , 'grey')} - $5 |{colored('©', 'yellow')} - $1")
    print("\n")
    take_bets()
    #statistic()
    for p in range(players_num):
        for i in range(2):#etch player getting 2 cards (face up, dealer 1 face uo, and 1 face down)
            hands[p].hit(p)
            hands[p].print_cards_in_hand(p)

        print("\n")
    dealer_value = dealer.hit()
    dealer_value = dealer.hit()
    dealer.print_cards_in_hand(status)

    p = 0

    while count_stands != players_num:
        game_on = True

        while game_on: # hit/stand/players moves

            if hands[p].status:
                if hands[p].value == 21:
                    show_win_or_lose_dealer_flip(False,p,1.5)
                    players[p].deposit_money(hands[p].bet * 1.5)
                    count_stands += 1
                    hands[p].set_status(False)
                    p += 1
                    game_on = False
                    print("\n")
                elif check_bust(hands[p].value,p):  # True - the value is less then 21
                    if choose(p):
                        hands[p].hit(p)
                        hands[p].print_cards_in_hand(p)
                        print("\n")
                    else:
                        index.append(p)
                        count_stands +=1
                        hands[p].set_status(False)
                        p += 1
                        game_on =False
                else:  # the value is over 21
                    show_win_or_lose_dealer_flip(True,p,1)
                    count_stands += 1
                    hands[p].set_status(False)
                    p += 1
                    game_on = False
                    print("\n")

    if len(index) > 0:
        game_on = True
        p = 0
        while game_on:
            dealer_card_status = True
            dealer.print_cards_in_hand(dealer_card_status)
            print("\n")
            if dealer_value == 21 : # if the dealer hand has 21 value - the dealer win all other player
                print("Dealer won! 21!")
                for i in index:
                    show_win_or_lose_dealer_flip(True,i,2)
                    game_on =False
            elif dealer_value < 21: #Ture - less then 21
                if dealer_choose(dealer_value):  # the dealer value is less then 16 - hit?
                    dealer_value = dealer.hit()
                else: #The dealer value is less then 21 but more then 17
                    for i in index:
                        show_win_or_lose(dealer_value >= hands[i].value,i,2)
                    game_on = False
            else:
                print(f"Dealer BUST!")
                for i in index:
                    show_win_or_lose(False,i,2)
                game_on =False
                print("\n")
    if count_stands == players_num:
        count_stands = 0
    if not replay():
        print("\n"*15)
        print(f"Bye")
        break

















