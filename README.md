# 4 Pillars of OOPs


## 1. Encapsulation


```python
# Advanced Python
# OOPS

class BigObject:  # class
    # stored in memory
    pass


obj1 = BigObject()  # instantiate


# class blueprint or class by CamelCase
# diff instances objects

# Lets code our own
# Use of dander

class PlayerCharacter:
    def __init__(self, name, age):  # dander method/magic method
        self.name = name  # self refers to itself
        self.age = age  # attributes/methods

    def run(self): #method
        print('run')
        return 'yay running'


player2 = PlayerCharacter('dan', 25)  # shows the memory location
player3 = PlayerCharacter('andi', 28)
player3.attack = 300

print(player2.name)
print(player3.name)

print(player2.age)
print(player3.age)

print(player2.run())

print(player2)  # diff memory location
print(player3)  # diff memory location

print(player3.attack)
```

    dan
    andi
    25
    28
    run
    yay running
    <__main__.PlayerCharacter object at 0x7f8f0e7b8908>
    <__main__.PlayerCharacter object at 0x7f8f0e7b8898>
    300



```python
# Attributes and Methods
# oops good for organising than procedural

# help shows blueprint


class PlayerCharacter:
    # Class object attributes- not dynamic- its static
    # true for all object, cant be modified later
    membership = True

    def __init__(self, name, age):  # dander method/magic method
        if self.membership:
            self.name = name  # self refers to itself
            self.age = age  # attributes/methods

    def run(self):
        print('run')
        return 'yay running'


player2 = PlayerCharacter('dan', 25)  # shows the memory location
player3 = PlayerCharacter('andi', 28)
player3.attack = 300

print(player2.membership)
print(player3.membership)

```

    True
    True



```python
class PlayerCharacter:
    # Class object attributes- not dynamic- its static
    # true for all object, cant be modified later
    membership = True

    def __init__(self, name, age):  # dander method/magic method
        # constructor function, called each time we instantiate
        if PlayerCharacter.membership: # since its class object attribute
            self.name = name  # self refers to itself
            self.age = age  # attributes/methods

    def shout(self):
        # here Playercharacter.name wil not work here, why? its defined in constructor function
        print(f'hey my name is {self.name}')
        return 'I will return'


player2 = PlayerCharacter('dan', 25)  # shows the memory location
player3 = PlayerCharacter('andi', 28)

print(player2.shout())
print(player3.shout())
```

    hey my name is dan
    I will return
    hey my name is andi
    I will return


# Excersice


```python
# Given the below class:
class Cat:
    species = 'mammal'

    def __init__(self, name, age):
        self.name = name
        self.age = age


# 1 Instantiate the Cat object with 3 cats

tom = Cat('tom', 5)
dick = Cat('dick', 4)
harry = Cat('harry', 3)


# 2 Create a function that finds the oldest cat

def oldest_cat(*args):
    return max(args)


# 3 Print out: "The oldest cat is x years old.". x will be the oldest cat age by using the function in 2

print(f'The oldest cat is {oldest_cat(tom.age, dick.age, harry.age)} years old')
```

    The oldest cat is 5 years old



```python
class PlayerCharacter:
    # Class object attributes- not dynamic- its static
    # true for all object, cant be modified later
    membership = True

    def __init__(self, name, age):  # dander method/magic method
        # constructor function, called each time we instantiate
        if PlayerCharacter.membership:  # since its class object attribute
            self.name = name  # self refers to itself
            self.age = age  # attributes/methods

    def shout(self):
        # here Playercharacter.name wil not work here, why? its defined in constructor function
        print(f'hey my name is {self.name}')
        return 'I will return'

    @classmethod
    def add_things(cls, num1, num2):
        return num1 + num2


# WE CAN RUN THIS WITHOUT INSTANTIATION
# player1 = PlayerCharacter('dan', 25)


print(PlayerCharacter.add_things(4, 5))
```

    9



```python
class PlayerCharacter:
    # Class object attributes- not dynamic- its static
    # true for all object, cant be modified later
    membership = True

    def __init__(self, name, age):  # dander method/magic method
        # constructor function, called each time we instantiate
        if PlayerCharacter.membership:  # since its class object attribute
            self.name = name  # self refers to itself
            self.age = age  # attributes/methods

    def shout(self):
        # here Playercharacter.name wil not work here, why? its defined in constructor function
        print(f'hey my name is {self.name}')
        return 'I will return'

    @classmethod  # we use then when we care about accessing the attributes
    def add_things(cls, num1, num2):
        return cls('teddy', num1 + num2)

    @staticmethod  # we use then when we don't care about accessing the attributes
    def add_things2(num1, num2):
        return num1 + num2


# WE CAN RUN THIS WITHOUT INSTANTIATION
# player1 = PlayerCharacter('dan', 25)


player3 = PlayerCharacter.add_things(4, 5)
print(player3)  # shows the location in which its has been instantiated
print(player3.age)  # runs add_things
player4 = PlayerCharacter.add_things(90, 22)
print(player4)  # shows the location in which its has been instantiated
print(player4.age)  # runs add_things

```

    <__main__.PlayerCharacter object at 0x7f8f0e7c6550>
    9
    <__main__.PlayerCharacter object at 0x7f8f0e7c66d8>
    112


