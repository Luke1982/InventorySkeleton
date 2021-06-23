# WorkAssignment
A corebos module that lets you create Work Assignments (on location) for users. Apart from that obvious explanation this is also a module on which a new 'inventory' block will be developed. Meaning, a block on which you can list items you've sold, purchased or offered and details about those actions. Which is almost like a detailblock (in the master/detail paradigm), apart from that it contains more fields than only those that live on the InventoryDetails record(s). Mainly fields from that module, but some are fields from the Products or Services module.

Which fields should be present on each inventoryline (a representation of and InventoryDetails record) can be controlled through 'Master Detail Layout' businessmaps. Apart from that, the visibility of each field for a particular user is also respected. Meaning: if you, as an admin, create a businessmap that tells the module to show the costprice of a product on the inventoryline but Sarah opens that record (the WorkAssignment record) and doesn't have access to the costprice field of products, it won't be visible.

> Important to know is that this module is very much in beta phase. It is likely to be buggy, missing functionality and may receive updates that break it

## How the module registers the block
The block registration is done through a [developer block](https://corebos.com/documentation/doku.php?id=en:devel:add_special_block) that installs [through the manifest](https://github.com/Luke1982/WorkAssignment/blob/master/manifest.xml#L714-L733). That block file takes care of all the logic that is connected to the inventory functionality. The manifest also [installs an event handler](https://github.com/Luke1982/WorkAssignment/blob/master/manifest.xml#L706-L711) that hooks into the save of the main module record and saves all the relevant data.

## Fields that are always active
There is a list of fields that is considered to be essential to having a functional inventorymodule. No matter what you do, these fields will be visible on the inventorylines. That list is:
#### From InventoryDetails
- Quantity
- Listprice
- Ext gross
- Ext Net
- Discount amount
- The product/service capturefield
- The description
- The discount type
- The linetotal
#### From Products/Services
- The productname
- The usageunit (which is not shown as a field but as part of a fieldlabel, only when the Qty in stock and Qty in demand fields are active, so the field is not really always active)

## The group financial fields
Apart from the fields that live on the 'lines', the module of course has aggregation fields.


## Todo
- Create address fields