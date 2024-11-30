# pw_gen
Pw_generator

import random
import string



def generate(länge):
    passwort = string.ascii_letters + string.digits + string.punctuation
    ##Diese Zeile ist erforderlich, da sonst das generierte Passwort ab ":" nicht richtig im weiteren Verlauf zugeordnet wird.
    passwort = passwort.replace(":", ";") 
    return ''.join(random.choice(passwort)for i in range(länge))

def passwortspeichern():
    with open("pwd.txt" , "a")as file:
        passwortliste = {}
        anbieter = input("Welchen Anbieter wollen Sie speichern")
        passwortliste[anbieter]=generate(16)
        file.write(f"{anbieter}:{generate(16)}+\n")
        print(passwortliste)
        return passwortliste


def passwoerter_anzeigen(anbieter):
    passwortliste3 = {}
    with open("pwd.txt" , "r")as file:
        for line in file:
            elemente = line.split(":")
            passwortliste3[elemente[0]] = elemente[1]
        print(passwortliste3[anbieter])
#####Muss noch bearbeitet werden######Klappt nicht
def passwoert_loeschen(anbieter):
    passwortliste3 = {}
    with open("pwd.txt", "a") as file:
        for line in file:
            elemente = line.split(":")
            passwortliste3[elemente[0]] = elemente[1]
        file.write(passwortliste3.pop(anbieter))

#passwortspeichern()
loeschen_anbieter = input("Lösche einen Anbieter!")
passwoert_loeschen(loeschen_anbieter)

#eingabe_anbieter = input("Welchen Anbieter möchtes du abrufen?")
#passwoerter_anzeigen(eingabe_anbieter)
