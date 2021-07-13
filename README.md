# ATM-SYSTEM-PROJECT
import java.io.IOException;
import java.text.DecimalFormat;
import java.text.DecimalFormatSymbols;
import java.util.*;
import java.io.IOException;
import java.text.DecimalFormat;
import java.util.*;

public class Main extends OptionMenu{

  public static void main(String[] args) throws IOException {
    OptionMenu optionMenu= new OptionMenu();

    optionMenu.getLogin();
  }

};

class Account {
  private int customerNumber;
  private int pinNumber;
  private double checkingBalance = 0;
  private double savingBalance = 0;

  Scanner input = new Scanner(System.in);
  DecimalFormat moneyFormat = new DecimalFormat("'$'###,##0.00");

  public int setCustomerNumber(int customerNumber){
    this.customerNumber = customerNumber;
    return customerNumber;
  }

  public int getCustomerNumber(){
    return customerNumber;
  }

  public int setPinNumber(int pinNumber){
    this.pinNumber = pinNumber;
    return pinNumber;
  }

  public int getPinNumber(){
    return pinNumber;
  }

  public double getCheckingBalance(){
    return checkingBalance;
  }

  public double getSavingBalance(){
    return savingBalance;
  }

  public double calcCheckingWithdraw(double amount){
    checkingBalance = (checkingBalance - amount);
    return checkingBalance;
  }

  public double calcSavingWithdraw(double amount){
    savingBalance = (savingBalance - amount);
    return savingBalance;
  }

  public double calcCheckingDeposit(double amount){
    checkingBalance = (checkingBalance + amount);
    return checkingBalance;
  }

  public double calcSavingDeposit(double amount){
    savingBalance = (savingBalance + amount);
    return savingBalance;
  }

  public void getCheckingWithdrawInput(){
    System.out.println("Checking Account Balance: " + moneyFormat.format(checkingBalance));
    System.out.print("Amount you want to withdraw from Checking Account: ");
    double amount =input.nextDouble();

    if((checkingBalance-amount)>=0){
      calcCheckingWithdraw(amount);
      System.out.println("New Checking Account Balance: " + moneyFormat.format(checkingBalance));
      }else{
      System.out.println("Balance Cannot be Negative." + "\n");
      }
    }

    public void getsavingWithdrawInput(){
      System.out.println("Saving Account Balance: " + moneyFormat.format(savingBalance));
      System.out.print("Amount you want to withdraw from Saving Account: ");
      double amount =input.nextDouble();

      if((savingBalance-amount)>=0){
        calcSavingWithdraw(amount);
        System.out.println("New Saving Account Balance: " + moneyFormat.format(savingBalance));
        }else{
        System.out.println("Balance Cannot be Negative." + "\n");
        }
      }

      public void getCheckingDepositInput(){
        System.out.println("Checking Account Balance: " + moneyFormat.format(checkingBalance));
        System.out.print("Amount you want to Deposit from Checking Account: ");
        double amount =input.nextDouble();

        if((checkingBalance+amount)>=0){
          calcCheckingDeposit(amount);
          System.out.println("New Checking Account Balance: " + moneyFormat.format(checkingBalance));
          }else{
          System.out.println("Balance Cannot be Negative." + "\n");
          }
        }

        public void getSavingDepositInput(){
          System.out.println("Saving Account Balance: " + moneyFormat.format(savingBalance));
          System.out.print("Amount you want to Deposit from Saving Account: ");
          double amount =input.nextDouble();

          if((savingBalance+amount)>=0){
            calcSavingDeposit(amount);
            System.out.println("New Saving Account Balance: " + moneyFormat.format(savingBalance));
            }else{
            System.out.println("Balance Cannot be Negative." + "\n");
            }
          }


}

class OptionMenu extends Account {
  Scanner menuInput= new Scanner(System.in);
  DecimalFormat moneyFormat=new DecimalFormat("'$'###,##0.00");

  HashMap<Integer,Integer> data= new HashMap<Integer,Integer>();

  public void getLogin() throws IOException {
    int x=1;
    do{
      try {
         data.put(952141, 191904);
         data.put(989947, 71976);

         System.out.println("Welcome to the ATM System!");
         System.out.println("Enter your Card Number");
         setCustomerNumber(menuInput.nextInt());

         System.out.print("Enter your PIN Number: ");
         setPinNumber(menuInput.nextInt());
         }
         catch (Exception e) {
           System.out.println("\n"+ "Invalid Character(s). Only Numbers."+"\n");
           x=2;
         }
         int cn=getCustomerNumber();
         int pn=getPinNumber();
         if(data.containsKey(cn) && data.get(cn)==pn){
             getAccountType();
         }else
         System.out.println("\n" + "Wrong Card Number or Pin Number" + "\n");
      System.out.println("\n" + " If you Don't have Account please Create Account!" + "\n");
		System.out.println("Enter your Card Number ");
		int cst_no=menuInput.nextInt();
		System.out.println("Enter PIN to be register");
		int pin=menuInput.nextInt();
		data.put(cst_no,pin);
		System.out.println("Your New Account has been Successfuly Registered! ");
		System.out.println("Redirecting to login.............");
		getLogin();
    }while(x==1);
  }

