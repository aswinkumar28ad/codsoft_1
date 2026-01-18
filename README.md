# codsoft_1
task for upskilling 
import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {

    private static final int MAX_ATTEMPTS = 10;
    private static final int MIN = 1;
    private static final int MAX = 100;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int roundsPlayed = 0;
        int roundsWon = 0;
        boolean playAgain;

        System.out.println("===== Number Guessing Game =====");

        do {
            int targetNumber = random.nextInt(MAX - MIN + 1) + MIN;
            int attemptsLeft = MAX_ATTEMPTS;
            boolean guessedCorrectly = false;

            roundsPlayed++;

            System.out.println("\nI have selected a number between 1 and 100.");
            System.out.println("You have " + MAX_ATTEMPTS + " attempts.");

            while (attemptsLeft > 0) {
                System.out.print("\nEnter your guess: ");

                if (!scanner.hasNextInt()) {
                    System.out.println("Invalid input! Enter a number.");
                    scanner.next();
                    continue;
                }

                int guess = scanner.nextInt();
                attemptsLeft--;

                if (guess == targetNumber) {
                    System.out.println("Correct! You guessed the number.");
                    guessedCorrectly = true;
                    roundsWon++;
                    break;
                } else if (guess < targetNumber) {
                    System.out.println("Too low!");
                } else {
                    System.out.println("Too high!");
                }

                System.out.println("Attempts left: " + attemptsLeft);
            }

            if (!guessedCorrectly) {
                System.out.println("\n You've run out of attempts.");
                System.out.println("The correct number was: " + targetNumber);
            }

            System.out.print("\nDo you want to play another round? (yes/no): ");
            playAgain = scanner.next().equalsIgnoreCase("yes");

        } while (playAgain);

        System.out.println("\n===== Result =====");
        System.out.println("Rounds Played: " + roundsPlayed);
        System.out.println("Rounds Won: " + roundsWon);
        System.out.println("Score: " + (roundsWon * 10));

        System.out.println("Thanks for playing!");
        scanner.close();
    }
}
