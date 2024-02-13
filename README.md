public class BankingApplication {

	public static void main(String[] args) {
		Bank bank = new Bank();
		bank.showMenu();
	}

}


import java.util.Scanner;

public class Bank {
	int balance;
	int previous;
	

	public void showMenu() {
		Scanner scan1 = new Scanner(System.in);
		System.out.print("Enter your name : ");
		String name = scan1.next();
		System.out.print("Enter your Id : ");
		int id = scan1.nextInt();
		System.out.println("===================================================");
		System.out.println("Welcome " + name);
		System.out.println("Your Customer ID is " + id);
		System.out.println("Your courrent balance is " + balance);
		System.out.println("===================================================");
		System.out.println("Enter B to check balance");
		System.out.println("Enter D to deposit cash");
		System.out.println("Enter W to withdraw cash");
		System.out.println("Enter P to get your previous transaction information");
		System.out.println("Enter E to exit");
		char option = '\0';
		do {
			Scanner scan = new Scanner(System.in);
			System.out.print("Enter a option to perform : ");
			option = scan.next().charAt(0);
			switch(option) {
				case 'B': case 'b':
					System.out.println("===================================================");
					System.out.println("Your current balance is : " + balance);
					System.out.println("===================================================");
					System.out.println();
					break;
				case 'D': case 'd':
					System.out.println("===================================================");
					System.out.print("Enter the amount you want to depost : ");
					System.out.println();
					System.out.println("===================================================");
					int amount = scan.nextInt();
					deposit(amount);
					System.out.println();
					break;
				case 'W': case 'w':
					System.out.println("===================================================");
					System.out.print("Enter the amount you want to withdraw : ");
					System.out.println();
					System.out.println("===================================================");
					int amount1 = scan.nextInt();
					withdraw(amount1);
					System.out.println();
					break;
				case 'P': case 'p':
					System.out.println("===================================================");
					getTransaction();
					System.out.println("===================================================");
					System.out.println();
					break;
				case 'E': case 'e':
					System.out.println("===================================================");
					break;
				default :
					System.out.println("===================================================");
					System.out.println("Enter a valid option");
					
			}
		}while(option  != 'E' && option != 'e');
		
	}
	public void deposit(int amount) {
		if(amount != 0) {
			balance = balance + amount;
			previous = amount;
		}		
	}
	public void withdraw(int amount) {
		if(balance>amount) {
			if(amount != 0) {
				balance = balance - amount;
				previous = -(amount);
			}
		}
		else {
			System.out.println();
			System.out.println("Sorry, Insufficent fund");
			System.out.println("You have " + balance +"rs in your account");
		}
	}
	public void getTransaction() {
		if(previous > 0) {
			System.out.println("Deposit : " + previous);
		}
		else if(previous < 0){
			System.out.println("Withdrawn : " + Math.abs(balance));
		}
		else {
			System.out.println("No Transactions occured");
		}
	}
}
