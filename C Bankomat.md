// C language 

#include <stdio.h>
#include <string.h>

float saldo = 0;
int annanUtdrag;
char användarNamn[20];
char Lösenord[20];

void skapaKonto() {
    printf("Skapa ett konto\n");
    printf("Ange önskat användarnamn: ");
    scanf("%s", användarNamn);
    printf("Ange önskat lösenord: ");
    scanf("%s", Lösenord);
    printf("Kontot har skapats.\n");
}

void login() {
    printf("Ange ditt användarnamn: ");
    scanf("%s", användarNamn);
    printf("Ange ditt lösenord: ");
    scanf("%s", Lösenord);
}

void visaMenu() {
    int choice;
    int harKonto = 0;

    printf("Välkommen\n");
    printf("Ange ditt användarnamn och lösenord för att logga in.\n");
    printf("Användarnamn: ");
    scanf("%s", användarNamn);
    printf("Lösenord: ");
    scanf("%s", Lösenord);

    if (strcmp(användarNamn, "omar") != 0 || strcmp(Lösenord, "elnadi") != 0) {
        printf("Fel användarnamn eller lösenord.\n");
        printf("Vill du skapa ett konto? Ange 1 för att skapa ett konto eller 0 för att avsluta: ");
        scanf("%d", &harKonto);

        if (harKonto) {
            skapaKonto();
            login();
        } else {
            return;
        }
    }

    printf("Inloggning lyckades.\n");

    do {
        printf("Välkommen\n");
        printf("**********Meny *********\n");
        printf("1. Dra ut pengar\n");
        printf("2. Sätta in pengar\n");
        printf("3. Saldo\n");
        printf("4. Avsluta\n");
        printf("Välj ett alternativ: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                // Dra ut pengar
                printf("Var snäll och ange summan att dra ut: ");
                int uttag;
                scanf("%d", &uttag);
                if (uttag > saldo) {
                    printf("Det finns inte tillräckligt med pengar på ditt konto.\n");
                } else {
                    saldo -= uttag;
                    printf("Du har dragit ut %d kr. Ditt saldo är nu %.2f kr.\n", uttag, saldo);
                }
                break;
            case 2:
                // Sätta in pengar
                printf("Var snäll och ange summan att sätta in: ");
                int insättning;
                scanf("%d", &insättning);
                saldo += insättning;
                printf("Tack för din insättning. Ditt saldo är nu %.2f kr.\n", saldo);
                break;
            case 3:
                // Saldo
                printf("Ditt saldo är: %.2f kr.\n", saldo);
                break;
            case 4:
                // Avsluta
                printf("Tack för ditt besök. Ha en bra dag!\n");
                return;
            default:
                printf("Ogiltigt val. Vänligen välj ett giltigt alternativ.\n");
                break;
        }

        printf("Vill du göra en annan transaktion? Välj 1 för att fortsätta eller 2 för att avsluta: ");
        scanf("%d", &annanUtdrag);
        printf("\n");

    } while (annanUtdrag == 1);
}

int main() {
    visaMenu();
    return 0;
}