from random import shuffle
class Card():
    def __init__(self,suit=1,ranke=1):
        self.suit = suit #
        self.ranke = ranke #ranke - 1,2,3...J,Q,K
    def get_suit(self):
        return self.suit
    def get_ranke(self):
        return self.ranke
    def set_ranke(self,ranke):
        self.ranke = ranke
    def __str__(self):
        return f" {values[self.ranke]} of {self.suit}"
class Deck(Card):
    def __init__(self):
        Card.__init__(self)
        self.deck = []
        for s in suits:
            for r in ranks:
                self.deck.append(Card(s,r))
    def __str__(self):
        deck_str = ""
        for card in self.deck:
            deck_str += '\n' + card.__str__()
        return deck_str
    def __len__(self):
        return len(self.deck)
    def get_deck(self):
        return self.deck
    def shuffle(self):
        shuffle(self.deck)
    def draw_card(self,name):
        card = self.deck.pop()
        if card.get_ranke() == 'Ace':
            if name == dealer.get_name():
                card.set_ranke("One")
            else:
                ranke = int(input(f"{name} you got Ace, you want 11 or 1?"))
                if ranke == 1:
                    card.set_ranke("One")
                else:
                    card.set_ranke("Ace")

        return card
class Player():
    def __init__(self,bank_roll,name):
        self.bank_roll = bank_roll
        self.name = name
        print(f"Hello {self.name}, you can start play now! \n You have {self.bank_roll} Dollars!")
    def __str__(self):
        return f"Name: {self.name}| Bank roll status: {self.bank_roll} Dollars"
    def get_name(self):
        return self.name
    def get_bank_roll(self):
        return self.bank_roll
    def deposit_money(self,money_amount):
        self.bank_roll += money_amount
        #print(f"{self.name}, Diposit Accepted,your balance is: {self.bank_roll} Dollars.")
    def withdraw(self,money_amount):
        while True:
            if money_amount > self.bank_roll:
                print("You cant withdraw more than you have!")
                money_amount = int(input(f"Try again other amount! \n REMINDER you have {self.bank_roll} Dollars"))
            elif self.bank_roll == 0 :
                return False
            else:
                self.bank_roll -= money_amount
                #print(f"{self.name}, Withdrawal Accepted,your balance is: {self.bank_roll} Dollars.")
                return True
class Player_Hand():
    def __init__(self):
        self.total_bet = 0
        self.cards = []
        self.value = 0
    def __len__(self):
        return len(self.cards)
    def get_total_bet(self):
        return self.total_bet
    def print_cards_in_hand(self):
        hand_str = ""
        for card in self.cards:
            hand_str += '|' + card.__str__()
        print(f"{player.get_name()} hand ► {hand_str}")
    def hit(self):
        card = deck.draw_card(player.get_name())
        self.cards.append(card)
        return player_hand.sum_value()
    def sum_value(self):
        sum = 0
        for i in range(len(self.cards)):
            sum += values[self.cards[i].get_ranke()]
        return  sum
    def make_bet(self,bet,player):
            while True:
                if bet < 10 :
                    bet = int (input("The minimum bet is 10 Dollars!"))
                elif player.withdraw(bet):
                    self.total_bet += bet
                    return True
                else:
                    return False
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
    def get_name(self):
        return self.name
def choose():
    c = input("\n Hit or Stand ?►")
    return c[0].lower() == 'h'
def check_bust(total_value):
    if total_value < 21:
        return True
    elif total_value > 21:
        print(" \n BUST \n")
        return False
def dealer_choose(dealer_value):
    if dealer_value < 17:
        return True
    else:
        return False
def dealer_vs_player(dealer_value,player_value):
    if dealer_value > player_value:
        print("Dealer won")
        print(f"you lose {bet} Dollars!")
        print("\n")

    else:
        print(f"You won! we diposit to your account {bet * 2} Dollar")
        player.deposit_money(bet * 2)
        print("\n")
def end_round():
    player_hand.reset_hand_cards()
    dealer.reset_hand_cards()
def replay():
    statistic()
    r = input("Play again? y/n►")
    return r[0].lower() == "y"
def statistic():
    print(f"                                           ╔══════════════╗")
    print(f"                                           ║Bank Roll: {player.get_bank_roll()} ║")
    print(f"                                           ╠══════════════╣")
    print(f"                                           ║   bet: {bet}    ║")
    print(f"                                           ╚══════════════╝")
suits = ('♥', '♦', '♠', '♣')
ranks = ('Two', 'Three', 'Four', 'Five', 'Six', 'Seven', 'Eight', 'Nine', 'Ten', 'Jack', 'Queen', 'King', 'Ace')
values = {'One':1,'Two':2, 'Three':3, 'Four':4, 'Five':5, 'Six':6, 'Seven':7, 'Eight':8, 'Nine':9, 'Ten':10, 'Jack':10,'Queen':10, 'King':10, 'Ace':11}
#Main gmae!##
deck = Deck() #createing the deck
deck.shuffle() #shuffleing the deck
game_on= True
name = input("Enter your name►")
bank_roll = int(input("Deposit to bank roll►"))
player = Player(bank_roll,name)
player_hand = Player_Hand()
dealer = Dealer_Hand()
print('\n'*15)
while True:
    dealer_turn = False  # chane to True when the player choose to Stand
    status = False  # the dealer show only one card
    end_round()
    game_on = True
    print("Hello!")
    bet = int(input("make a bet►"))
    print("\n")
    player_hand.make_bet(bet,player)
    statistic()
    for i in range(2):#etch player getting 2 cards (face up, dealer 1 face uo, and 1 face down)
        player_value = player_hand.hit()
        dealer_value = dealer.hit()

        player_hand.print_cards_in_hand()
    dealer.print_cards_in_hand(status)
    while game_on:
        if not dealer_turn:
            if player_value == 21:
                print(f"You won! we diposit to your account {bet*1.5} Dollar")
                player.deposit_money(bet*1.5)
                print("\n")

                game_on = False
            elif check_bust(player_value): #True - the value is less then 21
                if choose():
                   player_value = player_hand.hit()
                   player_hand.print_cards_in_hand()
                   print("\n")
                else:
                    dealer_turn = True
            else:# the value is over 21
                print(f"you lose {bet} Dollars!")
                print("\n")
                game_on = False

        else:
            status= True
            dealer.print_cards_in_hand(status)
            if dealer_value == 21 :
                print("Dealer won")
                print(f"you lose {bet} Dollars!")
                print("\n")
                end_round()
            elif check_bust(dealer_value):
                if dealer_choose(dealer_value): #the dealer value is less then 16 - hit
                    dealer_value = dealer.hit()
                else:
                    dealer_vs_player(dealer_value,player_value)
                    game_on = False
            else:
                print(f"Dealer BUST! You won! we diposit to your account {bet * 2} Dollar")
                player.deposit_money(bet * 2)
                print("\n")
                game_on = False

    if not replay():
        print("\n"*15)
        print(f"Bye {player.get_name()}, \n {player} ")
        print(f"Proofit: {player.get_bank_roll()-bank_roll} Dollars")
        break













