# Övning: Login Bootcamp

Hej! I detta bootcamp kommer ni inledningsvis får träna på veckans ämnen separat, för att i slutändan kunna skapa ett formulär med funktionalitet för att både inloggning och registrering.

## Formulärvalidering

Skapa ett kontaktformulär i HTML (styling är valfritt) innehållandes fälten Namn, Telefon, Email, Meddelande, samt en checkbox där man som användare bekräftar att man läst och förstått att ens data kan komma att sparas.
Skapa sedan en funktion som kickas igång när formuläret skickas. Testa att lyssna både efter 'submit'-händelsen på formuläret, samt 'click'-händelsen på knappen. Är det någon skillnad?
Glöm inte att förhindra formulärets default-beteende!

Spara ner datan från formuläret i ett objekt och logga ut ditt objekt i konsollen.

## Felhantering

Döp om din funktion till validateForm(). Skapa sedan en s.k. try/catch-sats där du i try-blocket kontrollerar följande:
* Namn måste bestå av minst 5 tecken
* Antingen telefon ELLER email måste fyllas i, båda fälten får inte vara tomma (men man behöver inte fylla i båda)
* Om telefon är ifyllt så måste det måste vara ett nummer (gör detta input-fält till type="text" och använd parseInt i kombination med isNaN() för att kontrollera detta)
* Meddelande får inte vara tomt
* Checkboxen måste vara "checked"

Om ett fel uppstår så skall ni kasta ett felmeddelande som ni visar för användaren på skärmen samt returnera ```false```. Om inget fel uppstår returnerar ni ```true```.

**Levelup!**

Vid fel så kastar ni istället ett objekt innehållandes ett rimligt felmeddelande samt referensen till det element där felet uppstått. När ni tar emot felet i ert catch-block så kan ni nu både ge användaren feedback, samt visa i vilket element felet uppstått ("element".focus() exempelvis).

## LocalStorage #1

Om validateForm() returnerar ```true``` så sparar ni meddelandet (endast själva meddelandet) i localStorage under nyckeln "message". Öppna inspekteraren, klicka på "Application" för att se om meddelandet sparats.

## LocalStorage #2

Skapa en funktion som heter getMessageFromLocalStorage(). Inuti funktionen så hämtar ni "message" från localStorage och returnerar resultatet. Logga ut returen från getMessageFromLocalStorage() i konsollen.

## LocalStorage #3 **Levelupp!**

Om validateForm() returnerar ```true``` så skall ni nu spara ner all data från formuläret i ett objekt som skickas till localStorage. Skapa även en funktion som hämtar objektet från localStorage och skriver ut värdet för nyckeln "name" i konsollen. (Tänk på att localStorage endast lagrar strängar!).

## LocalStorage #4 **Levelup!**

Gör om #3 men nu skall ni istället för att endast spara ner ert senast godkända objekt spara alla objekt som godkänts. Detta gör ni genom att lägga in objekten i en array som lagras i localStorage. Inför varje nytt godkänd meddelande behöver ni först hämta arrayen, pusha det nya objektet, innan ni återigen skickar er array till localStorage.

## Inloggning och Registreringsformulär

### Steg 1

Skapa upp två riktigt snygga formulär, ett för inloggning och ett för registrering. Från början skall endast inloggningsformuläret synas, och på respektive formulär skall det finnas en knapp som leder till det andra. **Exempel:** på inloggningsformuläret skall det knappen "Registrera dig" finnas, och vid klick på knappen så försvinner inloggningen och registreringen dyker upp istället.
Inloggningen skall bestå av fälten "username" och "password", medans registreringen skall bestå av fälten "username", "password", "password again", samt en checkbox där man godkänner villkoren.

### Steg 2

Skapa funktionerna validateRegistration() och validateLogin().
För validateRegistration() gäller följande:

* username måste bestå av minst 6 tecken
* username får inte vara upptaget
* password måste bestå av minst 8 tecken
* password och password again måste vara identiska
* checkboxen måste vara checked

Om registrering lyckas så skickar ni upp användaren till arrayen "users" som skall lagras i localStorage.

För validateLogin() gäller följande:

* username måste tillhöra en användare i databasen (tips: array-metoden .some())
* om en användare hittas så måste den användarens lösenord överensstämma med password

Om validateLogin lyckas så döljs formuläret, och information om den inloggade användaren visas på skärmen (exempelvis "Välkommen Jesper!").

### Steg 3 **Levelup!**

Vid lyckad inloggning skall du nu "redirecta" användaren till en helt ny sida (kolla upp window.location.href), där användaren välkomnas av texten "Välkommen <username>".
Fundera på hur du kan använda localStorage för att åstadkomma detta.

