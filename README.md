# AI-Fitness by MonoGameDeveloper

    import pyttsx3
    import speech_recognition as sr
    import datetime
    import os
    import time
    import requests
    import playsound
    import pyaudio

    engine = pyttsx3.init('sapi5')
    voices = engine.getProperty('voices')
    engine.setProperty('voice', voices[1].id)
    #mic = sr.Microphone(device_index=1)

    def speak(audio):
    	engine.say(audio)
	    engine.runAndWait()

    def wishMe():
	    hour = int(datetime.datetime.now().hour)
	    if hour>= 0 and hour<12:
		     speak("Good Morning Sir !")

	    elif hour>= 12 and hour<18:
		     speak("Good Afternoon Sir !")

	    else:
		     speak("Good Evening Sir !")

	    ainame =("Mirai")
	    speak("I am your Personal Assistant")
	    speak(ainame)
	    print(sr.Microphone.list_microphone_names())
	

    def excercise():
	    speak("Lets start with pushups first")
	    uname = ("Sir")
	    speak("Lets do 15 minutes pushups for starting")
	    speak(uname)
    	relax()
 #timeex()

    def relax():
        takeCommand()
        if 'Yes' in said or 'Done' in said:
                timeex()

    def timeex():
         hour = int(datetime.datetime.now().hour)
        if hour>= 18 and hour<=24:
                speak("Good job Sir")

    def takeCommand():
	
	     r = sr.Recognizer()
	
	     with sr.Microphone(device_index=1) as source:
		
		      print("Listening...")
		      r.pause_threshold = 1
		      audio = r.listen(source)
		      print('Listened : '+ r.recognize_google(audio))

	     try:
		     print("Recognizing...")
		     said = r.recognize_google(audio, language ='en-in')
		     print(f"User said: {said}\n")

	     except Exception as e:
		     print(e)
	     	print("Unable to Recognize your voice.")
		    print("Exception: " + str(e))
		    speak("Unable to Recognize your voice.")
		    return "None"
	
	return said

    if __name__ == '__main__':
	    clear = lambda: os.system('cls')
	
	clear()
	wishMe()
	excercise()
