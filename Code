import pyttsx3
import speech_recognition as sr
import datetime
import pyaudio
import wikipedia
import webbrowser
import os
import random

engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
engine.setProperty('voice',voices[0].id)

def speak(audio):
    engine.say(audio)
    engine.runAndWait()
def wishme():
    hour = int(datetime.datetime.now().hour)
    if hour>=0 and hour<12:
        speak("Good Morning! Master Rishab")
    elif hour>=12 and hour<18:
        speak("Good Afternoon! Master Rishab")
    else:
        speak("Good Evening! Master Rishab")
    speak("How can I serve you ?")

def takeCommand():
    #It takes command from microphone
    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening ......")
        r.pause_threshold = 1
        audio = r.listen(source)
    try:
        print("Recognizing....")
        query = r.recognize_google(audio, language = "en-in")
        print(f"User said : {query}")
    except Exception as e:
         print("Please say that again ......")
         return "None"
    return query

if __name__ == "__main__":
    wishme()
    while True:
        query = takeCommand().lower()
            if 'wikipedia' in query:
            speak("Searching Wikipedia ..... ")
            query = query.replace("wikipedia","")
            results = wikipedia.summary(query, sentences=2)
            speak("According to wikipedia")
            print(results)
            speak(results)
        elif 'open youtube' in query:
            chrome_path = "C:\Program Files (x86)\Google\Chrome\Application\chrome.exe"
            webbrowser.register('chrome', None, webbrowser.BackgroundBrowser(chrome_path))
            webbrowser.get('chrome').open("https://youtube.com")
        elif 'open google' in query:
            webbrowser.open("google.com")
        elif 'open supreme court website' in query:
            webbrowser.open("https://main.sci.gov.in/")
        elif 'play music' in query:
            music_dir = 'C:\\Users\\Rishabh\\Music'
            songs = os.listdir(music_dir)
            speak("playing music for you ")
            r_num = random.randrange(0,len(music_dir))
            os.startfile(os.path.join(music_dir,songs[r_num]))
        elif query == "stop" or query == "thank you":
            break
