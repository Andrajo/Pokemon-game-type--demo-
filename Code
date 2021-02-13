import copy

class ReviveItem():
  def __init__(self,name,item):
      self.name=name
      self.item=item
  
class HealItem(ReviveItem):
    pass
    
class AttackItem(ReviveItem):
    pass
    
class DefenseItem(ReviveItem):
    pass


class Trainer():
  def __init__(self,name,pokemons,items,active_pokemons,current_pokemon):
    self.current_pokemon=current_pokemon
    self.name=name
    self.pokemons=pokemons
    self.items=items
    self.active_pokemons=active_pokemons
  def activate_item(self,item,pokemon):
    self.items.pop(self.items.index(item))
    if type(item)==HealItem:
      pokemon.Heal(item)
    elif type(item)==ReviveItem:
      pokemon.revive(item)
  def challenge(self,own_pokemon,enemy_pokemon,attack_mode):
    if attack_mode == 1:
      own_pokemon.normal_attack(enemy_pokemon)
    if attack_mode == 2:
      own_pokemon.type_attack(enemy_pokemon)
    if attack_mode == 3:
      own_pokemon.Super_attack(enemy_pokemon)
    if enemy_pokemon.state=="Down":
        heal=HealItem("tear",50)
        life=ReviveItem("cry",30)
        strenght=AttackItem("battlecry",2)
        shield=DefenseItem("armor",2)
        print("{} is Down now".format(enemy_pokemon.name))
        self.current_pokemon.xp+=57*enemy_pokemon.level-7*self.current_pokemon.level
        posibility=[1]
        if random.choice(posibility)==1:
            lst_iteme=[life]
            for item_adaugat in self.items:
                lst_iteme.append(item_adaugat)
            self.items=copy.deepcopy(lst_iteme)
            print("{} found {} item".format(self.name,life.name))
        posibility=[0,1,0,0,0]
        if random.choice(posibility)==1:
            lst_iteme=[heal]
            for item_adaugat in self.items:
                lst_iteme.append(item_adaugat)
            self.items=copy.deepcopy(lst_iteme)
            print("{} found {} item".format(self.name,heal.name))
        posibility=[0,1,0,0,0,0,0,0,0,0]
        if random.choice(posibility)==1:
            lst_iteme=[strenght]
            for item_adaugat in self.items:
                lst_iteme.append(item_adaugat)
            self.items=copy.deepcopy(lst_iteme)
            print("{} found {} item".format(self.name,strenght.name))
        posibility=[0,1,0,0,0,0,0,0,0,0]
        if random.choice(posibility)==1:
            lst_iteme=[shield]
            for item_adaugat in self.items:
                lst_iteme.append(item_adaugat)
            self.items=copy.deepcopy(lst_iteme)
            print("{} found {} item".format(self.name,shield.name))
        if self.current_pokemon.xp>=1000:
            self.current_pokemon.xp=0
            self.current_pokemon.level+=1
            self.current_pokemon.max_health=self.current_pokemon.level*self.current_pokemon.defense
            self.current_pokemon.hp=self.current_pokemon.max_health
            print("Your companion got +{} super move.Now you have {}".format(min(self.current_pokemon.super_attack+1,3)-self.current_pokemon.super_attack,min(self.current_pokemon.super_attack+1,3)))
            self.current_pokemon.super_attack=min(self.current_pokemon.super_attack+1,3)
            print("Add a point to:\n1.Attack\n2.Defense")
            po=int(input())
            if po == 1 :
                self.current_pokemon.power+=1
            if po == 2 :
                self.current_pokemon.defense+=1
  def swap_pokemon(self,pokemon,next_pokemon):
    if next_pokemon.state=="Good":
      self.current_pokemon=next_pokemon
  def find_pokemon(self):
      lst=[1,0,0,0]
      ma=mi=self.pokemons[0].level
      for levelul in self.pokemons:
          if mi>levelul.level: 
              mi=levelul.level
          if ma < levelul.level:
              ma=levelul.level
      Pokemon_Name=random.choice(Pokemons_names)+" "+random.choice(Pokemon_name_2)
      lv=random.choice(range(mi,ma+1))
      x=random.choice(range(1,lv))
      if random.choice(lst)==1:
          New_Pokemon=Pokemon(Pokemon_Name,lv,Type,x,lv-x,self)
          print("You found a new posible companion:{} with: Level:{} Attack Power:{} Defense:{} Hp:{} Type:{}\n".format(New_Pokemon.name,New_Pokemon.level,New_Pokemon.power,New_Pokemon.defense,New_Pokemon.max_health,New_Pokemon.type))
          print("Your companions and their stats are:\n")
          poz=0
          for the_one in self.pokemons:
              poz+=1
              print(poz,"{} with: Level:{} Attack Power:{} Defense:{} Hp:{} Type:{}\n".format(the_one.name,the_one.level,the_one.power,the_one.defense,the_one.hp,the_one.type))
          print("Do you want to swap one of your companions with this one?(type: 1 or Yes \  anything else will be equal to No)")
          if input()=="1" or input()=="Yes":
              print("Who do you want to change?\n(input the number of the companion you want to swap for the new one)")
              pozitie=int(input())
              adj=["depreseed","sad","beautiful","lovely","happy","shitty","lonely","exciting","empty","boring","cranky","fulfilling","fantastic","bloody cruel","cruel"]
              place=["batroom of a gas station","house","girlfriend","nature","gas station","hospital","Cernobil station","a forest"]
              sbj=["restaurant","family","child by mistake","career in the culinary art","career in porn","protest against the tubular pasta shape"]
              name=["Franck","Jack","Emily","Himself","F***ING JESSICA","Karen","Stefi","Frank","Dragos","Andrei","Odobasian","Samuel","Chad"]
              kek=["his stupidity","a snack","his luck","that one pair of jeans","a glass of wather","a car","his car","F***ING JESSICA"]
              print("You choose to release {} ,he'll now live a {} life in the {} where he made a {}, just to meet a {} end becasue of {} and {}".format(self.pokemons[pozitie-1].name,random.choice(adj),random.choice(place),random.choice(sbj),random.choice(adj),random.choice(name),random.choice(kek)))
              print("Rename your new companion!")
              new_name=input()
              New_Pokemon.name=new_name
              self.pokemons[pozitie-1]=New_Pokemon
          else :
              print("You choose not to swap any of your companions")
  def Trainer_Not_Down(self):
      for i in self.pokemons:
          if i.state=="Good":
              return True
      return False
    
