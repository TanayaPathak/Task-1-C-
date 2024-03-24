# Task-1-C-

#include <iostream>
#include <cstdlib>
#include <ctime>

int guess_the_number() {
    int min_number = 1;
    int max_number = 100;
    
    srand(time(0));
    int secret_number = rand() % (max_number - min_number + 1) + min_number;
    
    int guess_count = 0;
    bool guessed = false;
    
    while (!guessed) {
        try {
            int guess;
            std::cout << "Guess a number between " << min_number << " and " << max_number << ": ";
            std::cin >> guess;
            
            if (guess < min_number || guess > max_number) {
                std::cout << "Invalid guess. Please enter a number between " << min_number << " and " << max_number << "." << std::endl;
                continue;
            }
            
            guess_count++;
            
            if (guess == secret_number) {
                guessed = true;
                std::cout << "You guessed it! The secret number was " << secret_number << "." << std::endl;
                std::cout << "It took you " << guess_count << " tries." << std::endl;
            } else {
                if (guess > secret_number) {
                    std::cout << "Too high, try again!" << std::endl;
                } else {
                    std::cout << "Too low, try again!" << std::endl;
                }
            }
        } catch (...) {
            std::cout << "Invalid input. Please enter a number." << std::endl;
        }
    }
    
    return 0;
}

int main() {
    guess_the_number();
    return 0;
}
