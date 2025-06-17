import java.util.*;
public class knapsack {


    public static class KnapsackInteractive {


        static class Item {
            String name;
            int value;
            int weight;


            Item(String name, int value, int weight) {
                this.name = name;
                this.value = value;
                this.weight = weight;
            }
        }


        public static int knapsackItem(String userName, String healthCondition, List<Item> items, int weightLimit) {
            int n = items.size();
            int[] values = new int[n];
            int[] weights = new int[n];
            String[] names = new String[n];


            for (int i = 0; i < n; i++) {
                Item item = items.get(i);
                values[i] = item.value;
                weights[i] = item.weight;
                names[i] = item.name;
            }


            int[][] dp = new int[n + 1][weightLimit + 1];


            // Build table
            for (int i = 1; i <= n; i++) {
                for (int w = 0; w <= weightLimit; w++) {
                    if (weights[i - 1] <= w) {
                        dp[i][w] = Math.max(dp[i - 1][w],
                                values[i - 1] + dp[i - 1][w - weights[i - 1]]);
                    } else {
                        dp[i][w] = dp[i - 1][w];
                    }
                }
            }


            // Traceback
            List<Integer> selectedItem = new ArrayList<>();
            int res = dp[n][weightLimit];
            int w = weightLimit;


            for (int i = n; i > 0 && res > 0; i--) {
                if (res != dp[i - 1][w]) {
                    selectedItem.add(i - 1);
                    res -= values[i - 1];
                    w -= weights[i - 1];
                }
            }


            // Output
            System.out.println("\n--- Knapsack Result ---");
            System.out.println("User Profile:");
            System.out.println("  Name: " + userName);
            System.out.println("  Health Condition: " + healthCondition);
            System.out.println("  Weight Limit: " + weightLimit + "kg");


            System.out.println("\nMaximum value: " + dp[n][weightLimit]);
            System.out.println("Selected items:");
            int totalWeight = 0;
            int totalValue = 0;
            for (int i = selectedItem.size() - 1; i >= 0; i--) {
                int idx = selectedItem.get(i);
                System.out.println("  - " + names[idx] + " (value: " + values[idx] + ", weight: " + weights[idx] + ")");
                totalWeight += weights[idx];
                totalValue += values[idx];
            }


            System.out.println("Total weight used: " + totalWeight);
            System.out.println("Total value of selected items: " + totalValue);
            System.out.println("------------------------");


            return dp[n][weightLimit];
        }


        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);


            // Get user profile
            System.out.print("Enter your name: ");
            String userName = scanner.nextLine();


            System.out.print("Enter your health condition: ");
            String healthCondition = scanner.nextLine();


            System.out.print("Enter knapsack weight limit: ");
            int weightLimit = Integer.parseInt(scanner.nextLine());


            // Get item list
            System.out.print("Enter number of items: ");
            int itemCount = Integer.parseInt(scanner.nextLine());


            List<Item> items = new ArrayList<>();


            for (int i = 0; i < itemCount; i++) {
                System.out.println("\nItem " + (i + 1) + ":");
                System.out.print("  Name: ");
                String name = scanner.nextLine();


                System.out.print("  Value: ");
                int value = Integer.parseInt(scanner.nextLine());


                System.out.print("  Weight: ");
                int weight = Integer.parseInt(scanner.nextLine());


                items.add(new Item(name, value, weight));
            }


            // Run knapsack
            int maxValue = knapsackItem(userName, healthCondition, items, weightLimit);
            System.out.println("Returned max value: " + maxValue);
        }
    }


}
