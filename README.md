#include <stdio.h>
#include <string.h>

int main()
{
    int choice, option;

    char animal[5][10] = {"dogs","cats","monkey","fish","wolf"};
    char food[5][10] = {"chocolate","noodles","chicken","apple","banana"};
    char sports[5][15] = {"cricket","football","basketball","kabaddi","chess"};

    printf("\t\t========== WORD HUNT ==========\n\n");
    printf("WELCOME TO THE GAME!!\n\n");
    printf("Rules of the game:\n");
    printf("1. Choose a category\n");
    printf("2. Enter a number (1-5) to select a secret word\n remember you only have 5 wrong attempts to guess it!!\n");
    printf("3. Start guessing letters!\n\n");

    printf("==== MENU ====\n");
    printf("1. Animals\n");
    printf("2. Food\n");
    printf("3. Sports\n");
    printf("4. Exit\n");

    printf("Enter your choice: ");
    scanf("%d", &choice);

    if(choice == 4)
    {
        printf("Exiting game...\n");
        return 0;
    }

    printf("Enter a number from 1 to 5: ");
    scanf("%d", &option);

    if(option < 1 || option > 5)
    {
        printf("Invalid number!\n");
        return 0;
    }

    char *secret;

    if(choice == 1)
        secret = animal[option - 1];
    else if(choice == 2)
        secret = food[option - 1];
    else if(choice == 3)
        secret = sports[option - 1];
    else
    {
        printf("Invalid category!\n");
        return 0;
    }

    int len = strlen(secret);
    char guess[20];

    for(int i = 0; i < len; i++)
        guess[i] = '_';

    guess[len] = '\0';

    int attempts = 5;

    while(attempts > 0)
    {
        char letter;
        int found = 0;

        printf("\nWord: %s\n", guess);
        printf("Attempts left: %d\n", attempts);
        printf("Enter a letter: ");
        scanf(" %c", &letter);

        for(int i = 0; i < len; i++)
        {
            if(secret[i] == letter)
            {
                guess[i] = letter;
                found = 1;
            }
        }

        if(found == 0)
        {
            printf("Wrong guess!\n");
            if (choice==1){
                if(option==1)
                    printf("hint:Man's best friend\n");
                if(option==2)
                    printf("hint:Loves milk\n");
                if(option==3)
                    printf("hint:Jumps on trees\n");
                if(option==4)
                printf("hint:Lives in water\n");
                if(option==5)
                    printf("hint:Wild animal that howls\n");

            }
            if (choice==2){
                if(option==1)
                    printf("hint:Sweet and cold\n");
                if(option==2)
                    printf("hint:Long, twisty, slurpy\n");
                if(option==3)
                    printf("hint:Gym bros say this word 24/7\n");
                if(option==4)
                printf("hint:Keeps doctors unemployed\n");
                if(option==5)
                    printf("hint:Monkey’s favorite snack\n");

            }
             if (choice==3){
                if(option==1)
                    printf("hint:Where people scream 'sixer!!' loudly\n");
                if(option==2)
                    printf("hint: players chasing one ball dramatically\n");
                if(option==3)
                    printf("hint:Tall people’s favourite flex\n");
                if(option==4)
                printf("hint:Desi wrestling but make it intense \n");
                if(option==5)
                    printf("hint:Silent war between two brains\n");

            }

            attempts--;
        }

        if(strcmp(secret, guess) == 0)
        {
            printf("\nCongratulations! You guessed the word: %s\n", secret);
            break;
        }
    }

    if(attempts == 0)
        printf("\nGame Over! The word was: %s\n", secret);

    return 0;
}