class PokemonDown(Exception):
  def __repr__(self):
    return "Pokemon is knocked out"


class Pokemon():
  def __init__(self,name,level,nature_type,power,defense,trainer):
    self.name=name
    self.level=level
    self.type=nature_type
    self.state="Good"
    self.power=power
    self.defense=defense
    self.max_health=self.level*self.defense
    self.hp=self.max_health
    self.xp=0
    self.super_attack=3
    self.trainer=trainer
  def lose_hp(self,attack):
    self.hp-=attack
    print("{} now has {} hp".format(self.name,max(self.hp,0))) 
    if self.hp<=0 :
      self.state="Down"
  def revive(self,item):
    if type(item)==ReviveItem and self.hp<=0:
      self.hp=min(item.item,self.max_health)
      self.state="Good"
      print("{} is now alive and at {} hp.".format(self.name,self.hp))
  def Heal(self,item):
    if type(item)==HealItem and self.state=="Good":
      old_hp=self.hp
      self.hp=min(self.hp+item.item,self.max_health)
      print("{} recived {} hp, now has {} hp".format(self.name,self.hp-old_hp,self.hp))
    elif type(item)==HealItem and self.state=="Down":
      print("Pokemon Down, replace")
  def IncreaseStrenght(self,item):
    if type(item)==AttackItem and self.state=="Good":
      self.power+=item.item
  def IncreaseDefense(self,item):
    if type(item)==DefenseItem and self.state=="Good":
      self.defense+=item.item
  def normal_attack(self,pokemon):
    if type(pokemon)==Pokemon and pokemon.state=="Good":
      print("{} used a normal attack.".format(self.name))
      pokemon.lose_hp(self.power-pokemon.defense*0.2)
      print("{} lost {} hp".format(pokemon.name,(self.power-pokemon.defense*0.2)))
  def type_attack(self,pokemon):
    if type(pokemon)==Pokemon and pokemon.state=="Good":
      print("{} used a {} attack.".format(self.name,self.type))
      if (self.type=="Grass" and pokemon.type=="Water") or (self.type=="Water" and pokemon.type=="Fire") or (self.type=="Fire" and pokemon.type=="Grass"):
        pokemon.lose_hp(2*self.power-pokemon.defense*0.2)
        print("It's super efective!\n{} lost {} hp".format(pokemon.name,(2*self.power-pokemon.defense*0.2)))
      if (self.type=="Water" and pokemon.type=="Grass") or (self.type=="Fire" and pokemon.type=="Water") or (self.type=="Grass" and pokemon.type=="Fire") or (self.type=="Water" and pokemon.type=="Water") or (self.type=="Fire" and pokemon.type=="Fire") or (self.type=="Grass" and pokemon.type=="Grass"):
        pokemon.lose_hp((1/2)*self.power-pokemon.defense*0.2)
        print("It's less efective.\n{} lost {} hp".format(pokemon.name,((1/2)*self.power-pokemon.defense*0.2)))
  def Super_attack(self,pokemon):
    if type(pokemon)==Pokemon and pokemon.state=="Good" and self.super_attack>0:
      self.super_attack-=1
      print("{} used a super attack.{} more remaining".format(self.name,self.super_attack))
      if (self.type=="Grass" and pokemon.type=="Water") or (self.type=="Water" and pokemon.type=="Fire") or (self.type=="Fire" and pokemon.type=="Grass"):
        pokemon.lose_hp(3*2*self.power-pokemon.defense*0.2)
        print("It's super efective!\n{} lost {} hp".format(pokemon.name,(3*2*self.power-pokemon.defense*0.2)))
      if (self.type=="Water" and pokemon.type=="Grass") or (self.type=="Fire" and pokemon.type=="Water") or (self.type=="Grass" and pokemon.type=="Fire") or (self.type=="Water" and pokemon.type=="Water") or (self.type=="Fire" and pokemon.type=="Fire") or (self.type=="Grass" and pokemon.type=="Grass"):
        pokemon.lose_hp(3*(1/2)*self.power-pokemon.defense*0.2)
        print("It's less efective.\n{} lost {} hp".format(pokemon.name,(3*(1/2)*self.power-pokemon.defense*0.2)))
      
        
