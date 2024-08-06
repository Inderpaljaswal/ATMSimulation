# ATMSimulation
import java.util.Scanner;

public class ATMSimulation {
    // Account class to represent a user's account
    static class Account {
        private double balance;

        // Constructor
        public Account(double initialBalance) {
            if (initialBalance > 0.0) {
                this.balance = initialBalance;
            }
        }

        // Method to deposit money
        public void deposit(double amount) {
            if (amount > 0.0) {
                balance += amount;
                System.out.println("Deposit successful. Current balance: $" + balance);
            } else {
                System.out.println("Deposit amount must be positive.");
            }
        }

        // Method to withdraw money
        public void withdraw(double amount) {
            if (amount > 0.0) {
                if (amount <= balance) {
                    balance -= amount;
                    System.out.println("Withdrawal successful. Current balance: $" + balance);
                } else {
                    System.out.println("Insufficient balance.");
                }
            } else {
                System.out.println("Withdrawal amount must be positive.");
            }
        }

        // Method to check the current balance
        public void checkBalance() {
            System.out.println("Current balance: $" + balance);
        }
    }

    public static void main(String[] args) {
        // Create an account with an initial balance
        Account account = new Account(5000.0); // Initial balance is $5000

        Scanner scanner = new Scanner(System.in);
        boolean exit = false;

        // Menu-driven interface
        while (!exit) {
            System.out.println("\nATM Simulation");
            System.out.println("1. Check Balance");
            System.out.println("2. Deposit");
            System.out.println("3. Withdraw");
            System.out.println("4. Exit");
            System.out.print("Select an option: ");

            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    account.checkBalance();
                    break;
                case 2:
                    System.out.print("Enter amount to deposit: $");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    break;
                case 3:
                    System.out.print("Enter amount to withdraw: $");
                    double withdrawAmount = scanner.nextDouble();
                    account.withdraw(withdrawAmount);
                    break;
                case 4:
                    exit = true;
                    System.out.println("Thank you for using the ATM simulation.");
                    break;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }

        scanner.close();
    }
}
