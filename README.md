import java.util.*;

class Employee {
    int empID;
    String name;
    double salary;

    Employee(int empID, String name, double salary) {
        this.empID = empID;
        this.name = name;
        this.salary = salary;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Simulating a database with a list
        List<Employee> employeeDB = new ArrayList<>();
        employeeDB.add(new Employee(101, "Chhavi", 55000));
        employeeDB.add(new Employee(102, "Amit", 60000));
        employeeDB.add(new Employee(103, "Priya", 58000));
        employeeDB.add(new Employee(104, "Rahul", 62000));

        System.out.println("=== Employee Management System ===");
        System.out.println("1. Display All Employees");
        System.out.println("2. Search Employee by ID");
        System.out.print("Enter your choice: ");
        int choice = sc.nextInt();

        switch (choice) {
            case 1:
                // Simulating JDBC SELECT * FROM Employee
                displayAllEmployees(employeeDB);
                break;

            case 2:
                System.out.print("Enter Employee ID to search: ");
                int searchID = sc.nextInt();
                searchEmployee(employeeDB, searchID);
                break;

            default:
                System.out.println("Invalid choice!");
        }

        sc.close();
    }

    // Simulating JDBC ResultSet iteration
    static void displayAllEmployees(List<Employee> employees) {
        System.out.println("\n--- Employee Records ---");
        System.out.printf("%-10s %-15s %-10s%n", "EmpID", "Name", "Salary");
        System.out.println("--------------------------------------");
        for (Employee e : employees) {
            System.out.printf("%-10d %-15s %-10.2f%n", e.empID, e.name, e.salary);
        }
    }

    // Simulating PreparedStatement WHERE EmpID=?
    static void searchEmployee(List<Employee> employees, int empID) {
        boolean found = false;
        for (Employee e : employees) {
            if (e.empID == empID) {
                System.out.println("\nEmployee Found:");
                System.out.printf("EmpID: %d%nName: %s%nSalary: %.2f%n", e.empID, e.name, e.salary);
                found = true;
                break;
            }
        }
        if (!found) {
            System.out.println("\n❌ No Employee found with ID: " + empID);
        }
    }
}
