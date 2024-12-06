# Plane-Management---Java - Amishka Mindika

//importing

import java.util.*;

//main
public class w20527648_planemanagement {
    public static final int rows = 4;
    public static final int[] seats_per_row = {14,12,12,14};
    public static final char[] labels = {'A', 'B', 'C', 'D'};

    public static final boolean[][] seats = new boolean[rows][];




    //main code
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.println("\n");
        System.out.println("✈____                  WELCOME TO                ____✈ ");
        System.out.println("✈____               PLANE MANAGEMENT             ____✈ ");
        System.out.println("✈____              APPLICATION SYSTEM            ____✈ ");
        System.out.println("\n");
        initializing_seats();
        int option;


        do {
            menu();
            System.out.println("Please enter a number from 1 to 6 or 0 for Quit :");
            option = input.nextInt();

            switch (option) {

                case 1:
                    buy_seats();
                    break;
                case 2:
                    cancel_seat();
                    break;
                case 3:
                    first_available();
                    break;
                case 4:
                    System.out.println("✈✈✈✈✈✈✈✈✈✈✈✈✈✈✈ SEATING PLAN ✈✈✈✈✈✈✈✈✈✈✈✈✈✈✈✈✈");
                    System.out.println("\n");
                    seating_plan();
                    System.out.println("\n");
                    System.out.println("✈✈✈✈✈✈✈✈✈✈✈✈✈✈✈ SEATING PLAN ✈✈✈✈✈✈✈✈✈✈✈✈✈✈✈✈✈");
                    break;
                case 5:
                    System.out.println("✈✈✈✈✈✈      Ticket Information & Total Sales        ✈✈✈✈✈✈");
                    System.out.println("\n");
                    totalSales();
                    int price;
                    break;


                case 6:
                    search_tickets();
                    break;

                case 0:
                    System.out.println("Program Ended");
                    return;
                default:
                    System.out.println("Invalid Index");
            }
            System.out.println("\n");
        }while (option !=0);
    }
    //initializing_seats
    public static void initializing_seats(){
        for (int i=0 ; i<rows; i++){
            seats[i] = new boolean[seats_per_row[i]];
        }
    }
    //menu

    public static void menu(){
        System.out.println("^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^");
        System.out.println("✈                    MENU OPTIONS                      ✈");
        System.out.println("^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^");
        System.out.println("(1) Buy a seat :");
        System.out.println("(2) Cancel a seat : ");
        System.out.println("(3) Find first available seat :");
        System.out.println("(4) Show seating plan :");
        System.out.println("(5) Print tickets information & total sales :");
        System.out.println("(6) Search tickets :");
        System.out.println("(0) Quit ");
        System.out.println("\n");
        System.out.println("^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^");
        System.out.println("\n");
    }
    //seating plan

    public static void cwtest(String[] args) {

        seating_plan();
    }

    public static void seating_plan(){
        for (int i=0 ; i<rows ; i++){
            System.out.print(labels[i] + " ");
            for (int j=0 ; j<seats_per_row[i]; j++ ){
                if (!seats[i][j]){
                    System.out.print("O");
                }
                else{
                    System.out.print("X");
                }
            }
            System.out.println();
        }
    }
    //buy seats

    public static void buy_seats() {
        Scanner input = new Scanner(System.in);


        System.out.println("Enter A or B or C or D to get the Row :");
        String seat_row = input.next().toUpperCase();

        if (!seat_row.matches("[A-D]")) {
            System.out.println("Invalid row letter");
            return;
        }

        System.out.println("Enter the seat number");
        int seat_index = input.nextInt() - 1;

        if (seat_index < 0 || seat_index > seats_per_row[seat_row.charAt(0) - 'A']) {
            System.out.println("Invalid seat selection");
            return;
        }
        System.out.println("Your name : ");
        String name = input.next();
        System.out.println("Your surname :");
        String surname = input.next();
        System.out.println("Your email address : ");
        String email = input.next();
        System.out.println("\n");
        System.out.println("_____Person Information_____ ");
        System.out.println("\n");
        System.out.println("\n");
        System.out.println("Your row :" + seat_row);
        System.out.print("Your seat : " + (seat_index + 1));
        System.out.println("\n");
        System.out.println("Reserved");

        //calling form person

        person person_info = new person(name,surname,email);
        person.person_info();

        //price display

        System.out.println("\n");
        int price = 0;
        if (seat_row.matches("[A-D]")) {
            if (seat_index >= 1 && seat_index <= 5) {
                System.out.println("Price for the ticket is :£200");
            } else if (seat_index >= 6 && seat_index <= 9) {
                System.out.println("Price for the ticket is :£150");
            } else {
                System.out.println("Price for the ticket is :£180");
            }
        }

        System.out.println("\n");
        System.out.println("************** GO FORWARD ***************");
        System.out.println("\n");
        ticket save = new ticket();
        ticket.save();
        System.out.println('\n');

        //enter a number to continue

        System.out.println("Please enter number from 0-6 to Go Forward : ");
        int menu = input.nextInt();


    }
    // total sales
    public static void totalSales(){
        ticket totalSales = new ticket();
        ticket.totalSales();


    }
    //search tickets

    public static void search_tickets() {
        Scanner input = new Scanner(System.in);
        System.out.println("Enter name to search for tickets:");
        String searchName = input.next();

    }
    //cancel_seats

    public static void cancel_seat() {
        Scanner input = new Scanner(System.in);
        System.out.println("Please enter the row letter to cancel your seat :");
        String cancel_row = input.next().toUpperCase();
        System.out.println("\n");

        if(!cancel_row.matches("[A-D]")){
            System.out.println("Invalid row letter");
            return;
        }

        System.out.println("Please enter the seat number to cancel your seat :");
        int cancel_seat = input.nextInt();
        if(!seats[cancel_row.charAt(0)- 'A'][cancel_seat]){
            System.out.println("\n");
            System.out.println("*****     Seat cancelled     *****");
        }else{
            System.out.println("Seat" + " " + cancel_row +  cancel_seat + " " + "is invalid ");
        }
    }
    //first available


    private static void first_available(){
        boolean seat_available = false;
        for (int i=0; i<rows; i++) {
            for (int p = 0; p < seats_per_row[i]; p++) {
                if (!seats[i][p]) {
                    System.out.println("First available seat is" + " " + "row" + labels[i] + " " + "seat" + (p + 1));
                    seat_available = true;
                    break;
                }
            }

            if (seat_available) {
                break;
            }
        }
        if (!seat_available){
            System.out.println(" Available seats = 0(you can't book now)");
        }
    }

}