import random 


print("""Little Intro:\nYour companions will get random power and defense stats as well as it's type.Same for the enemys.
      \nAll companions will start at level 10,once you level up you will have a point and will choose what to spend it on.
      \nYou will have 6 companions, as well as your enemys.
      \nYour current companion will get experience once it succesfuly eliminates an enemy companion.
      \nThe normal attack gives a normal ammount of damage,based only on enemys defense and your companion power.
      \nThe type attack is alike the normal attack, but it's influenced by the type of the companions(it may be a 2 times stronger attack or a half damage attack).
      \nEvery companion has a max of 3 super moves that's 3 times more powerful then the type attack and it's influenced by the same things, and once you level up if you have less then 3 you will get a bonus one. 
      \nYou have one move per Round,you can choose to attack,swap,or use an item .
      \nIf you try to use a super attack and your companion doesn't have any, or use an item when you don't have any your turn will pass.
      \nOnce you used an item,that item is gone
      \nAt start you will have one item for healing and one item for reviving, you will have a 33% chance to find a healing item(tear) after a fight, and 20% for a revive item(cry).
      \nAfter a fight you will have a 10% chance to find a special item that increses your companion power(battlecry) or defense(armor) by 2.
      \nYou can't attack or heal a pokemon that's down,you can just revive him or swap him with one in a good state.
      \nIf all your companions are down, you lose.Same for the enemys.
      \nPlease enjoy!""")
