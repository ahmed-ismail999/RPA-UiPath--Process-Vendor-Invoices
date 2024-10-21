# RPA - UiPath - Process for Handling WI3 Work Items

## Step 1: Open ACME System 1 Web Application
- **1.1** Open the ACME System 1 web application.

---

## Step 2: Log In to System 1
- **1.2** Log in to System 1 using the provided email and password.

---

## Step 3: Access the Dashboard
- **1.3** Navigate to the Dashboard, the central location where the user can select a specific menu item.

---

## Step 4: Access Work Items Listing
- **1.4** Access the "Work Items Listing" to view all available tasks.
  - **Output:** Work items of various types.

---

## Step 5: Process WI3 Work Items
For each activity of type WI3, perform the following steps:

- **1.5.A** Open the Details page for the selected activity.
- **1.5.B** Download the PDF invoice from the activity details.
- **1.5.C** Return to the Dashboard and access the “Search for Vendors” section from the Vendors menu.
- **1.5.D** Search for the vendor specified in the invoice based on the TaxID.
  - **Note:** If the Vendor TaxID is missing from the invoice, reject the activity (See **1.5.F-No_3** below).

---

## Step 6: Vendor Exists in ACME System 1?

### If Vendor Exists:
- **1.5.F-Yes_1** Go back to the Dashboard and access the “Add Invoice Details” section from the Invoices menu.
- **1.5.F-Yes_2** Fill in all fields of the form with the invoice details.
- **1.5.F-Yes_3** Return to the Work Item Details and open the "Update Work Item."
- **1.5.F-Yes_4** Set the status to **Completed** and add the comment:  
  `"Added Invoice [invoice-number] to system."`

### If Vendor Does Not Exist:
- **1.5.F-No_1** Go back to the Work Item Details and open the "Update Work Item."
- **1.5.F-No_2** Send an email to `vdd@acme-test.com` with the subject:  
  `"Please add Vendor"`, and attach the invoice.
- **1.5.F-No_3** Set the status to **Rejected** and add the comment:  
  `"Vendor with TaxID [invoice-number] not present in system. Email sent to VDD."`

---

## Step 7: Continue Processing the Next WI3 Activity
- **1.6** Once the current WI3 activity is completed or rejected, continue to the next WI3 activity and repeat the above steps.

---