## 2. Abstraction


```python
# Hiding the info and only giving  to the info necessary, everything else is hidden in hood

class PlayerCharacter:
    def __init__(self, name, age):  # dander method/magic method
        self.name = name  # self refers to itself
        self.age = age  # attributes/methods

    def run(self):  # method
        return self

    def speak(self):
        print(f'my name is {self.name}, and I am {self.age} years old')


player1 = PlayerCharacter('dan', 25)
player1.speak()  # don't care about speak, just want it's access. THIS IS ABSTRACTION
```

    my name is dan, and I am 25 years old



```python
#  now what if

class PlayerCharacter:
    def __init__(self, name, age):  # dander method/magic method
        self.name = name  # self refers to itself
        self.age = age  # attributes/methods

    def run(self):  # method
        return self

    def speak(self):
        print(f'my name is {self.name}, and I am {self.age} years old')


player2 = PlayerCharacter('adi', 28)
player2.name = 'hacked'
player2.speak = 'haha- even this is hacked-  change in class, seems bad'
print(player2.speak)  # this is bad, class made with hard work and it can be changed
```

    haha- even this is hacked-  change in class, seems bad


## In python no true privacy
### _name -> private - request don't touch it / lest keep this private(no guarantee
### __ convention to not be modified -> dander


# 3. Inheritance


```python
# POWER OF INHERITANCE - common shared properties but something diff private property

class Hero:
    def sign_in(self):
        print('logged in')


class Wizard(Hero):
    def __init__(self, name, power):
        self.name = name
        self.power = power

    def attack(self):  # individual attack
        print(f'{self.name} magical power releasing at {self.power}')


class Archers(Hero):
    def __init__(self, name, arrows):
        self.name = name
        self.arrows = arrows

    def attack(self):  # individual attack
        print(f'{self.name} arrow power releasing at {self.arrows}')


class Ogre(Hero):
    def __init__(self, name, strength):
        self.name = name
        self.strength = strength

    def attack(self):  # individual attack
        print(f'{self.name} attacking with strength of {self.strength}')


invoker = Wizard('invoker', 500)
windranger = Archers('windranger', 100)
axe = Ogre('axe', 200)
invoker.attack()
windranger.attack()
axe.attack()

# isinstance checks 
print('lets check does invoker belogs to wizard class')
print(isinstance(invoker, Wizard))
print('lets check does invoker belogs to Hero class')
print(isinstance(invoker, Hero))
```

    invoker magical power releasing at 500
    windranger arrow power releasing at 100
    axe attacking with strength of 200
    lets check does invoker belogs to wizard class
    True
    lets check does invoker belogs to Hero class
    True


# 4. POLYMORPHISM


```python
# many forms

class DotaPlayer:
    def sign_in(self):
        print('logged in')

    def attack(self):
        print('Channeling ')


class Wizard(DotaPlayer):
    def __init__(self, name, power):
        self.name = name
        self.power = power

    def attack(self):  # individual attack
        DotaPlayer.attack(self)  # if we want to use DOTAPLAYER attack else skip this
        print(f'then we see {self.name} magical power releasing at {self.power}')


class Archer(DotaPlayer):
    def __init__(self, name, arrows):
        self.name = name
        self.arrows = arrows

    def attack(self):  # individual attack
        print(f'{self.name} arrow power releasing at {self.arrows}')


class Ogre(DotaPlayer):
    def __init__(self, name, strength):
        self.name = name
        self.strength = strength

    def attack(self):  # individual attack
        print(f'{self.name} attacking with strength of {self.strength}')


invoker = Wizard('invoker', 500)
windranger = Archer('windranger', 100)
axe = Ogre('axe', 200)

invoker.attack()  # runs
print(invoker.attack())  # prints whole this that method has as well as what it returns


def hero_attack(char):
    char.attack()


hero_attack(invoker)
hero_attack(windranger)
hero_attack(axe)
```

    Channeling 
    then we see invoker magical power releasing at 500
    Channeling 
    then we see invoker magical power releasing at 500
    None
    Channeling 
    then we see invoker magical power releasing at 500
    windranger arrow power releasing at 100
    axe attacking with strength of 200


