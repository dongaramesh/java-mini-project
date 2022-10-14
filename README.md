//package aarogya_hospital;
import java.util.*;
import java.util.ArrayList;
import java.util.HashSet;
import java.util.Scanner;


// the main class
 class AarogyaHospital{

	
        // class for storing the patient information
	class AarogyaMember{
          // declare all the details for the patient including name, age, gender, Aadhar Card number, contact number, city, address, date of admission, guardian name, guardian address, guardian contact number
    String name, gender, city, address, date, guardianName, guardianAddress,status;
    int id, age;
    long aadharNumber, contactNumber, gaurdianNumber;
    int count;
    boolean recovered;
	
	    // make constructor for the class and assign it a unique Id
	    public AarogyaMember(){
        recovered = false;
	    }
    	    // for taking patient information
	    public void input(){
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter the patient id: ");
        id = sc.nextInt();
        System.out.println("Enter the patient name: ");
        name = sc.next();
        System.out.println("Enter the patient age: ");
        age = sc.nextInt();
        System.out.println("Enter the patient gender: ");
        gender = sc.next();
        System.out.println("Enter the patient Aadhar Number: ");
        aadharNumber = sc.nextLong();
        System.out.println("Enter the patient contact Number: ");
        contactNumber = sc.nextLong();
        System.out.println("Enter the patient city: ");
        city = sc.next();
        System.out.println("Enter the patient Address: ");
        address = sc.next();
        System.out.println("Enter the patient admit date: ");
        date = sc.next();
        System.out.println("Enter status ");
         status = sc.next();
        System.out.println("Enter the guardian Name: ");
        guardianName = sc.next();
        System.out.println("Enter the guardian Address: ");
        guardianAddress = sc.next();
        System.out.println("Enter the guardian contact number: ");
        gaurdianNumber = sc.nextLong();
        System.out.println();
	    }  

	}

	// pick the choice of task to be performed
	static long choices(){
    System.out.println("*");
		System.out.println("Press 1 for adding new member");
		System.out.println("Press 2 to view list of all available members");
		System.out.println("Press 3 to search member by ID");
		System.out.println("Press 4 to search member from a particular city");
		System.out.println("Press 5 to search member from a particular age group");
		System.out.println("Press 6 to mark recovery of a member");
		System.out.println("Press 7 to delete data of a member");
		System.out.println("Press 0 to exit");
		System.out.println();
    
            // create scanner class to take input
      Scanner ip = new Scanner(System.in);
      System.out.println("Choose any option: ");
	    long option=ip.nextLong();
      System.out.println();
	    return option;
	}
  static void displaydetails(AarogyaHospital.AarogyaMember p)
  {
    System.out.println("Patient id: "+p.id);
    System.out.println("Patient Name: "+p.name);
    System.out.println("Patient Gender: "+p.gender);
    System.out.println("Patient Age: "+p.age);
    System.out.println("Patient City: "+p.city);
    System.out.println("Patient Contact Number: "+p.contactNumber);
    System.out.println("Patient Aadhar Number: "+p.aadharNumber);
    System.out.println("Patient address: "+p.address);
    System.out.println("Admit date: "+p.date);
    System.out.println("status: "+p.status);
    System.out.println("Guardian name: "+p.guardianName);
    System.out.println("Guradian address: "+p.guardianAddress);
    System.out.println("Guradian contact number: "+p.gaurdianNumber);
    System.out.println();
    
  }

	public static void main(String args[]){
		
		// initialise array list to store list of patients information
    ArrayList<AarogyaMember> list=new ArrayList<AarogyaMember>();
    AarogyaHospital h = new AarogyaHospital();
    Scanner sc=new Scanner(System.in);
    Iterator<AarogyaMember> i = list.iterator();
    
		
		//for adding aarogya member information
		while(true){

			//take choice
			long option=choices();
			
			//invalid choice
			
			// take the input and add in the arrayList
			if(option==1){
        AarogyaHospital.AarogyaMember newpatient = h.new AarogyaMember();
        newpatient.input();
        list.add(newpatient);
        	        }
        
			//iterate and print all the patients information
	       		 else if(option==2){
               int count=0;
               i = list.iterator();
               while(i.hasNext())
                 {
                   AarogyaHospital.AarogyaMember p = i.next();
                   displaydetails(p);
                   count++;
                   System.out.println("*");
                 }
               if(count==0)
               {
                 System.out.println("no data found");
               }

	       		 }
			
			// print details of the patient with a particular id (take id as input)
	                else if(option==3){
                    int count=0;
                    System.out.println("enter search id");
                    int sid=sc.nextInt();
                    i=list.iterator();
                    while(i.hasNext())
                 {
                   AarogyaHospital.AarogyaMember p = i.next();
                   if(p.id==sid)
                   {
                   displaydetails(p);
                     count++;
                   System.out.println("*");
                 }
	                }
                    if(count==0)
               {
                 System.out.println("no data found with "+sid);
               }
                  }
			
			// to print all the patients from a particular city (take city as input)
	                else if(option==4){
                    int count=0;
                     System.out.println("enter city");
                    String scity=sc.next();
                    i=list.iterator();
                    while(i.hasNext())
                 {
                   AarogyaHospital.AarogyaMember p = i.next();
                   if(p.city.equals(scity))
                   {
                   displaydetails(p);
                     count++;
                   System.out.println("*");   
                 }
	                }
                    if(count==0)
               {
                 System.out.println("no data found with "+scity);
               }
	               }
			// to print details of all the patients in a particular age group (take age limits as input)
	               else if(option==5){
                   int count=0;
                   System.out.println("enter start age");
                    int sage=sc.nextInt();
                   System.out.println("enter end age");
                    int eage=sc.nextInt();
                    i=list.iterator();
                    while(i.hasNext())
                 {
                   AarogyaHospital.AarogyaMember p = i.next();
                   if(p.age>=sage&&p.age<=eage)
                   {
                   displaydetails(p);
                     count++;
                   System.out.println("*");
                     
                 }
	                }
                   if(count==0)
               {
                 System.out.println("no data found in this age group");
               }
	              }
	              // take member id as input to maintain recovered information of patient
	               else if(option==6){
	            System.out.println("Enter the patient id: ");
                    int id = sc.nextInt();
                   int count = 0;
                    i = list.iterator();
                    while(i.hasNext())
                      {
                        AarogyaHospital.AarogyaMember p = i.next();
                      
                          if(p.id==id)
                          {
                            System.out.println("Patient "+p.id+" is recovered");
                            count++;
                          }
                       
                      }
                   if(count==0)
                   {
                     System.out.println("Patient information is wrong");
                   }
                         
                      

	              }
	              //take member id as input to delete patient information
	              else if(option==7){
                  
                  System.out.println("Enter the patient id: ");
                    int id = sc.nextInt();
                    i = list.iterator();
                    while(i.hasNext())
                      {
                        AarogyaHospital.AarogyaMember p = i.next();
                        
                        if(p.id == id)
                        {
                          i.remove();
                          
                          System.out.println("Successfully deleted");
                        }
                          
                        
                        
                      }
                    System.out.println();


	              }
			
	              else if(option==0){
	             break;
	             }
                 else
                {
                  System.out.println("try again with correct option");
                  System.out.println();
                }
		}
	}
}
