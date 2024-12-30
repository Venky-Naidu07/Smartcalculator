import java.util.Scanner;

public class SmartCalculator {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        boolean continueCalculating = true;

        while (continueCalculating) {
            System.out.print("Enter first number: ");
            double num1 = getValidNumber(scanner);

            System.out.print("Enter second number: ");
            double num2 = getValidNumber(scanner);

            System.out.print("Enter operation (+, -, *, /): ");
            char operator = getValidOperator(scanner);

            double result = 0;
            switch (operator) {
                case '+':
                    result = num1 + num2;
                    break;
                case '-':
                    result = num1 - num2;
                    break;
                case '*':
                    result = num1 * num2;
                    break;
                case '/':
                    if (num2 == 0) {
                        System.out.println("Error: Cannot divide by zero.");
                        continue;
                    }
                    result = num1 / num2;
                    break;
            }

            System.out.println("Result: " + result);

            System.out.print("Do you want to perform another calculation? (yes/no): ");
            String answer = scanner.next();
            if (answer.equalsIgnoreCase("no")) {
                continueCalculating = false;
            }
        }

        System.out.println("Goodbye!");
        scanner.close();
    }

    public static double getValidNumber(Scanner scanner) {
        while (!scanner.hasNextDouble()) {
            System.out.println("Invalid input. Please enter a valid number.");
            scanner.next();
        }
        return scanner.nextDouble();
    }

    public static char getValidOperator(Scanner scanner) {
        char operator;
        while (true) {
            operator = scanner.next().charAt(0);
            if (operator == '+' || operator == '-' || operator == '*' || operator == '/') {
                break;
            }
            System.out.println("Invalid operator. Please enter one of +, -, *, or /.");
        }
        return operator;
    }
}
