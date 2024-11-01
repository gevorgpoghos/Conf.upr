## Задача 1
Реализовать на Jsonnet приведенный ниже пример в формате JSON. Использовать в реализации свойство программируемости и принцип DRY.
![Screenshot 2024-11-01 091606](https://github.com/user-attachments/assets/412689db-4f87-4ae6-b0f0-5f07af6abdc3)

```
{
  groups: [
    std.join("-", ["ИКБО", std.toString(i), "20"]) for i in std.range(1, 24)
  ],

  students: [
    { age: 19, group: "ИКБО-4-20", name: "Иванов И.И." },
    { age: 18, group: "ИКБО-5-20", name: "Петров П.П." },
    { age: 18, group: "ИКБО-5-20", name: "Сидоров С.С." },
    { age: 20, group: "ИКБО-6-20", name: "Кузнецов К.К." } // новый студент
  ],

  subject: "Конфигурационное управление"
}
```
```
{
  "groups": [
    "ИКБО-1-20",
    "ИКБО-2-20",
    "ИКБО-3-20",
    "ИКБО-4-20",
    "ИКБО-5-20",
    "ИКБО-6-20",
    "ИКБО-7-20",
    "ИКБО-8-20",
    "ИКБО-9-20",
    "ИКБО-10-20",
    "ИКБО-11-20",
    "ИКБО-12-20",
    "ИКБО-13-20",
    "ИКБО-14-20",
    "ИКБО-15-20",
    "ИКБО-16-20",
    "ИКБО-17-20",
    "ИКБО-18-20",
    "ИКБО-19-20",
    "ИКБО-20-20",
    "ИКБО-21-20",
    "ИКБО-22-20",
    "ИКБО-23-20",
    "ИКБО-24-20"
  ],
  "students": [
    {
      "age": 19,
      "group": "ИКБО-4-20",
      "name": "Иванов И.И."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Петров П.П."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Сидоров С.С."
    },
    {
      "age": 20,
      "group": "ИКБО-6-20",
      "name": "Кузнецов К.К."
    }
  ],
  "subject": "Конфигурационное управление"
}
```

## Задача 2
Реализовать на Dhall приведенный ниже пример в формате JSON. Использовать в реализации свойство программируемости и принцип DRY.

![Screenshot 2024-11-01 093729](https://github.com/user-attachments/assets/2e440116-1e5d-4c9d-88c3-fa0eada0578a)
![Screenshot 2024-11-01 093740](https://github.com/user-attachments/assets/be65c61e-e9ec-44ad-a51a-941f2d2636ae)
```
let List/groups =
      [ "ИКБО-12-20"
      , "ИКБО-13-20"
      , "ИКБО-14-20"
      , "ИКБО-15-20"
      , "ИКБО-16-20"
      , "ИКБО-17-20"
      , "ИКБО-18-20"
      , "ИКБО-19-20"
      , "ИКБО-20-20"
      , "ИКБО-21-20"
      , "ИКБО-22-20"
      , "ИКБО-23-20"
      , "ИКБО-24-20"
      , "ИКБО-25-20"
      ]
let students =
      [ { age = 18, group = "ИКБО-10-20", name = "Василев И.И." }
      , { age = 18, group = "ИКБО-5-20", name = "Петров П.П." }
      , { age = 18, group = "ИКБО-20-20", name = "Сидоров С.С." }
      , { age = 18, group = "ИКБО-10-20", name = "Смирнов А.А." }
      ]
let subject = "Конфигурационное управление"
in { groups = List/groups, students = students, subject = subject }
```
```
groups:
  - "ИКБО-12-20"
  - "ИКБО-13-20"
  - "ИКБО-14-20"
  - "ИКБО-15-20"
  - "ИКБО-16-20"
  - "ИКБО-17-20"
  - "ИКБО-18-20"
  - "ИКБО-19-20"
  - "ИКБО-20-20"
  - "ИКБО-21-20"
  - "ИКБО-22-20"
  - "ИКБО-23-20"
  - "ИКБО-24-20"
  - "ИКБО-25-20"
students:
  - age: 18
    group: "ИКБО-10-20"
    name: "Василев И.И."
  - age: 18
    group: "ИКБО-5-20"
    name: "Петров П.П."
  - age: 18
    group: "ИКБО-20-20"
    name: "Сидоров С.С."
  - age: 18
    group: "ИКБО-10-20"
    name: "Смирнов А.А."
subject: "Конфигурационное управление"
```

## Задача 3
Для решения дальнейших задач потребуется программа на Питоне, представленная в методичке к 3 практической работе. Разбираться в самом языке Питон при этом необязательно. Реализовать грамматики, описывающие следующие языки (для каждого решения привести БНФ). Код решения должен содержаться в переменной BNF:

Язык нулей и единиц. 10 100 11 101101 000

![Screenshot 2024-11-01 094228](https://github.com/user-attachments/assets/8496ce1b-4eaa-4eb9-844d-73cf11a24a5c)

```
import random
def parse_bnf(text):
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar
def generate_phrase(grammar, start):
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join(generate_phrase(grammar, name) for name in seq)
    return str(start)
BNF = """
E = "0" E | "1" E | ""
"""
for i in range(10):
    phrase = generate_phrase(parse_bnf(BNF), 'E')
    if phrase:
        print(phrase.replace('"', ''))
```

## Задача 4
Язык правильно расставленных скобок двух видов.

(({((()))})) {} {()} () {}

![Screenshot 2024-11-01 094504](https://github.com/user-attachments/assets/7fcd4bc4-a53c-4f5a-892e-0042e4e9adb8)


```
import random
def parse_bnf(text):
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar
def generate_phrase(grammar, start):
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join(generate_phrase(grammar, name) for name in seq)
    return str(start)
BNF = '''
E = "()" | "{}" | E E | "(" E ")" | "{" E "}"
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))
```

## Задача 5
Язык выражений алгебры логики. ((~(y & x)) | (y) & ~x | x) & x у & ~ (у) ((y) & y & ~y) ~x ~((x) & y | (y) | (x)) & x | x | (y & ~y)

![Screenshot 2024-11-01 094703](https://github.com/user-attachments/assets/c385dadf-5b62-484a-b03f-87ba96d5873d)


```
import random
def parse_bnf(text):
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar
def generate_phrase(grammar, start):
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join(generate_phrase(grammar, name) for name in seq)
    return str(start)
BNF = '''
E = "~" E | E "&" E | E "|" E | "(" E ")" | "x" | "y"
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))
```
