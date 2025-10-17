``` python
print("Привет, данная программа может зашифровать и расшифровать текст с помощью шифра Цезаря. \nДавай попробуем!")
print()

def encrypt_caesar():
  while True:
    print()
    print("1) Зашифровать \n2) Расшифровать")
    print()
    num = input("Что делаем?: ")
    print()
    if not num.isdigit():
      print()
      print("Ошибка: введите цифру!")
      continue
    elif num != "1" and num != "2":
      print()
      print("Ошибка: введите 1 или 2!")
      continue
      
    print("1) Русский \n2) Английский")
    print()
    language = input("Введите язык: ")
    if not language.isdigit():
      print()
      print("Ошибка: введите цифру!")
      continue
    elif language != "1" and language != "2":
      print()
      print("Ошибка: введите 1 или 2!")
      continue
      
    print()
    n = input("Введите сдвиг:  ")
    if not n.lstrip('-').isdigit():
      print()
      print("Ошибка: сдвиг должен быть числом!")
      continue
    n = int(n) 
    print()
    
    text = input("Введите текст: ")
    if num == "1":
      shift = n
    else:
      shift = -n

    
    #валидация алфавита
    has_ru = False
    has_en = False

    for char in text:
      if ("А" <= char <= "Я") or ('а' <= char <= 'я') or (char in 'Ёё'):
        has_ru = True
      if ('A' <= char <= 'Z') or ('a' <= char <= 'z'):
        has_en = True
      
    if has_ru and has_en:
      print()
      print("Ошибка: в тексте смешаны русские и английские буквы.")
      continue

    if language == "1" and has_en:
      print()
      print("Ошибка: выбран русский язык, но в тексте есть английские буквы.")
      continue

    if language == "2" and has_ru:
      print()
      print("Ошибка: выбран английский язык, но в тексте есть русские буквы.")
      continue

   
    result = ""
    
    for symbol in text:
      if symbol.isalpha(): #если буква
          if int(num) == 1: #зашифровать
            if int(language) == 1: #русский
              if symbol in 'Ёё':
                result += symbol
                continue
              
              code = ord(symbol) + shift
              if symbol.islower():
                while code > ord("я"):
                  code -= 32
                while code < ord("а"):
                  code += 32
              else:
                while code > ord("Я"):
                  code -= 32
                while code < ord("А"):
                  code += 32 
              
              result += chr(code)
                  
            elif int(language) == 2: #английский
              code = ord(symbol) + shift
              if symbol.islower():
                while code > ord("z"):
                  code -= 26 
                while code < ord("a"):
                  code += 26
              else:
                while code > ord("Z"):
                  code -= 26
                while code < ord("A"):
                  code += 26
              
              result += chr(code)            
    
    
          elif int(num) == 2: #расшифровать
            if int(language) == 1: #русский
              if symbol in 'Ёё':
                result += symbol
                continue
              
              code = ord(symbol) + shift
              if symbol.islower():
                while code < ord("а"):
                  code += 32
                while code > ord("я"):
                  code -= 32
              else:
                while code < ord("А"):
                  code += 32
                while code > ord("Я"):
                  code -= 32
              
              result += chr(code)
                
            elif int(language) == 2: #английский
              code = ord(symbol) + shift
              if symbol.islower():
                while code < ord("a"):
                  code += 26
                while code > ord("z"):
                  code -= 26              
              else:
                while code < ord("A"):           
                  code += 26
                while code > ord("Z"):
                  code -= 26
              
              result += chr(code)          
      else:
        result += symbol
    print()
    print(f'Ответ: {result}')  
    break

encrypt_caesar()
print()

while True:
  print()
  print("Хотите попробовать еще раз? \n1) Да \n2) Нет")
  print()
  yn = input("Выберите цифру: ")
  print()
  if yn.isalpha():
    print("Ошибка: введите цифру!")
    continue
  elif int(yn) == 1:
    encrypt_caesar()
  elif int(yn) == 2:
    print("До свидания!")
    break
  else:
    print("Ошибка: введите 1 или 2!")
    continue
```
