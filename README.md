# Adit-Sharma
This program is a console-based grocery bill calculator that lets a cashier enter items, applies slab-based discounts and tax, and prints a formatted receipt.​

# Constants and imports
import datetime
Lets the program print the current date and time on the receipt.​

TAX_RATE = 0.05
Sets a fixed tax rate of 5% to be applied on the discounted subtotal.​

# get_item_details()
Prints a section header and asks for an item name; if the user types done, it returns None to signal end of input.​

In a loop, asks for quantity, forcing it to be a positive integer; invalid or non-positive inputs trigger an error message and re-prompt.​

In another loop, asks for price, forcing it to be a positive float; again, invalid or non-positive inputs cause a re-prompt.​

Returns a dictionary like {'name': ..., 'quantity': ..., 'price': ..., 'subtotal': quantity * price} for each valid item; if input ends unexpectedly (EOF), it returns None.​

# calculate_bill(items)
Computes initial_subtotal as the sum of all item subtotals in the items list.​

Chooses a discount rate based on slabs:

≥ 1000 → 12%, ≥ 500 → 10%, ≥ 200 → 5%, otherwise 0%.​

Calculates:

discount_amount = initial_subtotal * discount_rate

discounted_subtotal = initial_subtotal - discount_amount

tax_amount = discounted_subtotal * TAX_RATE

grand_total = discounted_subtotal + tax_amount.​

Returns a summary dictionary with all these values for later printing.​

# print_receipt(items, summary)
If items is empty, prints a short “RECEIPT - No Items Added” block and returns.​

Otherwise, prints a header with the store name “VIT STORE”, “Bill of Sale” title, and the current date-time, plus formatting lines.​

Prints column headings (ITEM, QTY, PRICE, TOTAL) and then loops through each item to print its details nicely aligned using formatted strings.​

Extracts values from summary and prints:

Subtotal

Discount line (only if a discount was applied, showing the percentage and amount)

Taxable subtotal

Tax line with the 5% rate

GRAND TOTAL, plus a thank-you message and closing lines.​

# main() and program flow
main() starts by creating an empty list purchased_items and printing a welcome message with instructions (“Type 'done' when finished”).​

In a while True loop, it calls get_item_details() repeatedly:

If None is returned, the loop breaks (user finished entering items).

Otherwise, it appends the item to purchased_items and prints a line summarizing what was added and the running subtotal.​

After the loop:

If there are items, it calls calculate_bill(purchased_items) and then print_receipt(purchased_items, bill_summary).

If no items were added, it prints a simple “No items were added to the bill. Goodbye!” message.​

The if __name__ == "__main__": main() block makes sure main() runs when the file is executed as a script.
