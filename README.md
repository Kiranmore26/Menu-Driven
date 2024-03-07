# Menu-Driven

Q1
THursday-lab6

package Activities;

import java.util.Scanner;
class OrderingSystem
{
	 String[] menuItems;
     int[] itemCounts;
     Scanner sc = new Scanner(System.in);
     
     
//     Method to insert an Item
	public void insertItem() 
    { 
        System.out.print("Enter the new menu item: ");
        String newItem = sc.nextLine();
        // Check if the item is already in the menu
        for (int i = 0; i < menuItems.length; i++) 
        {
            if (menuItems[i] != null && menuItems[i].equalsIgnoreCase(newItem)) 
            {
                System.out.println("Item already exists. Updating count...");
                itemCounts[i]++;
                return;
            }
        }
        // Find the first available slot in the array
        for (int i = 0; i < menuItems.length; i++) 
        {
            if (menuItems[i] == null) {
                menuItems[i] = newItem;
                itemCounts[i] = 1;
                System.out.println("Item inserted successfully.");
                return;
            }
        }

        System.out.println("Menu is full. Unable to insert the item.");
    }
	
//		Method to Update an item
	 public void updateItemCount() 
	 {
	        System.out.print("Enter the menu item to update count: ");
	        String itemToUpdate = sc.nextLine();

	        // Check if the item is in the menu
	        for (int i = 0; i < menuItems.length; i++) 
	        {
	            if (menuItems[i] != null && menuItems[i].equalsIgnoreCase(itemToUpdate)) 
	            {
	                System.out.print("Enter the new count for " + menuItems[i] + ": ");
	                itemCounts[i] = sc.nextInt();
	                System.out.println("Count updated successfully.");
	                return;
	            }
	        }

	        System.out.println("Item not found in the menu. Unable to update count.");
	    }

	 
//	 	Method to Delete an item
	  public void deleteItem() 
	  {
	        System.out.print("Enter the menu item to delete: ");
	        String itemToDelete = sc.nextLine();

	        // Check if the item is in the menu
	        for (int i = 0; i < menuItems.length; i++) 
	        {
	            if (menuItems[i] != null && menuItems[i].equalsIgnoreCase(itemToDelete)) 
	            {
	                menuItems[i] = null;
	                itemCounts[i] = 0;
	                System.out.println("Item deleted successfully.");
	                return;
	            }
	        }

	        System.out.println("Item not found in the menu. Unable to delete.");
	    }

//	 	Method to Display Items
	  public void displayMenu() 
	  {
	        System.out.println("\nMenu:");

	        for (int i = 0; i < menuItems.length; i++) 
	        {
	            if (menuItems[i] != null) 
	            {
	                System.out.println(menuItems[i] + " - Count: " + itemCounts[i]);
	            }
	        }
	    }  
}


public class MenuManager 
{
    
    public static void main(String[] args) 
    {
        Scanner sc = new Scanner(System.in);
        System.out.println("Welcome to the Taj Hotel!");
        MenuManager m = new MenuManager();
        OrderingSystem o = new OrderingSystem();
        // Initialize menu items array and counts array
        o.menuItems = new String[100]; // Assuming a maximum of 100 menu items
        o.itemCounts = new int[100];

        int choice;
        do //to repeat the process
        {
            System.out.println("\nMenu:");
            System.out.println("1. Insert new item");
            System.out.println("2. Update item count");
            System.out.println("3. Delete item");
            System.out.println("4. Display menu");
            System.out.println("0. Exit");
            System.out.print("Enter your choice: ");
            choice = sc.nextInt();

            switch (choice) 
            {
                case 1:
                    o.insertItem();
                    break;
                case 2:
                    o.updateItemCount();
                    break;
                case 3:
                    o.deleteItem();
                    break;
                case 4:
                    o.displayMenu();
                    break;
                case 0:
                    System.out.println("Exiting Menu Manager. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid choice. Please enter a valid option.");
            }
        } 
        while (choice != 0);
        System.out.println("********* Thank You ***************");
        System.out.println("********* visit Again **************");
    }
    
    
}
