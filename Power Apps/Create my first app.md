# Power Apps Exercise: Create Your First App Using Excel as a Data Source

In this exercise, you'll create your first app using an **Excel table** as the data source. You can use any Excel table, provided:

- The data is formatted as a **table**.
- The file is stored in a location accessible by **Microsoft Power Apps**, such as **OneDrive**.

---

## Exercise Overview

This exercise includes **two parts**:

1. **Generate a three-screen app** from an Excel table.
2. **Create a blank canvas app** that you'll enhance in future units.

Both apps use the **same data**.  
The three-screen app serves as a reference to understand how controls work together to display data.

---

## Get the Data

To complete this exercise:

1. **Download the Machine Order Data file**  
   - [Click here to download the files*(Insert actual link here)*.
   
2. **Extract the files** from the downloaded ZIP file.

3. Locate and open the Excel file named:  
   **`Machine-Order-Data.xlsx`**

---

## Upload to OneDrive

1. Open **OneDrive** in a browser.
2. Select **+ Add new > Files upload**.
3. In the **Open** dialog box:
   - Navigate to your **Downloads** folder.
   - Select **Machine-Order-Data.xlsx**.
4. Click **Open**.
5. Search for **"Machine-Order-Data"** in OneDrive to confirm the upload was successful.

---

###  Next Steps
- Use this uploaded Excel file as the data source for your Power Apps project.
- Proceed to generate the **three-screen app** and then create the **blank canvas app**.

---

##  Notes
- Ensure your Excel data is formatted as a **table** before uploading.
- Keep the file in a location accessible by Power Apps (OneDrive recommended).

---
# Build a Three-Screen App in Power Apps

In this exercise, you'll build a **three-screen app** using an Excel table as the data source. This app will allow you to browse, view details, and edit records.

---

## Steps to Build the App

### 1. Sign in to Power Apps
- Go to Power Apps Maker Portal and **sign in**.

### 2. Create the App
- From the **left navigation pane**, select **Apps**.
- Select **Start with an app template**.
- Under **Data-centered mobile apps**, choose **From Excel**.

### 3. Connect to Your Data
- Under **Select the table**:
  - Expand **OneDrive for Business**.
  - Find the file **Machine-Order_Data.xlsx**.
  - Select the **Machines** table.
  - Click **Create app**.

---

##  Fix Formula Error (If Occurs)
- In the **Machines** screen:
  - Select **Data**.
  - Reconnect to the **Machines** data source.

---

##  Customize the Browse Screen
1. Expand **BrowseGallery1** and select **Title1**.
2. In the **Property dropdown** (above Tree view), select **Text**.
3. In the formula bar:
   - Delete the existing value.
   - Type:  
     ```powerfx
     ThisItem.'Machine Name'
     ```
   - This displays the machine name for each item.

4. For **Subtitle1**:
   - Select **Text** property.
   - Type:  
     ```powerfx
     ThisItem.Price
     ```

5. For **Body1**:
   - Select **Text** property.
   - Type:  
     ```powerfx
     ThisItem.Color
     ```

---

##  Add an Image to the Gallery
- Move **Title1**, **Subtitle1**, and **Body1** slightly to the right:
  - Select all three (hold **Shift**).
  - In the **X property**, set value to `80`.

- Insert an **Image control**:
  - From the command bar, select **+ Insert**.
  - Search for **Image** and add it.
  - Resize and position it to the left of the text fields.

- Set the image property:
  ```powerfx
  ThisItem.Photo
  # Create a Canvas App in Power Apps

In this exercise, you'll create a **Canvas App** from scratch using data stored in an Excel file on OneDrive. This app will allow you to browse and edit coffee machine records.

---

##  Steps to Build the Canvas App

### 1. Start a Blank Canvas App
- Go to Power Apps Maker Portal.
- Select the **Create** tab.
- In the **Create** popup window:
  - Choose **Start with a blank canvas app**.
  - Select **Tablet size**.

> If the **Welcome to Power Apps Studio** pop-up appears, select **Skip**.

---

### 2. Save Your App
- Select **Save** from the top-right corner.
- In the **Save as** window:
  - Name your app:  
    **Contoso Coffee Machines**
  - Click **Save**.

---

### 3. Add a Gallery to Display Data
- From the **Insert** menu, select **Vertical gallery**.
- A control named **Gallery1** appears.
- Power Apps prompts you to **Select a data source**.

---

### 4. Connect to Excel Data
- Select **OneDrive for Business** (search for it if needed).
- If prompted, select **Add a connection** and authenticate.
- Choose the Excel file:  
  **Machine-Order-Data.xlsx**.
- Select the **Machines** table and click **Connect**.
- Confirm that the gallery's **Data source** is set to **Machines**.

---

### 5. Customize the Gallery
- If the gallery doesn't show picture, title, and price:
  - For **Title**:  
    ```powerfx
    ThisItem.'Machine Name'
    ```
  - For **Subtitle**:  
    ```powerfx
    ThisItem.Price
    ```
  - For **Image**:  
    ```powerfx
    ThisItem.Photo
    ```

Resize the gallery to fill the left side of the screen.

---

### 6. Add an Edit Form
- Deselect the gallery by clicking on a blank area.
- From **Insert**, select **Edit form**.
- Position the form on the **right half** of the screen.
- In the **Properties panel**, set **Data source** to **Machines**.
- Click **Edit fields** → **Add field**.
- Select these fields in order:
  - Photo
  - Machine ID
  - Machine Name
  - Price
  - Color
  - Description
  - Feature
  - Machine Type
  - Machine Type ID
  - Avg. Cups/Week
  - Avg. Espressos/Week
- Click **Add** and close the panel.

---

### 7. Bind Form to Selected Gallery Item
- With the form selected:
  - In the **Item** property, enter:  
    ```powerfx
    Gallery1.Selected
    ```

---

### 8. Fix Photo Field
- The photo field shows a URL instead of an image.
- Steps:
  1. Select the **Photo data card**.
  2. Delete the text input control inside it.
  3. Unlock the data card.
  4. Insert an **Image control**.
  5. Set its **Image** property to:  
     ```powerfx
     ThisItem.Photo
     ```
  6. Fix formula errors:
     - Replace references to deleted controls with your image control name (e.g., `Image2`).
     - For **Y + Height** formula:  
       ```powerfx
       Image2.Y + Image2.Height
       ```
     - For **Update** property:  
       ```powerfx
       Image2.Image
       ```

---

### 9. Preview the App
- Click the **Play** button (or press **F5**).
- Test:
  - Scroll through the gallery.
  - Select items and view details in the form.

---

### 10. Add a Save Button
- From **Insert**, select **Button**.
- Position it on **Screen1**.
- Configure its **OnSelect** property to submit the form:
  ```powerfx
  SubmitForm(Form1)

# Power Apps Guide: Build Apps Using Excel Data

This guide walks you through creating two types of apps in **Microsoft Power Apps** using an Excel table stored in **OneDrive for Business**:

1. **Three-Screen App** (auto-generated from Excel)
2. **Canvas App** (built from scratch)

Both apps use the same data source:  
**Machine-Order-Data.xlsx** (Machines table).

---

##  Prerequisites
- Microsoft Power Apps account
- Excel file formatted as a **table** and stored in **OneDrive for Business**
- File: `Machine-Order-Data.xlsx`

---

##  Part 1: Build a Three-Screen App

### 1. Upload Excel File
- Download and extract **Machine-Order-Data.xlsx**.
- Upload to **OneDrive for Business**:
  - Open OneDrive → **+ Add new > Files upload**.
  - Select the file and confirm upload.

---

### 2. Generate the App
- Go to Power Apps Maker Portal.
- From the left pane, select **Apps** → **Start with an app template**.
- Under **Data-centered mobile apps**, choose **From Excel**.
- Select:
  - **OneDrive for Business**
  - File: `Machine-Order-Data.xlsx`
  - Table: **Machines**
- Click **Create app**.

---

### 3. Fix Formula Error (If Occurs)
- In the **Machines** screen:
  - Select **Data** → reconnect to **Machines**.

---

### 4. Customize Browse Screen
- For **Title1**:
  ```powerfx
  ThisItem.'Machine Name'