Power=[1,2,3,4,5,6,7,8,9]
types=["Fire","Water","Grass"]
Trainer_First_Name=["Josh","Judi","Odobasian","Samuel","Sam","Chad","Dick"]
Trainer_Last_Name=["Ash","Doom","Ded","Goodman","Babyface"]
Pokemons_names=["Megalodon","Turbo","Babite","Elatric","Turteo"]
Pokemon_name_2=["Dick","Autobot","Traumato","Boomball","Showers","Schlurp","Long Stone"]
Enemy_Trainer_Name=random.choice(Trainer_First_Name)+" "+random.choice(Trainer_Last_Name)
heal=HealItem("tear",50)
life=ReviveItem("cry",30)
strenght=AttackItem("battlecry",2)
shield=DefenseItem("armor",2)
items=[heal,life]
Trainer_Name=input("What's your name?\n")
Pokemon_list=[]
start_pokemon=0
Andrei=Trainer(Trainer_Name,Pokemon_list,items,6,start_pokemon)
for number in range(6):
    Pokemon_Name=input("Choose a name for the companion:")
    Type=random.choice(types)
    x=random.choice(Power)
    Charmender=Pokemon(Pokemon_Name,10,Type,x,10-x,Andrei)
    Andrei.pokemons.append(Charmender)
print("\nHello {}, for your next battles you own:\n".format(Andrei.name))
j=0
for i in Andrei.pokemons:
    j+=1
    print(str(j)+". {} with Power:{}; Defense:{}; Hp:{}; and Type:{}. \n".format(i.name,i.power,i.defense,i.hp,i.type))
start_pokemon=int(input("Choose the number of your starting companion:"))
Andrei.current_pokemon=Andrei.pokemons[start_pokemon-1]
print("You choose",Andrei.current_pokemon.name,"\n")
Pokemon_list=[]
Dragos=Trainer(Enemy_Trainer_Name,Pokemon_list,items,6,0)
First_Trainer=Trainer(Enemy_Trainer_Name,Pokemon_list,items,6,0)
Second_Trainer=Trainer(Enemy_Trainer_Name,Pokemon_list,items,6,0)
Third_Trainer=Trainer(Enemy_Trainer_Name,Pokemon_list,items,6,0)
Forth_Trainer=Trainer(Enemy_Trainer_Name,Pokemon_list,items,6,0)
Fifth_Trainer=Trainer(Enemy_Trainer_Name,Pokemon_list,items,6,0)
Sixth_Trainer=Trainer(Enemy_Trainer_Name,Pokemon_list,items,6,0)
Enemy_Trainer_List=[First_Trainer]
for Trainer_number in Enemy_Trainer_List:
  for number in range(2):
      Pokemon_Name=random.choice(Pokemons_names)+" "+random.choice(Pokemon_name_2)
      Type=random.choice(types)
      x=random.choice(Power)
      Charmender=Pokemon(Pokemon_Name,10,Type,x,10-x,Trainer_number)
      Trainer_number.pokemons.append(Charmender)
  Trainer_number.current_pokemon=Trainer_number.pokemons[0]

