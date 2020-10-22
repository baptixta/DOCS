
# :snake: Python

### Utilizado para comentar o código

""" triplas aspas são utilizadas para comentários
	no código de várias linhas"""

### escrever algo
print "Hello World"

### Números em PYTHON
int - float - complex

### Deixar o usuário escrever
EXEMPLO
nome = input("What is your name? ")
quest = input("What is your quest? ")
cor = input("What is your favorite color? ")

### declarar variável e atribuir n° a ela
exemplo = 10

### Pular linha
\n

### Formatar Casas decimais
{:.1f}
{:.2f}

### Strings - podem conter números, letras e símbolos - escrito entre aspas
nome = "John"
numero = "10"
### Métodos de String
.capitalize()
.count()
.startwith()
.endswith()
.split()
replace()



### Concatenando Strings
EXEMPLO
string_1 = "pão"
string_2 = "padaria"
print ("João comprou {} na {}".format(string_1, string_2))

### Métodos de String
len() - mostra o n° de letras da String
EXEMPLO
parrot = "teste"
print len(parrot)

lower() - deixa a string em letra minúscula
EXEMPLO
parrot = "teste"
print parrot.lower()

upper() - deixa a string em letra maiúscula
EXEMPLO
parrot = "teste"
print parrot.upper()

str() - transforma métodos não-String em Strings
EXEMPLO
pi = 3.14
print str(pi)

### boolean - variável lógica - verdadeiro ou falso
exemploa = True
exemplob = False

### WhiteSpace - espaçamento é importante
utilização de 2 a 4 espaços no código

### Operações Aritméticas - exemplos
adicao = 72 + 23
subtração = 108 - 204
multiplicacao = 108 * 0.5
divisao = 108 / 9
potenciação = 2**2
modulo = 3%2

### CONDICIONAIS
Equal to (==)
Not equal to (!=)
Less than (<)
Less than or equal to (<=)
Greater than (>)
Greater than or equal to (>=)

### Chamar alguma letra da String
letra = "TESTE"[1]

### iMPORTAR DATA
from datetime import datetime

### DATA ATUAL
datetime.now()

### DATAS/HORAS ESPECÍFICAS
now = datetime.now()
current_year = now.year
current_month = now.month
current_day = now.day
current_hour = now.hour
current_minute = now.minute
current_second = now.second

### OPERADORES LÓGICOS
and - or - not
not - visto primeiro, and - visto em seguida, or - visto por último

### FUNÇÃO - CONTROL FLOW
def functionname( parameters ):
   "function_docstring"
   function_suite
   return [expression]

### FUNÇÃO - IF/ELSE
EXEMPLO
def clinic():
    print "You've just entered the clinic!"
    print "Do you take the door on the left or the right?"
    answer = raw_input("Type left or right and hit 'Enter'.").lower()
    if answer == "left" or answer == "l":
      print "This is the Verbal Abuse Room, you heap of parrot droppings!"
    elif answer == "right" or answer == "r":
      print "Of course this is the Argument Room, I've told you that already!"
    else:
      print "You didn't pick left or right! Try again."
      clinic()

clinic()

EXEMPLO 2
### # Make sure that the_flying_circus() returns True
def the_flying_circus():
    if 5>4 and 4 > 3:    # Start coding here!
        # Don't forget to indent
        # the code inside this block!
        return True
    elif 3==3:
        # Keep going he
