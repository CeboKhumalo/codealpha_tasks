def will_you_be_saved():
    
    
    #displaying Message to user. 
    print("Welcome to my code!.\n This code will help you determine if you would have survived the sinking of the titanic.\n Based on the factors that, came into play that determined the survival of thousands on that fatefull night.")
    
    #holds the users final score.
    users_final_score = 0 

    #Requesting for user inforsmation.
    name_surname = str(input('Please enter your Name and Surname:'))
    age = int(input('Please enter your age:'))

    
    #confirming if the user enetered a valid age.
    while age < 0: 
        try:
            print("The age entered is invalid")
            age = int(input('Please enter a valid age:')) #allows user o eneter a valid age.
        except ValueError:
            print("Invalid input. Please enter a valid age.")
    print()

    #using users age to determine the likely hood of their survival.
    if age < 15:
        print(f" Dont worry {name_surname}, you will be our top priority.")
        users_final_score +=  10   
    else:
        print(f"{name_surname}, you are {age}! but let us hope you are at least important.")
        users_final_score +=  3
    print()


    
    #requesting users gender.
    print("(Male = 'xy', female = 'xx')")
    gender = str(input('PLease enter your sex:'))

    #using users gender to determine the likely hood of their survival.
    if gender == 'xx':
        print(f"Do not worry {name_surname}, you will be our top priority.")
        users_final_score +=  8
    else:
        print(f"{name_surname}, chances of you surviving are pretty slim.\n let us hope you are at least important or you know an officer.")
        users_final_score +=  3
    print()


    #determining the users language.
    print("How good is your english?\nEnter the number(1-3):\n1.Excellent\n2.Good\n3.Bad")
    lang = str(input("Enter here:"))

    #determining survival based on language//if user does not speak english, they will have difficulties comprehending instructions.
    if lang == '1' or lang == '2':
        print("Atleast you would be able to comprehend basic instruction")
        users_final_score +=  5
    else:
        print("Not being able to understand basic instruction would be an issue for you")
        users_final_score +=  3
    print()
    
    #confirming users social class.
    print("Please enter your 9-Diget, ticket number below")
    print("Your Ticket number should start with:\n 5999******\n 5888*****\n 5777*****")
    ticket_num = (input('Enter ticket number:'))

    #confirms if the ticket number entered is 9 digits long and has only digits.
    if len(ticket_num) != 9 or not ticket_num.isdigit(): 
        print("The Ticket number is invalid please try again below.")
        ticket_num = (input('Enter valid ticket number:')) #allows the user to enter a valid account number.
        if ticket_num.startswith('5999'): 
            print(f" Dont worry {name_surname},we do see here that you purchased a FIRST CLASS TICKET,\n you will be top priority.!")
            users_final_score +=  10 
        elif ticket_num.startswith('5888'):
            print(f" Hello {name_surname},we do see here that you purchased a SECOND CLASS TICKET,\n depending on who you know you can still be rescued!. ")
            users_final_score +=  6   
        elif ticket_num.startswith('5777'):
            print(f"Hello {name_surname},we do see here that you purchased our cheapest TICKET,\n do worry, we might not but dont lose hope yet!.")
            users_final_score +=  3
        print()
    else:       #checks the first digits of the ticket number, and displays relevant message to user depending on ticket class type.
        if ticket_num.startswith('5999'): 
            print(f" Dont worry {name_surname},we do see here that you purchased a FIRST CLASS TICKET,\n you will be top priority.!")
            users_final_score +=  10 
        elif ticket_num.startswith('5888'):
            print(f" Hello {name_surname},we do see here that you purchased a SECOND CLASS TICKET,\n depending on who you know you can still be rescued!. ")
            users_final_score +=  6   
        elif ticket_num.startswith('5777'):
            print(f"Hello {name_surname},we do see here that you purchased our cheapest TICKET,\n do worry, we might not but dont lose hope yet!.")
            users_final_score +=  3
    print()

    
    #determines users survival based on cabin location.
    print("Where is your Cabin located?.\nEnter the number(1-3):\n 1.Upper deck.\n 2.Middle deck.\n 3.Lower deck")
    cabin_location = str(input("Enter here:"))

    #displays message based on cabin location.
    if cabin_location == '1' :
        print("Chances of you surviving are high since you are located near the life boats.")
        users_final_score +=  5
    elif cabin_location == '2':
        print("Chances of you surviving are slightly lower since you are situated some distance between the life boats")
        users_final_score +=  3
    else: 
        print("Your chances of survival are pretty low.")
        users_final_score +=  1
    print()
                               

    #determining if the user is related to or friends with offcers on board.
    officers_dictionary = {
        438100: 'Captain Edward John Smith', 438201: 'Chief officer Henry Tingle Wilde',
        438302: '1st Officer William McMaster Murdoch', 438403: '2nd Officer Charles Herbert Lightoller',
        438504: '3rd Officer Herbert John Pitman', 438605: '4th Officer Joseph Groves Boxhall',
        438706: '5th Officer Harold Godfrey Lowe', 438807: '6th Officer James Paul Moody'
    }#internal dictionary of officers names, surnames and thier respective officer codes.
    
    print("Are you related to or friends with the Captain or one of the Officers on Board?")

     #control for loop.
    related_to_officers = (input("(yes or no):")) # allows the user to enter to loop if entered "yes".
    
    if related_to_officers == 'yes':
        officer_code_str = (input("Enter the 6-digit officer code"))
        while related_to_officers == 'yes':
            if len(officer_code_str) != 6 and not officer_code_str.isdigit(): #validate the officer code the user entered.
                    print("Invalid input. Please enter a 6-digit code containing only numbers.")
                    officer_code_str = (input("Enter the 6-digit officer code")) #allows the user to input the code again.
                    continue
            else
                officer_code = int(officer_code_str) #converts officer_code_str to "int" after validating the code .
                if officer_code in officers_dictionary: #confirms if the officer code entered is found in the internal dictionary
                    officer_name_surname = officers_dictionary[officer_code] #makes it easier to read.
                    print(f"Hey {name_surname}, because you know {officer_name_surname}, your chances of survival are looking good.") #displays message to user
                    users_final_score +=  5   
                    break
                else:
                    print("Officer code not found. chances of survival are slim.") #displays message to let the user know the code is not found
                    break 
    else:
        print("Your chances are looking quite slim")


    #displays to the user their score and if they will servive based on thier score.
    if users_final_score >=25:
        print(f" Hey {name_surname}, you have scored {users_final_score}, so meaning during the sinking of the titanic you were likey to survive.")
    else:
        print(f" {name_surname} you scored {users_final_score}, which means during the sinking of the titanic you would have not made it unfortunately,\n based on the factors the were in play that determined if one enters the life boat or not.")



#calling the main fuction.
will_you_be_saved()
