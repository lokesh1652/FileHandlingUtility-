# FileHandlingUtility-
#A Java program to demonstrate file handling operations like reading, writing, and modifying text files.
import java.io.*;
import java.util.Scanner;

public class FileHandlingUtility {

    // Method to write content to a file
    public static void writeToFile(String fileName, String content) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(fileName))) {
            writer.write(content);
            System.out.println("Content successfully written to the file: " + fileName);
        } catch (IOException e) {
            System.err.println("Error writing to file: " + e.getMessage());
        }
    }

    // Method to read content from a file
    public static void readFromFile(String fileName) {
        try (BufferedReader reader = new BufferedReader(new FileReader(fileName))) {
            String line;
            System.out.println("Content of the file " + fileName + ":");
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.err.println("Error reading from file: " + e.getMessage());
        }
    }

    // Method to append content to a file
    public static void appendToFile(String fileName, String content) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(fileName, true))) {
            writer.newLine(); // Add a new line before appending
            writer.write(content);
            System.out.println("Content successfully appended to the file: " + fileName);
        } catch (IOException e) {
            System.err.println("Error appending to file: " + e.getMessage());
        }
    }

    // Method to modify content of a file (overwrite)
    public static void modifyFile(String fileName, String newContent) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(fileName))) {
            writer.write(newContent);
            System.out.println("File " + fileName + " successfully modified.");
        } catch (IOException e) {
            System.err.println("Error modifying file: " + e.getMessage());
        }
    }

    // Main method to demonstrate file operations
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String fileName = "example.txt";

        // Write to file
        System.out.println("Enter content to write to the file:");
        String contentToWrite = scanner.nextLine();
        writeToFile(fileName, contentToWrite);

        // Read from file
        readFromFile(fileName);

        // Append to file
        System.out.println("Enter content to append to the file:");
        String contentToAppend = scanner.nextLine();
        appendToFile(fileName, contentToAppend);

        // Read from file after appending
        readFromFile(fileName);

        // Modify file
        System.out.println("Enter new content to overwrite the file:");
        String newContent = scanner.nextLine();
        modifyFile(fileName, newContent);

        // Read from file after modification
        readFromFile(fileName);

        scanner.close();
    }
}







