# XO-game-project-
tik tak toe  in c++

#include <iostream>
#include <ctime>

using namespace std;

void draw(char* espaces);
void player(char joueur, char* espaces);
void ordinateur(char autom, char* espaces);
bool gangant  (char*espaces , char joueur , char autom  ) ; 
bool nul (char* espaces );

int main() {
    bool traitement = true ;
    char autom = 'O';
    char joueur = 'x';
    char espaces[9] = { ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ' };
    draw (  espaces ) ;
   while (traitement ){
    player( joueur,  espaces);
    draw( espaces);
    if (gangant( espaces ,  joueur , autom  )){
        traitement = false ;
        break ;
    }
    else if (nul( espaces )){
        traitement = false ; 
        break ;
    }
    ordinateur ( autom ,  espaces );
    draw ( espaces ) ; 
    if (gangant( espaces ,  joueur , autom  )){
        traitement = false ;
        break ;
    }
    else if (nul( espaces )){
        traitement = false ; 
        break ;
    }
   }
   cout<<"mar7ba bik fi darek "<<'\n' ; 



    return 0;
}

void draw(char* espaces) {
    cout << '\n';
    cout << "     |     |     " << '\n';
    cout << "  " << espaces[0] << "  |  " << espaces[1] << "  |  " << espaces[2] << "  " << '\n';
    cout << "_____|_____|_____" << '\n';
    cout << "     |     |     " << '\n';
    cout << "  " << espaces[3] << "  |  " << espaces[4] << "  |  " << espaces[5] << "  " << '\n';
    cout << "_____|_____|_____" << '\n';
    cout << "     |     |     " << '\n';
    cout << "  " << espaces[6] << "  |  " << espaces[7] << "  |  " << espaces[8] << "  " << '\n';
    cout << "     |     |     " << '\n';
    cout << '\n';
}

void player(char joueur, char* espaces) {
   
    int pick;
    do {
        cout << "donner la case que vous voulez attaquer " << '\n';
        cin >> pick;
        if (pick < 1 || pick > 9) {
            cout << "Entrez un nombre entre 1 et 9" << endl;
        } else if (espaces[pick-1] != ' ') {
            cout << "Cette case est deja occupee" << endl;
        }
    } while (pick < 1 || pick > 9 || espaces[pick-1] != ' ');
    espaces[pick-1] = joueur;
    draw (  espaces );
}
    


void ordinateur(char autom, char* espaces) {
    int random;
    srand(time(0));
    while (true) {
        random = rand() % 9;
        if (espaces[random] == ' ') {
            espaces[random] = autom;
            break;
        }
    }
    draw ( espaces ) ; 
   
}
bool gangant (char *espaces, char joueur, char autom ){

    if((espaces[0] != ' ') && (espaces[0] == espaces[1]) && (espaces[1] == espaces[2])){
        espaces[0] == joueur ? cout << "YOU WIN!\n" : cout << "YOU LOSE!\n";
    }
    else if ((espaces[3] != ' ') && (espaces[4] == espaces[3]) && (espaces[5] == espaces[3])){
        espaces[3] == joueur ? cout << "YOU WIN!\n" : cout << "YOU LOSE!\n";}
    else if ((espaces[6] != ' ') && (espaces[6] == espaces[7]) && (espaces[7] == espaces[8])){
        espaces[6] == joueur ? cout << "YOU WIN!\n" : cout << "YOU LOSE!\n";}
    else if ((espaces[0] != ' ') && (espaces[0] == espaces[4]) && (espaces[4] == espaces[8])){
        espaces[0] == joueur ? cout << "YOU WIN!\n" : cout << "YOU LOSE!\n";}
    else if ((espaces[2] != ' ') && (espaces[2] == espaces[4]) && (espaces[4] == espaces[6])){
        espaces[2] == joueur ? cout << "YOU WIN!\n" : cout << "YOU LOSE!\n";}
    else if ((espaces[0] != ' ') && (espaces[0] == espaces[3]) && (espaces[3] == espaces[6])){
        espaces[0] == joueur ? cout << "YOU WIN!\n" : cout << "YOU LOSE!\n";}
    else if ((espaces[1] != ' ') && (espaces[1] == espaces[4]) && (espaces[4] == espaces[7])){
        espaces[1] == joueur ? cout << "YOU WIN!\n" : cout << "YOU LOSE!\n";}
    else if ((espaces[2] != ' ') && (espaces[2] == espaces[5]) && (espaces[5] == espaces[8])){
        espaces[2] == joueur ? cout << "YOU WIN!\n" : cout << "YOU LOSE!\n";}
    else {
        return false ;
        }
    return true ; 
    }
    bool nul (char*espaces ){
        int i ; 
        for (int i=0 ; i<9 ; i++){
            if (espaces[i]=' '){
                return false ;
            }
        }

        cout <<"c'est nul"<<'\n' ; 
        return true ;
            }
        