for Trainer_number in Enemy_Trainer_List:
  print("You're facing now {} and his companion {}".format(Trainer_number.name,Trainer_number.current_pokemon.name))
  while Andrei.Trainer_Not_Down() and Trainer_number.Trainer_Not_Down():
    print("\nEnemy companion stats:","\n","Attack Power:{} \n Defense:{} \n Hp:{} \n Type:{}\n".format(Trainer_number.current_pokemon.power,Trainer_number.current_pokemon.defense,Trainer_number.current_pokemon.hp,Trainer_number.current_pokemon.type))
    print("Your companion stats:","\n","Attack Power:{} \n Defense:{} \n Hp:{} \n Type:{}\n".format(Andrei.current_pokemon.power,Andrei.current_pokemon.defense,Andrei.current_pokemon.hp,Andrei.current_pokemon.type),"\nChoose your next action:", "\n" ,"1.Attack" ,"\n", "2.Use Item", "\n", "3.Swap Pokemon", "\n")
    first_input=int(input())
    if Andrei.current_pokemon.state=="Down":
        print("Your companion is down, please revive or swap")
    if first_input==1:
        print("Choose the attack mode:\n 1.Normal Attack \n 2.{} attack \n 3.Super Attack".format(Andrei.current_pokemon.type))
        second_input=int(input())
        Andrei.challenge(Andrei.current_pokemon,Trainer_number.current_pokemon,second_input)
    if first_input==2:
        print("Avaible items:")
        poz=0
        for elementul2 in Andrei.items:
            poz+=1
            print(str(poz)+".{}".format(elementul2.name),end=' ')
        print("\n Choose item:")
        second_input=int(input())
        print("Avaible Companions:")
        for i in range(len(Andrei.pokemons)):
            print(str(i+1)+".{}".format(Andrei.pokemons[i].name),end=" ")
        print("\nYour curren companion is : {}\n Choose Companion:".format(Andrei.current_pokemon.name))
        third_input=int(input())
        Andrei.activate_item(Andrei.items[second_input-1],Andrei.pokemons[third_input-1])
    if first_input==3 or Andrei.current_pokemon.state=="Down":
        print("Avaible Companions")
        activ_ones=0
        lst_of_activ_ones=[]
        for pokemon in Andrei.pokemons:
            if pokemon.state=="Good" and pokemon!=Andrei.current_pokemon:
                activ_ones+=1
                lst_of_activ_ones.append(pokemon)
                print(str(activ_ones)+".{} with: Attack Power:{} Defense:{} Hp:{} Type:{}".format(pokemon.name,pokemon.power,pokemon.defense,pokemon.hp,pokemon.type))
        if len(lst_of_activ_ones)>0:
            second_input=int(input())
            print("You swaped {} for {}".format(Andrei.current_pokemon.name,lst_of_activ_ones[second_input-1].name))
            Andrei.swap_pokemon(Andrei.current_pokemon,lst_of_activ_ones[second_input-1])
        else:
            print("You have no other avaible pokemon")
             
    if Trainer_number.current_pokemon.state=="Good":
          if Trainer_number.current_pokemon.hp<Trainer_number.current_pokemon.max_health/3 and Trainer_number.items.count(heal)>0:
              for nani in Trainer_number.items:
                if type(nani)==HealItem:
                    Trainer_number.activate_item(nani,Trainer_number.current_pokemon)
          else:
              lst=[1,2,3,1,1,1,1,1,1,2,2,1,1,2,2,2,1,1,2,1]
              Trainer_number.challenge(Trainer_number.current_pokemon,Andrei.current_pokemon,random.choice(lst))
    elif Trainer_number.current_pokemon.state=="Down":
      ok=0
      for i in Trainer_number.items:
          if type(i)==ReviveItem:
              ok=1
              Trainer_number.activate_item(i,Trainer_number.current_pokemon)
      if ok == 0 :
          for i in Trainer_number.pokemons:
              if i.state=="Good":
                  print("{} swaped {} with {}".format(Trainer_number.name,Trainer_number.current_pokemon.name,i.name))
                  Trainer_number.swap_pokemon(Trainer_number.current_pokemon,i)
                  break
  if Andrei.Trainer_Not_Down()==False:
    print("You lost the chalenge")
    break
  else:
    Andrei.find_pokemon()
      
if Andrei.Trainer_Not_Down()==True:
    print("Good job, you won the game, thanks so much for playing!")
