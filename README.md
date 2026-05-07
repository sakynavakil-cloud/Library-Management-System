# Library-Management-System

import java.util.*;

public class Main {

    // ===== Book Class =====
    static class Book {
        int id;
        String title;
        String author;
        boolean isIssued;

        Book(int id, String title, String author) {
            this.id = id;
            this.title = title;
            this.author = author;
            this.isIssued = false;
        }
    }

    // ===== Library System =====
    static class Library {
        ArrayList<Book> books = new ArrayList<>();

        void addBook(Book b) {
            books.add(b);
            System.out.println("Book added successfully!");
        }

        void viewBooks() {
            if (books.isEmpty()) {
                System.out.println("No books available.");
                return;
            }

            for (Book b : books) {
                System.out.println(
                        "ID: " + b.id +
                        " | Title: " + b.title +
                        " | Author: " + b.author +
                        " | Status: " + (b.isIssued ? "Issued" : "Available")
                );
            }
        }

        void issueBook(int id) {
            for (Book b : books) {
                if (b.id == id) {
                    if (!b.isIssued) {
                        b.isIssued = true;
                        System.out.println("Book issued successfully!");
                    } else {
                        System.out.println("Book already issued.");
                    }
                    return;
                }
            }
            System.out.println("Book not found.");
        }

        void returnBook(int id) {
            for (Book b : books) {
                if (b.id == id) {
                    if (b.isIssued) {
                        b.isIssued = false;
                        System.out.println("Book returned successfully!");
                    } else {
                        System.out.println("Book was not issued.");
                    }
                    return;
                }
            }
            System.out.println("Book not found.");
        }

        void searchBook(int id) {
            for (Book b : books) {
                if (b.id == id) {
                    System.out.println("Found: " + b.title + " by " + b.author);
                    return;
                }
            }
            System.out.println("Book not found.");
        }
    }

    // ===== MAIN =====
    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        Library lib = new Library();

        while (true) {
            System.out.println("\n===== LIBRARY SYSTEM =====");
            System.out.println("1. Add Book");
            System.out.println("2. View Books");
            System.out.println("3. Issue Book");
            System.out.println("4. Return Book");
            System.out.println("5. Search Book");
            System.out.println("6. Exit");

            System.out.print("Enter choice: ");
            int choice = input.nextInt();

            switch (choice) {

                case 1:
                    System.out.print("Enter Book ID: ");
                    int id = input.nextInt();
                    input.nextLine();

                    System.out.print("Enter Title: ");
                    String title = input.nextLine();

                    System.out.print("Enter Author: ");
                    String author = input.nextLine();

                    lib.addBook(new Book(id, title, author));
                    break;

                case 2:
                    lib.viewBooks();
                    break;

                case 3:
                    System.out.print("Enter Book ID: ");
                    lib.issueBook(input.nextInt());
                    break;

                case 4:
                    System.out.print("Enter Book ID: ");
                    lib.returnBook(input.nextInt());
                    break;

                case 5:
                    System.out.print("Enter Book ID: ");
                    lib.searchBook(input.nextInt());
                    break;

                case 6:
                    System.out.println("Exiting system...");
                    return;

                default:
                    System.out.println("Invalid choice!");
            }
        }
    }
}
