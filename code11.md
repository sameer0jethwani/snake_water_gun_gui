from PIL import Image,ImageTk
import requests
from io import BytesIO
import tkinter
import random
from win32com.client import Dispatch

s=Dispatch("SAPI.Spvoice")

root = tkinter.Tk()
root.title('snake , water, gun')
root.geometry("1920x1080")
option1 = ["snake", "water", "gun"]
com1 = random.choice(option1)


def snake1():
    user_enter1=option1[0]
    if com1==option1[0]:
        a=tkinter.Label(root,text=f"draw, because you and computer both choosed {user_enter1}",font=("Arial", 23))
        a.grid(column=3,row=1)
        s.Speak("draw")

    elif com1 == option1[1]:
        b=tkinter.Label(root,text=f"you won , beacuse you choosed {user_enter1} and computer choosed {com1}",font=("Arial", 23))
        b.grid(column=3,row=1)
        s.Speak("you won")

    elif com1 == option1[2]:
        c=tkinter.Label(root,text=f"you lost , beacuse you choosed {user_enter1} and computer choosed {com1}",font=("Arial", 23))
        c.grid(column=3,row=1)
        s.Speak("you lost")



def water1():
    global user_enter1
    user_enter1 = option1[1]
    if com1==option1[1]:
        a=tkinter.Label(root,text=f"draw, because you and computer both choosed {user_enter1}",font=("Arial", 23))
        a.grid(column=3,row=2)
        s.Speak("draw")
    elif com1 == option1[2]:
        b=tkinter.Label(root,text=f"you won , beacuse you choosed {user_enter1} and computer choosed {com1}",font=("Arial", 23))
        b.grid(column=3,row=2)
        s.Speak("you won")
    elif com1 == option1[0]:
        c=tkinter.Label(root,text=f"you lost , beacuse you choosed {user_enter1} and computer choosed {com1}",font=("Arial", 23))
        c.grid(column=3,row=2)
        s.Speak("you lost")


def gun1():
    global user_enter1
    user_enter1 = option1[2]
    if com1==option1[2]:
        a=tkinter.Label(root,text=f"draw, because you and computer both choosed {user_enter1}",font=("Arial", 23))
        a.grid(column=3,row=3)
        s.Speak("draw")
    elif com1 == option1[0]:
        b=tkinter.Label(root,text=f"you won , beacuse you choosed {user_enter1} and computer choosed {com1}",font=("Arial", 23))
        b.grid(column=3,row=3)
        s.Speak("you won")
    elif com1 == option1[1]:
        c=tkinter.Label(root,text=f"you lost , beacuse you choosed {user_enter1} and computer choosed {com1}",font=("Arial", 23))
        c.grid(column=3,row=3)
        s.Speak("you lost")


url1 = "https://cdn.iconscout.com/icon/premium/png-256-thumb/snake-94-718911.png"
response1 = requests.get(url1)
img1 = ImageTk.PhotoImage(Image.open(BytesIO(response1.content)))
panel1 = tkinter.Button(root, image = img1,height=300,width=300,command=snake1)
panel1.grid(column=0,row=1)

url2 = "https://ak6.picdn.net/shutterstock/videos/19476076/thumb/1.jpg"
response2 = requests.get(url2)
img2 = ImageTk.PhotoImage(Image.open(BytesIO(response2.content)))
panel2 = tkinter.Button(root, image = img2,height=300,width=300,command=water1)
panel2.grid(column=0,row=2)

url3 = "https://t3.ftcdn.net/jpg/02/22/86/92/500_F_222869257_aGwW0bJfbzRqiJaBJUyKBm6veRqzUALu.jpg"
response3 = requests.get(url3)
img3 = ImageTk.PhotoImage(Image.open(BytesIO(response3.content)))
panel3 = tkinter.Button(root, image = img3,height=300,width=300,command=gun1)
panel3.grid(column=0,row=3)

info3 = tkinter.Label(root,text="click on the picture to choose \n\n\n\nrules:\n gun is drown in water \n gun will kill snake\n snake will drink water ",font=("Arial", 15))
info3.grid(column=2,row=1)


root.mainloop()
