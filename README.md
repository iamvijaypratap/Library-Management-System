# Library-Management-System
import datetime 
from datetime import timedelta 
curr_date = datetime.datetime.now()
formated_date = curr_date.strftime("%A %d %b %Y ,  %I : %M %p")
new_date = curr_date+timedelta(30)
formated_new_date = new_date.strftime("%A %d %b %Y , %I : %M %p")
class Library:
    def __init__(self,list):
        self.book = list
    def DisplayAvailableBook(self):
        print("Books Present in this library are :")
        for book in self.book:
            print(" *" + book)
    def BorrowBook(self,bookname):
        if bookname in self.book:
            print(f" {bookname} Book has been issued to you on {formated_date} . Please Return Within 30 Days ! \n Last date To Return Is {formated_new_date} ")
            self.book.remove(bookname)
            return True
        else:
            print("Sorry, This book is either not available or has already been issued to someone else. Please wait until the book is available")
            return False
    def ReturnBook(self,bookname):
        self.book.append(bookname)
        print("Thanks for returning this book! Hope you enjoyed reading it. Have a great day ahead!")
class Student:
    def requestBook(self):
        self.book=input("Enter the name of the book you want to borrow: ")
        return self.book
    def returnBook(self):
        self.book=input("Enter the name of the book you want to return: ")
        return self.book

if __name__=="__main__":
     centralLibrary =Library(["Python Notes","JAVA","C BASIC","CLRS","c++","Ruby","Web Development"])
     student = Student()
     while(True):
        welcomeMsg = '''\n ====== Welcome to Central Library ======
        Please choose an option:
        1. List all the books
        2. Request a book
        3. Add/Return a book
        4. Exit the Library
        '''
        print(welcomeMsg)
        try:
           a = int(input("Enter Your Choice : "))
           if a==1:
              centralLibrary.DisplayAvailableBook()
           elif a==2:
              centralLibrary.BorrowBook(student.requestBook())
           elif a==3:
              centralLibrary.ReturnBook(student.returnBook())
           elif a==4:
              print("Thanks For Choosing Central Library  ")
              exit()
           else:
              print("Invalid Choice")
        except Exception as e:
            print("Invalid Choice! Please Choose From Given Options")