  public void getAccountType(){
    System.out.println("Select the Account you Want to Access: ");
    System.out.println(" Type 1 - Checking Account");
    System.out.println(" Type 2 - Saving Account");
    System.out.println(" Type 3 - Exit");
    System.out.println(" Type 4 - Convert your Currency");

    int selection= menuInput.nextInt();

    switch (selection) {
      case 1:
      getChecking();
      break;

      case 2:
      getSaving();
      break;

      case 3:
      System.out.println("Thank You for using our ATM SYSTEM, Have a Great Day!. \n");
      break;

        case 4:
      currencyConvert();
      System.exit(0);
     
      
      default:
      System.out.println("\n" + "Invalid Choice." + "\n");
      getAccountType();
    }
  }

public void currencyConvert()
{
	double amount, dollar, pound, code, euro, yen, ringgit, rupee;
 
		DecimalFormat f = new DecimalFormat("##.##");
 
		Scanner sc = new Scanner(System.in);
 
		System.out.println("Hi Sir, Welcome to the Currency Converter!, Please Proceed");
 
		System.out.println("Which Currency you want to Convert ? ");
		
		System.out.println("1:Rupee \t2:Dollar \t3:Pound \n4:Euro  \t5:Yen   \t6:Ringgit ");
		code = sc.nextInt();
		
		System.out.println("How much Amount you want to convert ?");
		amount = sc.nextFloat();
 
		// For amounts Conversion
		if (code == 1) {
 
			dollar = amount / 74.86;
			System.out.println("Your " + amount + " Rupees is : " + f.format(dollar) + " Dollar");
 
			pound = amount / 97;
			System.out.println("Your " + amount + " Rupees is : " + f.format(pound) + " Pound");
 
			euro = amount / 88;
			System.out.println("Your " + amount + " Rupees is : " + f.format(euro) + " Euro");
 
			yen = amount / 0.71;
			System.out.println("Your " + amount + " Rupees is : " + f.format(yen) + " Yen");
 
			ringgit = amount / 17.6;
			System.out.println("Your " + amount + " Rupees is : " + f.format(ringgit) + " Ringgit");
		} else if (code == 2) {
			// For Dollar Conversion
 
			rupee = amount * 74.86;
			System.out.println("Your " + amount + " Dollar is : " + f.format(rupee) + " Rupees");
 
			pound = amount * 0.77;
			System.out.println("Your " + amount + " Dollar is : " + f.format(pound) + " Pound");
 
			euro = amount * 0.85;
			System.out.println("Your " + amount + " Dollar is : " + f.format(euro) + " Euro");
 
			yen = amount * 104.99;
			System.out.println("Your " + amount + " Dollar is : " + f.format(yen) + " Yen");
 
			ringgit = amount * 4.25;
			System.out.println("Your " + amount + " Dollar is : " + f.format(ringgit) + " Ringgit");
		} else if (code == 3) {
			// For Pound Conversion
 
			rupee = amount * 97;
			System.out.println("Your " + amount + " Pound is : " + f.format(rupee) + " Rupees");
 
			dollar = amount * 1.3;
			System.out.println("Your " + amount + " Pound is : " + f.format(dollar) + " Dollar");
 
			euro = amount * 1.10;
			System.out.println("Your " + amount + " Pound is : " + f.format(euro) + " Euro");
 
			yen = amount * 136.21;
			System.out.println("Your " + amount + " Pound is : " + f.format(yen) + " Yen");
 
			ringgit = amount * 5.5;
			System.out.println("Your " + amount + " Pound is : " + f.format(ringgit) + " Ringgit");
		} else if (code == 4) {
			// For Euro Conversion
 
			rupee = amount * 88;
			System.out.println("Your " + amount + " Euro is : " + f.format(rupee) + " Rupees");
 
			dollar = amount * 1.18;
			System.out.println("Your " + amount + " Euro is : " + f.format(dollar) + " Dollar");
 
			pound = amount * 0.91;
			System.out.println("Your " + amount + " Euro is : " + f.format(pound) + " Pound");
 
			yen = amount * 123.43;
			System.out.println("Your " + amount + " Euro is : " + f.format(yen) + " Yen");
 
			ringgit = amount * 5;
			System.out.println("Your " + amount + " Euro is : " + f.format(ringgit) + " Ringgit");
		} else if (code == 5) {
 
			// For Yen Conversion
 
			rupee = amount * 0.71;
			System.out.println("Your " + amount + " Yen is : " + f.format(rupee) + " Rupees");
 
			dollar = amount * 0.0095;
			System.out.println("Your " + amount + " Yen is : " + f.format(dollar) + " Dollar");
 
			pound = amount * 0.007;
			System.out.println("Your " + amount + " Yen is : " + f.format(pound) + " Pound");
 
			euro = amount * 0.0081;
			System.out.println("Your " + amount + " Yen is : " + f.format(euro) + " Euro");
 
			ringgit = amount * 0.040;
			System.out.println("Your " + amount + " Yen is : " + f.format(ringgit) + " Ringgit");
		} else if (code == 6) {
			// For Ringgit Conversion
 
			rupee = amount * 17.66;
			System.out.println("Your " + amount + " Ringgit is : " + f.format(rupee) + " Rupees");
 
			dollar = amount * 0.24;
			System.out.println("Your " + amount + " Ringgit is : " + f.format(dollar) + " Dollar");
 
			pound = amount * 0.18;
			System.out.println("Your " + amount + " Ringgit is : " + f.format(pound) + " Pound");
 
			euro = amount * 0.20;
			System.out.println("Your " + amount + " Ringgit is : " + f.format(euro) + " Euro");
 
			yen = amount * 24.69;
			System.out.println("Your " + amount + " Ringgit is : " + f.format(yen) + " Yen");
		} else {
			System.out.println("Invalid input");
		}
		
		System.out.println("Thank you for choosing our Programs");
	
}
public void viewcurrencyConvert(double amount)
{
	double  dollar, pound, code, euro, yen, ringgit, rupee;
 
		DecimalFormat f = new DecimalFormat("##.##");
 
     		rupee = amount * 74.86;
			System.out.println("Your " + amount + " Dollar is : " + f.format(rupee) + " Rupees");
 
			pound = amount * 0.77;
			System.out.println("Your " + amount + " Dollar is : " + f.format(pound) + " Pound");
 
			euro = amount * 0.85;
			System.out.println("Your " + amount + " Dollar is : " + f.format(euro) + " Euro");
 
			yen = amount * 104.99;
			System.out.println("Your " + amount + " Dollar is : " + f.format(yen) + " Yen");
 
			ringgit = amount * 4.25;
			System.out.println("Your " + amount + " Dollar is : " + f.format(ringgit) + " Ringgit");
		
		
		System.out.println("Thank You for using our ATM SYSTEM, Have a Great Day!.");
	
}

