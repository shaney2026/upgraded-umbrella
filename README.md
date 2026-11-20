
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double subtotal = 0;
        String receipt = "";
        String choice = "no";

        System.out.println("=== POINT OF SALE SYSTEM ===");

        do {
            System.out.print("\nProduct: ");
            String product = sc.nextLine();

            System.out.print("Price: PHP ");
            double price = sc.nextDouble();

            System.out.print("Quantity: ");
            int qty = sc.nextInt();
            sc.nextLine();

            if (price <= 0 || qty <= 0) {
                System.out.println("Invalid price or quantity!");
                continue;
            }

            double total = price * qty;
            subtotal += total;

            receipt += product + " x" + qty
                    + " = PHP " + String.format("%.2f", total) + "\n";

            System.out.print("Add another product? (yes/no): ");
            choice = sc.nextLine();

        } while (choice.equalsIgnoreCase("yes"));

        double discount = subtotal >= 1000 ? subtotal * 0.10 : 0;
        double total = subtotal - discount;

        System.out.printf("\nTotal: PHP %.2f%n", total);

        double cash;
        do {
            System.out.print("Cash: PHP ");
            cash = sc.nextDouble();

            if (cash < total) {
                System.out.println("Insufficient cash!");
            }

        } while (cash < total);

        System.out.println("\n======= RECEIPT =======");
        System.out.print(receipt);
        System.out.printf("Subtotal: PHP %.2f%n", subtotal);
        System.out.printf("Discount: PHP %.2f%n", discount);
        System.out.printf("Total: PHP %.2f%n", total);
        System.out.printf("Cash: PHP %.2f%n", cash);
        System.out.printf("Change: PHP %.2f%n", cash - total);
        System.out.println("=======================");
        System.out.println("Thank you for shopping!");

        sc.close();
    }
}
