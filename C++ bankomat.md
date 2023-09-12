## C++
1.Inkludera de nödvändiga biblioteken <iostream> och <string> för att använda inmatning/utmatning och strängar i C++.

2.Definiera funktionen skapaKonto(). Inuti funktionen ber användaren om önskat användarnamn och lösenord, och sparar dem i motsvarande variabler. Sedan skrivs ett meddelande ut för att bekräfta att kontot har skapats.

3.Definiera funktionen login(). Inuti funktionen ber användaren om användarnamn och lösenord och sparar dem i motsvarande variabler.

4.Definiera funktionen visaMenu(). Inuti funktionen skapas variablerna choice och harKonto. harKonto initialiseras till 0 som standard och används senare för att kontrollera om användaren har ett konto.

5.Skriv ut en välkomsthälsning och be användaren ange sitt användarnamn och lösenord för att logga in. Användarnamnet och lösenordet lagras i motsvarande variabler.



6.En oändlig loop (do-while) startar där användaren kan göra olika transaktioner. En meny skrivs ut där användaren kan välja alternativ genom att ange en siffra. Beroende på användarens val utförs olika åtgärder: Dra ut pengar, sätta in pengar, visa saldo eller avsluta.

7.Efter varje åtgärd ombeds användaren välja om hen vill göra en annan transaktion. Om användaren väljer 1 fortsätter loopen och användaren kan välja ett nytt alternativ. Om användaren väljer 2 bryts loopen och programmet avslutas.

#include <iostream>
using namespace std;

float saldo = 0;
int annanUtdrag;
string användarNamn;
string Lösenord;

void skapaKonto() {
	cout << "Skapa ett konto" << std::endl;
	cout << "Ange önskat användarnamn: " <<  endl;
	cin >> användarNamn;
	cout << "Ange önskat lösenord: " << endl;
	cin >> Lösenord;
	cout << "Kontot har skapats." << endl;
}

void login() {
	cout << "Ange ditt användarnamn: " << endl;
	cin >> användarNamn;
	cout << "Ange ditt lösenord: " << endl;
	cin >> Lösenord;
}



void visaMenu() {
	int choice;
	int harKonto = 0;

	cout << "Välkommen" << endl;
	cout << "Ange ditt användarnamn och lösenord för att logga in." << endl;
	cout << "AnvändarNamn: " << endl;
	cin >> användarNamn;
	cout << "Lösenord: " << endl;
	cin >> Lösenord;

	if (användarNamn != "omar" || Lösenord != "elnadi") {
		cout << "Fel användarnamn eller lösenord." << endl;
		cout << "Vill du skapa ett konto? Ange 1 för att skapa ett konto eller 0 för att avsluta: ";
		cin >> harKonto;

		if (harKonto) {
			skapaKonto();
			login();
		}
		else {
			return;
		}
	}

	cout << "Inloggning lyckades." << endl;


	do {
		cout << "Välkommen" << endl;
		cout << "**********Meny *********" << endl;
		cout << "1. Dra ut pengar" << endl;
		cout << "2. Sätta in pengar" << endl;
		cout << "3. Saldo" << endl;
		cout << "4. Avsluta" << endl;
		cout << "Välj ett alternativ: ";
		cin >> choice;

		switch (choice) {
		case 1:
			// Dra ut pengar
			cout << "Var snäll och ange summan att dra ut: " << endl;
			int uttag;
			cin >> uttag;
			if (uttag > saldo) {
				cout << "Det finns inte tillräckligt med pengar på ditt konto." << endl;
			}
			else {
				saldo -= uttag;
				cout << "Du har dragit ut " << uttag << " kr. Ditt saldo är nu " << saldo << " kr." << endl;
			}
			break;
		case 2:
			// Sätta in pengar
			cout << "Var snäll och ange summan att sätta in: " << endl;
			int insättning;
			cin >> insättning;
			saldo += insättning;
			cout << "Tack för din insättning. Ditt saldo är nu " << saldo << " kr." << endl;
			break;
		case 3:
			// Saldo
			cout << "Ditt saldo är: " << saldo << " kr." << endl;
			break;
		case 4:
			// Avsluta
			std::cout << "Tack för ditt besök. Ha en bra dag!" << endl;
			return;
		default:
			cout << "Ogiltigt val. Vänligen välj ett giltigt alternativ." << endl;
			break;
		}

		cout << "Vill du göra en annan transaktion? Välj 1 för att fortsätta eller 2 för att avsluta: " << endl;
		cin >> annanUtdrag;
		cout << std::endl;

	} while (annanUtdrag == 1);
}

int main() {
	visaMenu();
	system(pause>0) // funkade med "system(pause>0)" för mig på visual studio 2019
}