  public void getChecking(){
    System.out.println("Checking Account: ");
    System.out.println(" Type 1 - View Balance");
    System.out.println(" Type 2 - Withdraw Funds");
    System.out.println(" Type 3 - Deposit Funds");
    System.out.println(" Type 4 - Exit");
    System.out.print("Choice: ");

    int selection = menuInput.nextInt();

    switch (selection) {
      case 1:
      System.out.println("Checking Account Balance: " + moneyFormat.format(getCheckingBalance()));
      
      viewcurrencyConvert(getCheckingBalance());
      getAccountType();
      break;

      case 2:
      getCheckingWithdrawInput();
      getAccountType();
      break;

      case 3:
      getCheckingDepositInput();
      getAccountType();
      break;

      case 4:
      System.out.println("Thank You for using our ATM SYSTEM, Have a Great Day!.");
      break;

      default:
      System.out.println("\n" + "Invalid Choice." + "\n");
      getChecking();
    }
  }


  public void getSaving(){
    System.out.println("Saving Account: ");
    System.out.println(" Type 1 - View Balance");
    System.out.println(" Type 2 - Withdraw Funds");
    System.out.println(" Type 3 - Deposit Funds");
    System.out.println(" Type 4 - Exit");
    System.out.print("Choice: ");

    int selection = menuInput.nextInt();

    switch (selection) {
      case 1:
      System.out.println("Saving Account Balance: " + moneyFormat.format(getSavingBalance()));
    
      viewcurrencyConvert(getSavingBalance());
      getAccountType();
      break;

      case 2:
      getsavingWithdrawInput();
      getAccountType();
      break;

      case 3:
      getSavingDepositInput();
      getAccountType();
      break;

      case 4:
      System.out.println("Thank You for using our ATM SYSTEM, Have a Great Day!.");
      break;

      default:
      System.out.println("\n" + "Invalid Choice." + "\n");
      getChecking();
    }
  }

}
