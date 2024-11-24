import java.util.ArrayList;
import java.util.Scanner;

public class Main{

    // A simple class to represent a Task
    static class Task {
        String taskName;
        boolean isCompleted;

        // Constructor
        Task(String taskName) {
            this.taskName = taskName;
            this.isCompleted = false;
        }

        // Mark the task as completed
        void markAsCompleted() {
            this.isCompleted = true;
        }

        // Display task status
        @Override
        public String toString() {
            return taskName + (isCompleted ? " (Completed)" : " (Pending)");
        }
    }

    // The main list that holds all the tasks
    static ArrayList<Task> todoList = new ArrayList<>();
    static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        // Menu-driven loop
        while (true) {
            System.out.println("\nTo-Do List Application");
            System.out.println("1. Add a Task");
            System.out.println("2. View All Tasks");
            System.out.println("3. Remove a Task");
            System.out.println("4. Mark Task as Completed");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            scanner.nextLine();  // Consume newline left-over

            switch (choice) {
                case 1:
                    addTask();
                    break;
                case 2:
                    viewAllTasks();
                    break;
                case 3:
                    removeTask();
                    break;
                case 4:
                    markTaskAsCompleted();
                    break;
                case 5:
                    System.out.println("Exiting the To-Do List application...");
                    return;  // Exit the program
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }

    // Method to add a task to the list
    private static void addTask() {
        System.out.print("Enter the task description: ");
        String taskDescription = scanner.nextLine();
        todoList.add(new Task(taskDescription));
        System.out.println("Task added successfully!");
    }

    // Method to view all tasks
    private static void viewAllTasks() {
        if (todoList.isEmpty()) {
            System.out.println("No tasks in your to-do list.");
        } else {
            System.out.println("\nYour To-Do List:");
            for (int i = 0; i < todoList.size(); i++) {
                System.out.println((i + 1) + ". " + todoList.get(i));
            }
        }
    }

    // Method to remove a task from the list
    private static void removeTask() {
        if (todoList.isEmpty()) {
            System.out.println("No tasks to remove.");
            return;
        }

        System.out.print("Enter the task number to remove: ");
        int taskNumber = scanner.nextInt();
        scanner.nextLine();  // Consume newline left-over

        if (taskNumber > 0 && taskNumber <= todoList.size()) {
            todoList.remove(taskNumber - 1);  // Remove the task
            System.out.println("Task removed successfully!");
        } else {
            System.out.println("Invalid task number. Please try again.");
        }
    }

    // Method to mark a task as completed
    private static void markTaskAsCompleted() {
        if (todoList.isEmpty()) {
            System.out.println("No tasks to mark as completed.");
            return;
        }

        System.out.print("Enter the task number to mark as completed: ");
        int taskNumber = scanner.nextInt();
        scanner.nextLine();  // Consume newline left-over

        if (taskNumber > 0 && taskNumber <= todoList.size()) {
            Task task = todoList.get(taskNumber - 1);
            task.markAsCompleted();  // Mark the task as completed
            System.out.println("Task marked as completed!");
        } else {
            System.out.println("Invalid task number. Please try again.");
        }
    }
}
