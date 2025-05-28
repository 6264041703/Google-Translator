# Display the thinker from GUI method...
# Install googletrans and Translator from pip...

from tkinter import *            # library = tkinter & googletrans...
from tkinter import ttk
from tkinter import messagebox
from tkinter import Menu 
from googletrans import Translator, LANGUAGES     # class = Translator  # constant = LANGUAGE
import tkinter as tk
from langdetect import detect
from langcodes import *
from gtts import gTTS
import pyttsx3
import os
import tkinter as tk
from tkinter.ttk import Combobox
from tkinter.messagebox import showinfo
import speech_recognition as sr


def Translate():
    translator = Translator()
    translated=translator.translate(text= Input_text.get(1.0, END) , src = src_lang.get(), dest = dest_lang.get())

    Output_text.delete(1.0, END)
    Output_text.insert(END, translated.text)


root = Tk()
root.geometry('1535x790')

image_icon = PhotoImage(file = "Google_Translate_Icon.png")
root.iconphoto(False, image_icon)
# Make title and label... 
root.title("Project Kratos__Google Translator")

  
# Top Frame
Top_Frame = Frame(root, bg= "white smoke", width = 2000, height = 37 )
Top_Frame.place(x=0,y=0)

Top_Frame = Frame(root, bg= "White", width = 2000, height = 77 )
Top_Frame.place(x=0,y=37)

Top_Frame2 = Frame(root, bg= "ghost white", width = 2000, height = 111 )
Top_Frame2.place(x=0,y=114)

Top_Frame2 = Frame(root, bg= "White", width = 2000, height = 790 )
Top_Frame2.place(x=0,y=225)


language = list(LANGUAGES.values())


src_lang = ttk.Combobox(root, values= language, font="Cambria 14 italic", width =20)
src_lang.place(x=100,y=219)
src_lang.set('Choose Input Language')

dest_lang = ttk.Combobox(root, values= language, font="Cambria 14 italic", width =20)
dest_lang.place(x=1080,y=219)
dest_lang.set('Choose Output Language')

def DeclareWord_Count():
    Text_Content = Input_text.get("1.0", END)
    In_Text_Box = len (Text_Content)
    DisplayLabel.config(text = str(In_Text_Box - 1))

def Init_Count():
    DeclareWord_Count()
    DisplayLabel.after(1000, Init_Count)

def record():
    r = sr.Recognizer()


    with sr.Microphone() as source:
        r.pause_threshold = 2
        audio = r.listen(source)

        try:
            query = r.recognize_google(audio, language="en-IN")
        except Exception as e:
            showinfo(title='Error!', message=e)
            return "Nothing"
        return query


def clearTextInput():
    Input_text.delete("1.0","end")
    Output_text.delete("1.0","end")


engine = pyttsx3.init()
def speaknow():
    texts = Input_text.get (1.0, END)
    gender = gender_Combobox.get()
    speed = speed_Combobox.get()
    voices = engine.getProperty('voices')

    def setVoice():
        if gender == 'Male':
            engine.setProperty('voice', voices[0].id)
            engine.say(texts)
            engine.runAndWait()
            
        else:
            engine.setProperty('voice', voices[1].id)
            engine.say(texts)
            engine.runAndWait()

    if (texts):                                  
        if (speed== 'Fast'): 
            engine.setProperty('rate', 250)
            setVoice()
        elif (speed == 'Normal'):
            engine.setProperty('rate', 150)
            setVoice()
        else:
            engine.setProperty('rate', 50)
            setVoice()        


Label(root, text="G", font="Corbel 25 ", bg='White', foreground="blue").place(x=100,y=55)
Label(root, text="o", font="Corbel 25 ", bg='White', foreground="red").place(x=122,y=55)
Label(root, text="o", font="Corbel 25 ", bg='White', foreground="yellow").place(x=141,y=55)
Label(root, text="g", font="Corbel 25 ", bg='White', foreground="blue").place(x=160,y=55)
Label(root, text="l", font="Corbel 25 ", bg='White', foreground="green").place(x=179,y=55)
Label(root, text="e", font="Corbel 25 ", bg='White', foreground="red").place(x=187,y=55)

Label(root, text = "Translator", font = "Corbel 25 ", bg='White').place(x=220, y=55)
Label(root,text ="Project_Kratos", font = 'mistral 18', bg ='white smoke' , width = '20').pack(side = 'bottom')



def check_lang():
    if Input_text.compare("end-1c", "==", "1.0"):
        detect_lab.config(text="""Hey! You forgot to enter anything...""", font= "Cambria 16 italic")
    else:
        code = detect(Input_text.get(1.0, END))
        my_result = Language.make(language = code).display_name()
        detect_lab.config(text=f" Detected Language :- {my_result}", font="Cambria 16 italic")


detect_btn = Button(root, text="DETECT LANGUAGE",font= "Corbel 16 italic ", borderwidth=1, command= check_lang, bg= "ghost white", height=1)
detect_btn.place(x=120, y=530)

detect_lab = Label (root, text="", bg= "ghost white")
detect_lab.place(x=330, y=219)


Input_text = Text(root,font = 'Ebrima 20', height = 5, wrap = WORD, padx=5, pady=5, width = 45, undo = True, border=3, borderwidth=3)
Input_text.place(x=85,y = 250)
Input_text.insert(END,"")



Output_text = Text(root,font = 'Ebrima 20', height = 5, wrap = WORD, padx=5, pady= 5, width =45,border=3, borderwidth=3)
Output_text.place(x = 774 , y = 250)

arrow_btn = PhotoImage(file='C:/Users/dooma/OneDrive/Documents/Top_Projects/arr.png')
arrow_img = Label(image= arrow_btn)
trans_btn = Button(root, image= arrow_btn, background="ghost white", borderwidth= 1, command = Translate)
trans_btn.place(x = 655, y= 475)

DisplayLabel = Label(root, text="", font= ("Arial", 10),width=3, bg='white')
DisplayLabel.place(x=645, y=450)

Label(root,text ="/5000", font = 'arial 10 bold', bg ='white').place(x=675,y=450)

mic_btn = PhotoImage(file='C:/Users/dooma/OneDrive/Documents/Top_Projects/mic.png')
mic_img = Label(image = mic_btn)
mic_text = Button(root, image= mic_btn, bg='white smoke', borderwidth=1, command=lambda: Input_text.insert(END, record()))
mic_text.place(x=100, y=450)

Clear_Pi = PhotoImage(file='C:/Users/dooma/OneDrive/Documents/Top_Projects/close.png')
Clear_img = Label(image = Clear_Pi)
Clear_Btn=Button(root, image = Clear_Pi, bg = 'white smoke', borderwidth=1, command=clearTextInput).place(x= 680, y= 219)

Listen_Btn = PhotoImage(file='C:/Users/dooma/OneDrive/Documents/Top_Projects/listen.png')
Listen_img = Label(image=Listen_Btn)
speak_btn = Button(root, image = Listen_Btn, bg= "white smoke", borderwidth=1, command= speaknow)
speak_btn.place(x=180, y=450)

gender_Combobox = Combobox(root, value = ['Male', 'Female'], font = "arial 12 italic", state = 'r',width=6)
gender_Combobox.place(x=280,y=465)
gender_Combobox.set('Male')

speed_Combobox = Combobox(root, value = ['Fast', 'Normal', "Slow"], font = "arial 12 italic", state = 'r',width=6)
speed_Combobox.place(x=400,y=465)
speed_Combobox.set('Normal')



Init_Count()
root.update()
root.mainloop()        # call Tk() class
