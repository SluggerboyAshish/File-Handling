import os
print("-"*40)
print("********* WELCOME TO STUDENT MANAGEMENT SYSTEM *******")
print("-"*40)

# def View():
#     if (os.path.exists("database.txt")):
#         obj=open("database.txt","r")
#         res=obj.read()
#         print(res)
#     else:
#         obj=open("database.txt","w")
#         obj.close()
def View():
    try:
        obj=open("database.txt","r")
        res=obj.read()
        print(res)
    except:
        print("File not Found")
        obj=open("database.txt","w")
        print("File Now created")

def add():
    new=input("Enter the name of the new student Name:")
    obj=open("database.txt","a")
    obj.write(f"{new}\n")
    obj.close()

def remove():
    a=input("Enter the Name you want to Search ")
    obj=open("database.txt","r")
    res=obj.read()
    word=res.split()
    if a in word:
        word.remove(a)
        print(word)
        obj=open("database.txt","w")
        listToStr = '\n'.join([str(elem) for elem in word])
        obj.write(f"{listToStr}\n")
        obj.close()
        
            
    else:
        print("Name Not Found")
    # a=input("Enter the Name you want to delete ")
    # obj=open("database.txt","r")
    # res=obj.readlines()
    # obj=open("database.txt","w")
    # for line in res:
    #     if line.strip("\n")!=a:
    #         obj.write(line)
            
    
def search():
    a=input("Enter the Name you want to Search ")
    obj=open("database.txt","r+")
    res=obj.read() 
    word=res.split()
    if a in word:
        print("Name Present")
    else:
        print("Name Not Found")


while (True):

    ch=int(input("Please Choose Any one Options: \n 1. To View Student list \n 2. To Add new list \n 3. To remove the Data \n 4. To search data \n 5. EXIT \n Enter your choice:"))
    if ch==1:
        View()
    elif ch==2:
        add()
    elif ch==3:
        remove()
    elif ch==4:
        search()
    elif ch==5:
        break
    else : 
        print("Wrong Input")
    yn=input("Do you want to continue y/n :")
    if yn=="y":
        continue
    else:
        break
