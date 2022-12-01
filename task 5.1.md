documents = [
        {"type": "passport", "number": "2207 876234", "name": "Василий Гупкин"},
        {"type": "invoice", "number": "11-2", "name": "Геннадий Покемонов"},
        {"type": "insurance", "number": "10006", "name": "Аристарх Павлов"}
      ]

directories = {
        '1': ['2207 876234', '11-2'],
        '2': ['10006'],
        '3': []
}

print ("=" *10, "Работа с документами" , "=" *10, end = '\n\n\n')

print ("p – people – команда, которая спросит номер документа и выведет имя человека, которому он принадлежит; " ,"s – shelf – команда, которая спросит номер документа и выведет номер полки, на которой он находится.", "l– list – команда, которая выведет список всех документов в формате passport ""2207 876234"" ""Василий Гупкин"";" ,
"a – add – команда, которая добавит новый документ в каталог и в перечень полок, спросив его номер, тип, имя владельца и номер полки, на котором он будет храниться.",
"q - выход" ,sep ='\n', end='\n') 

print('\n')


def pass_n(documents):
  number_doc= input("Введите номер документа: ")
  for doc in documents :
    if number_doc == doc["number"] :
      print('Владелец документа: ',(doc['name']),end= "\n\n")
      break
  else:
    print("Введен некорректный номер документа!Попробуйте заново.",end= "\n\n")


def num_direct_num_doc(doc,direct):
  answer = input("Введите номер документа")
  for a, n in directories.items():
    if answer in n :
      print(f'Документ под номером "{answer}" находится на полке {a}',end= "\n\n")
      break
  else:
    print("Введен некорректный номер документа!Попробуйте заново.", end= "\n\n")


def list_documents():
  for doc in documents:
    print(doc['type'],doc['number'],doc['name'], end= "\n\n")


def add_document(num_dir,add_doc):
  arg_shelf= input("Введите номер полки, в которой будет храниться номер документа: ")
  if arg_shelf in directories:
    for document in documents: 
      agr_type= input("Введите тип документа (type): ")
      arg_number= input("Введите номер документа (number): ")
      arg_name= input("Введите имя владельца (name): ")
      documents.append({"type": agr_type, "number": arg_number, "name": arg_name})
      directories[arg_shelf].append(arg_number)
      print('\n  Новые документы добавлены! ',end= "\n\n" )
      break
  else:
    print("Такой полки не существует,попробуйте заново", end= "\n\n")


def main():
  while True: 
    print('Возможные команды  (p,s,l,a,q): ', end= "\n\n" )
    comand = input('Введите название команды ')
 
    if comand == 'p':
      pass_n(documents)
    
    elif comand == 's':
      num_direct_num_doc(documents,directories)
    
    elif comand == 'l':
      list_documents()
      print(end="\n\n")
    
    elif comand == 'a':
      add_document(documents,directories)

    elif comand == 'q':
      print("**Завершение работы с программой**")
      break
    
    else: 
      print("Введена неверная команда", end= "\n\n")
main()  

  