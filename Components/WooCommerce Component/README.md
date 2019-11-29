# Kalipso Studio V5 Add On's
Kalipso designer programming components.

The Kalipso components need to be added in the project settings. Just add a linked project and choose the component you have downloaded and all the component actions, objects and forms will be available.


***** WooCommerce Component *****

Files needed:

woocomponent.kzc

This component is part of the project WooCommerce REST API and allow you to populate the temp tables with information that comes from WooCommerce.

To use any of the implemented function you need the main website address, the customer key and the customer secret. These keys are configured in WooCommerce, check our wiki for more information.


Public implemented functions:

  getCoupons -> Gets all the coupons.
  
  getCustomers -> Gets all the customer information.
  
  getOrders -> Gets all the orders.
  
  getProducts -> Gets all the products.
  
  getOrderNotes -> Gets all the already imported order notes. This GA is dependent of you already imported the Orders to the temp table.
  


Private implemented functions:

  checkLicense -> Checks the component license. At the moment it as full access, no restrictions.