# excersice


```python
#  calling method of class from subclass, requires __init__ to be defined in sub class also

class Hero(object):

    def __init__(self, email):
        self.email = email

    def sign_in(self):
        print('logged in')


class Wizard(Hero):
    def __init__(self, name, power, email):
        Hero.__init__(self, email)
        self.name = name
        self.power = power


invoker = Wizard('invoker', 500, 'invoker@dota2.com')
print(invoker.email)
```

    invoker@dota2.com



```python
# what is SUPER
class Hero(object):

    def __init__(self, email):
        self.email = email

    def sign_in(self):
        print('logged in')


class Wizard(Hero):
    def __init__(self, name, power, email):
        super().__init__(email) #  Using super
        self.name = name
        self.power = power


invoker = Wizard('invoker', 500, 'invoker@dota2.com')
print(invoker.email)
```

    invoker@dota2.com


#  introspection @ runtime


```python
#  dir
# what we have access to

class Hero(object):

    def __init__(self, email):
        self.email = email

    def sign_in(self):
        print('logged in')


class Wizard(Hero):
    def __init__(self, name, power, email):
        super().__init__(email) #  Using super
        self.name = name
        self.power = power


invoker = Wizard('invoker', 500, 'invoker@dota2.com')
print(dir(invoker))
```

    ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'email', 'name', 'power', 'sign_in']


# Dunder


```python
class Toy():
    def __init__(self, color, age):
        self.color = color
        self.age = age


action_figure = Toy('red', 0)
print(action_figure.__str__())
print(str(action_figure))
```

    <__main__.Toy object at 0x7fd20be4b748>
    <__main__.Toy object at 0x7fd20be4b748>



```python
#  We can do basic modificatio
#  Example


class Toy:
    def __init__(self, color, age):
        self.color = color
        self.age = age

    def __str__(self):
        return f'{self.color}'

    def __len__(self):
        return 5


action_figure = Toy('red', 0)
print(action_figure.__str__())
print(str(action_figure))
print(len(action_figure))

```

    red
    red
    5



```python
#  We can do basic modificatio
#  Example


class Toy:
    def __init__(self, color, age):
        self.color = color
        self.age = age
        self.my_dict = {'name': 'YOYO',
                        'has_pets': False,
                        }

    def __str__(self):
        return f'{self.color}'

    def __len__(self):
        return 5

    def __call__(self):
        return 'yes???'

    def __getitem__(self, item):
        return self.my_dict[item]


action_figure = Toy('red', 0)
print(action_figure.__str__())
print(str(action_figure))
print(len(action_figure))
print(action_figure())
print(action_figure['name'])

```

    red
    red
    5
    yes???
    YOYO


# Excersice


```python
class SuperList(list):

    def __len__(self):
        return 1000


super_list1 = SuperList()

print(len(super_list1))
super_list1.append(5)
print(super_list1[0])
print(issubclass(SuperList, list))  # ISSUBCLASS
print(issubclass(list, object))
super_list1.append(7)
super_list1.append(8)
super_list1.append(9)
super_list1.append(10)
print(super_list1[0])
print(super_list1[1])
print(super_list1[2])
print(super_list1[3])
print(super_list1[4])
print(super_list1)


```

    1000
    5
    True
    True
    5
    7
    8
    9
    10
    [5, 7, 8, 9, 10]


# Multiple inhetritance


```python
class DotaPlayer:
    def sign_in(self):
        print('logged in')


class Wizard(DotaPlayer):
    def __init__(self, name, power):
        self.name = name
        self.power = power

    def attack(self):  # individual attack
        return f'then we see {self.name} magical power releasing at {self.power}'


class Archer(DotaPlayer):
    def __init__(self, name, aim):
        self.name = name
        self.aim = aim

    def aim(self):  # individual attack
        return f'{self.name} arrow power releasing at {self.aim}'

    def run(self):
        return f'{self.name} running very fast'


class Ogre(Wizard, Archer):  # powers of both wizard and archer
    def __init__(self, name, power, aim):
        Wizard.__init__(self, name, power)  # but adding complexity
        Archer.__init__(self, name, aim)   # but adding complexity


axe = Ogre('axe', 500, 1000)
print(axe.run())
print(axe.power)
print(axe.aim)
print(axe.sign_in())

```

    axe running very fast
    500
    1000
    logged in
    None


# MRO methof resolution order


```python
class A:
    num = 10


class B(A):
    pass


class C(A):
    num = 1


class D(B, C):
    pass


print(D.num)
# why?

print(D.mro()) # AVOID OR BE CAUTIOUS OFF
print(D.__mro__)

```

    1
    [<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>]
    (<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>)



```python

```
