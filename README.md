# Bankdenomination
import java.util.Scanner;
public class BankDenomination {
     public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the amount (up to 5 digits): ");
        int amount = scanner.nextInt();
        if (amount < 1 || amount > 99999) {
            System.out.println("INVALID AMOUNT");
            return;
        }
        System.out.println("OUTPUT: " + convertToWords(amount));
        int[] denominations = {1000, 500, 100, 50, 20, 10, 5, 2, 1};
        int totalNotes = 0;
        System.out.println("DENOMINATION:");
        for (int denomination : denominations) {
            if (amount >= denomination) {
                int count = amount / denomination;
                amount %= denomination;
                totalNotes += count;
                System.out.println(denomination + " X " + count + " = " + (denomination * count));
            }
        }
        System.out.println("Total Notes: " + totalNotes);
        scanner.close();
    }
    public static String convertToWords(int number) {
        String[] units = {
            "ZERO", "ONE", "TWO", "THREE", "FOUR", "FIVE", 
            "SIX", "SEVEN", "EIGHT", "NINE"
        };
        StringBuilder words = new StringBuilder();
        String numberStr = String.valueOf(number);
        for (char digit : numberStr.toCharArray()) {
            words.append(units[Character.getNumericValue(digit)]).append(" ");
        }
        return words.toString().trim();
    }
}
