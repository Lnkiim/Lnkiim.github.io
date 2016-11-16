---
layout: post
title: Project2
---
**Overall Approach**
	There are two overlapping architectures which are contained in this code. The first structure is built in a class is called ‘OnlineStoreManager’. This class is responsible for building and overseeing the production of my second class ‘Online Stores’. The OnlineStoreManager functions on a more macro level, hence it houses all of the functions where aggregate information is needed. (ie. The list of stores created.) 
	The OnlineStore class acts as the blueprint to handle the operations on a more micro level. This class houses methods which help the actual stores operate by tracking inventory, updating customer history, etc. While designing the structure of this class, it was made apparent that splitting up methods gave the code more versatility. For example, the ‘sell’ method, doesn’t actually execute any manipulation of the object or its attributes. Instead, it is merely calling other methods that should be triggered in the work flow. Going back to the example, when an item is sold, two adjustments should be made, the purchase history and the stores inventory. If for some reason, the store needed to adjust the inventory and not because a customer had purchased an item, the code has the flexibility to just call the subtract_inventory method and adjust the inventory as needed.


https://lnkiim.github.io/images/Slide1.jpg

![Alt text](/images/Slide1.jpg?raw=true)

**Documentation**

**Class: Online Store Manager**

**Function: Init**
Instantiates an online store manager. Online store manager will track aggregate information for all stores.
Parameters: 
1.	Name- of the online store manager
2.	Product List- a list containing all the types of items stores are permitted to sell. 
3.	‘Stores’ List – it is not a required parameter but is an attribute of any online store 
manager. Hence is it required to be listed under init.

**Function: create_online_store**
Creates online stores. First confirms that the inventory of the store is also in the product list.
If the product is not permitted for sale under the product list, a message will print. Then the object ‘store’ is created and stored in a list.
Parameters: 
1.	Name- of the store to be created
2.	Inventory- a dictionary data structure where the keys are the product and values are the quantity.
Returns: The object of type OnlineStore.
See Also: Class Online Store, def __init__

**Function: total_stores**
Parameters: none
Returns: the total number of stores that were created for any given osm.


**Function: list_stores**
Parameters:none
Returns: a list of strings with the ‘name’ attribute for each of the stores created


**Class: OnlineStore**

**Function: init**
Instantiates a new object of type OnlineStore. 
Creates a dictionary for customer history where the key is the customer ID, value is another nested dictionary, where key is the product, value is the quantity.

Parameters:
1.	Name- of the store to be created
2.	Inventory- a dictionary data structure where the keys are the product and values are the quantity.


**Function: sell**
Checks if the product is sold at the store. Checks if the desired quantity is equal to or less than what the store has in inventory.

Parameters:
1.	Customer ID- a unique pin for each customer which will help track purchase history
2.	Product – the item the customer wants to purchase
3.	Quantity- the desired number of the item the customer wants to purchase


**Function: get_inventory**

Parameters: none
Returns: dictionary of each store’s inventory where key is product, value is quantity

**Function: update_customer**
Checks if the customer is already in the system. If the customer already exists, the code will update their purchase history in the customer_history dictionary. If the customer does not exist, a new entry is made in the dictionary. 

Parameters:
1.	Customer ID- the customer’s unique identifier
2.	Product – the purchased item
3.	Quantity- the quantity of the purchased item

**Function: subtract_inventory**
This method gets called whenever the sell method is called. Reduces a store’s inventory whenever a customer purchases an item.

Parameters: 
1.	Product- purchased item
2.	Quantity – the number of items that were purchased

**Function: add_inventory**
Updated a store’s inventory whenever supplies are replenished.

Parameters: 
1.	Product – the product that is being replenished
2.	Quantity- the amount of the product

