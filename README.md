import java.util.ArrayList;
import java.util.Scanner;

class Donor {
    String name;
    int age;
    String bloodGroup;
    String location;   // NEW FIELD

    Donor(String name, int age, String bloodGroup, String location) {
        this.name = name;
        this.age = age;
        this.bloodGroup = bloodGroup;
        this.location = location;
    }

    void display() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Blood Group: " + bloodGroup);
        System.out.println("Location: " + location); // DISPLAY LOCATION
        System.out.println("---------------------");
    }
}

public class BloodBank {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<Donor> donors = new ArrayList<>();

        int choice;

        do {
            System.out.println("\n--- Blood Bank Management ---");
            System.out.println("1. Add Donor");
            System.out.println("2. View Donors");
            System.out.println("3. Search by Blood Group");
            System.out.println("4. Exit");
            System.out.print("Enter choice: ");

            choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {
                case 1:
                    System.out.print("Enter Name: ");
                    String name = sc.nextLine();

                    System.out.print("Enter Age: ");
                    int age = sc.nextInt();
                    sc.nextLine();

                    System.out.print("Enter Blood Group: ");
                    String bg = sc.nextLine();

                    System.out.print("Enter Location: ");   // NEW INPUT
                    String loc = sc.nextLine();

                    donors.add(new Donor(name, age, bg, loc));
                    System.out.println("Donor added successfully!");
                    break;

                case 2:
                    if (donors.isEmpty()) {
                        System.out.println("No donors available.");
                    } else {
                        for (Donor d : donors) {
                            d.display();
                        }
                    }
                    break;

                case 3:
                    System.out.print("Enter Blood Group to search: ");
                    String searchBG = sc.nextLine();

                    boolean found = false;
                    for (Donor d : donors) {
                        if (d.bloodGroup.equalsIgnoreCase(searchBG)) {
                            d.display();
                            found = true;
                        }
                    }

                    if (!found) {
                        System.out.println("No donors found with this blood group.");
                    }
                    break;

                case 4:
                    System.out.println("Thank you!");
                    break;

                default:
                    System.out.println("Invalid choice!");
            }

        } while (choice != 4);

        sc.close();
    }
}
