# Cafe-Inventory-System

START

DISPLAY welcome message
ASK user: "Do you want to proceed? (yes/no)"
IF user says "no" THEN
    DISPLAY goodbye message
    EXIT
ELSE IF user says "yes" THEN
    INITIALIZE inventory with predefined items and expiry dates

    DISPLAY inventory items

    LOOP
        DISPLAY options: Add, Check & Remove, Show, Exit
        GET user's choice

        IF choice is "Add" THEN
            ASK user for item name, quantity, expiry date
            VALIDATE inputs
            ADD item to inventory

        ELSE IF choice is "Check & Remove" THEN
            SET today's date
            FOR each item in inventory DO
                FOR each batch in item DO
                    IF expired THEN
                        REMOVE batch
                        DISPLAY alert
                    ELSE IF almost expired (within 3 days) THEN
                        DISPLAY notice
                        MARK item as almost expired

            IF no almost expired items found THEN
                DISPLAY "No items expiring soon."

            DISPLAY "Expired items removed"

            ASK user: "Do you want to sell an item? (yes/no)"
            IF user says "yes" THEN
                DISPLAY items (prioritize almost expired first)
                ASK user to choose an item
                ASK quantity to sell

                SORT item batches:
                    - Almost expired first
                    - Then by earliest expiry

                FOR each batch in sorted batches DO
                    SELL from batch using FIFO until quantity is fulfilled
                    UPDATE inventory
                DISPLAY how many units were sold

        ELSE IF choice is "Show Inventory" THEN
            DISPLAY all items with total quantity and expiry dates
            IDENTIFY low stock items (<= threshold)

            IF there are low stock items THEN
                ASK user: "Do you want to replenish? (yes/no)"
                IF yes THEN
                    FOR each low stock item DO
                        ASK for quantity and expiry
                        ADD to inventory

        ELSE IF choice is "Exit" THEN
            DISPLAY exit message
            BREAK loop

        ELSE
            DISPLAY "Invalid input"

END
