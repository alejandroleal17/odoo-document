<br>

<center>

<span class='titulo'> <img src='flujo.png' width='7%' heigth='7%'> Odoo Workflow</span>

</center>

### 1. Receiving Sales Calls (User - Call Center)
1.1. **Check Stock**
    - Use the Odoo inventory module to access stock in real time.
    - Use the quick search function in the sales module to check product availability.
    - If the product is not available, use the sales module to search for alternative products and offer them to the customer.
   <center>
<div style="text-align:center">
     <img src='callcenter.png'>
</div>
</center>

1.2. **Create Order**
    - Use the Odoo sales module to create sales orders.
    - Customize sales order fields to capture information such as shipping address and payment method.
    - Provide training on the use of the sales module and how to handle different sales scenarios.

### 2. Review of Pending Orders (Warehouse Operator)
2.1. **Check Pending Orders**
    - Use the sales module to review pending orders.
    - Use priority tags in the sales module to establish an order hierarchy.
  

2.2. **Make Dispatch**
    - Use the inventory module to manage product packaging and labeling.
    - Use the Odoo calendar to schedule pickups and ensure punctual deliveries.
    2.2.1. **Make Shipment and Specify the Shipping Order**
    - Complete the shipping process using the Odoo delivery module and associate it with the corresponding order.
    - Generate shipping documents using custom templates in the sales module. 
    2.2.2. **Product Tracking**
    - Use the shipment tracking feature in the delivery module to track the products and update their status in the system.
  <center>
<div style="text-align:center">
     <img src='operator.png'>
</div>
</center>

2.3. **Check Stock**
    - Use the inventory module to schedule regular stock reviews.
    - Set up minimum stock alerts using Odoo notification features.

2.4. **Receive Products**
    - Use the purchasing module to receive incoming products and register them in inventory.
    - Use the quality control functions in the inventory module to inspect the products received.

2.5. **Perform Movements Within the Inventory (Reception and Shipping)**
    - Use the inventory module to perform inventory movements, such as transfers between locations.
    - Record inventory movements in the system to maintain an accurate record of stock.

2.6. **Import and Export Stock Product Data**
    - Use Odoo's import and export features to update and synchronize stock data with other systems.
    - Set up integrations with external tools to facilitate data import and export.


<button id="printButton">PRINT PDF  <img src='../../print-pdf.png' width='25px' heigth='15px' class='print-image'> </button>
