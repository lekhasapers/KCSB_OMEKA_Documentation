# User Guide

This section provides guidance on accessing and using the Omeka S website.
_____

## Accessing the Website

To access the Omeka S website, visit [archives.kcsb.org](http://archives.kcsb.org).

#### Accessing the Administrative Back-End

The Omeka S administrative back-end is designed for managing collections, configuring settings, and overseeing the content displayed on your website. Here’s how to access and navigate the admin dashboard:

#### Visit the Admin Dashboard

Go to [archives.kcsb.org/admin](http://archives.kcsb.org/admin). You will be prompted to log in with your administrative credentials.

#### Login Credentials

You will be prompted to log in with your administrative credentials.  

Enter your username and password to access the admin dashboard. If you have forgotten your password, use the "Forgot Password" link to reset it.

#### Admin Dashboard Overview

Once logged in, you will be taken to the main dashboard, which provides a quick overview of the site’s activity and shortcuts to frequently used features.

#### Navigation Menu

The navigation menu on the left side of the dashboard allows you to access different sections:

- **Items:** Manage digital items in your collection, including adding, editing, and deleting items.
- **Item Sets:** Organize items into sets for better categorization and retrieval.
- **Media:** Upload and manage media files such as images, audio, and video associated with your items.
- **Pages:** Create and edit site pages to provide additional information and context for your collections.
- **Users:** Manage user accounts, assign roles, and set permissions.
- **Modules:** Add functionality to your Omeka S installation through various modules and plugins.
- **Settings:** Configure site-wide settings such as themes, languages, and API settings.

#### User Roles and Permissions

Omeka S supports multiple user roles, each with specific permissions:

- **Global Administrator:** Full access to all settings and content management features. This category will generally include the Engineer, Assistant Engineer, and the Archives Coordinator
- **Supervisor:** Manage content but with limited access to site-wide settings. This category will generally include the Advisors.
- **Editor:** Create and edit items and item sets but cannot change global settings. This category will generally include the experienced Archives volunteers
- **Reviewer:** Has content privileges but can only delete their own content. This category will generally include Archives volunteers.
- **Author**  Can create their own content. This category will generally include beginner Archives volunteers.
- **Researcher:** Access public and private items for research purposes. This category will include the general public. 
_____

### Creating and Managing Content 

As indicated before, The content in Omeka S is organized into **Items**, **Item Sets**, and **Media**. This section explains how to create and manage these content types efficiently. There are also parameters to manage **Users**, which this section will review in depth. 



#### Adding Items

1. **Navigate to the "Items" Section:** Access this section from the navigation menu on the left.
2. **Click "Add New Item":** This opens the item creation form.
3. **Enter Item Details:** Fill in fields such as title, description, and metadata.
4. **Attach Media Files:** Upload associated files like images, audio, and video.
5. **Save the Item:** Click "Save" to add the item to your collection.

#### Adding a New Item

1. Navigate to the "Items" section.
2. Click "Add New Item."
3. Enter item details, such as title, description, and associated media.
4. Save the item.


#### Creating Item Sets

Item Sets are groups of related items. They help organize collections.

1. **Go to "Item Sets":** Access this section via the navigation menu.
2. **Click "Add New Item Set":** This opens the item set creation form.
3. **Enter Set Details:** Provide a title, description, and any relevant metadata.
4. **Add Items to the Set:** Select items to include in the set.
5. **Save the Item Set:** Click "Save" to create the item set.

#### Managing Media

Media management is critical for associating files with items.

1. **Upload Media Files:** Access the "Media" section and click "Add New Media."
2. **Select Files to Upload:** Choose files from your computer or provide a URL for external media.
3. **Link Media to Items:** Assign media to items, specifying their role (e.g., image, audio).

#### Managing Users

1. Access the "Users" section.
2. Click "Add New User" to create a user account.
3. Assign a role and set permissions for the user.
4. Save the user account.
---
### CSV Upload

A critical part of the KCSB content management workflow is the CSV upload module. Procedures and best practices will also be reviewed in this section. 

#### KCSB Spreadsheet Template:

   - A template for preparing your CSV file is available to assist you. The KCSB Spreadsheet can be found [here](https://docs.google.com/spreadsheets/d/1MOXkm5SRqjtfC2neQVebXPRcSTAMlcT3/edit?usp=sharing&ouid=107537356243937470846&rtpof=true&sd=true).

#### Prepare Your CSV File:

   - **Format:** Ensure your CSV file is formatted correctly, with column headers matching Omeka S metadata fields (e.g., title, description, creator).
   - **Include Media URLs:** This has not been something I've been able to figure out, as there's a roadblock with linking URLs from Google Drive. However, if you find a way around it, please change my documentation so future archivists don't have to manually upload files. 

#### Navigate to CSV Import:

   - Access the "CSV Import" module from the admin dashboard.
   - Click "Import CSV" to begin the upload process.

#### Upload the CSV File:

   - **Select File:** Choose the CSV file from your computer.
   - **Configure Mapping:** Map CSV columns to Omeka S fields. Ensure each column is correctly matched to a metadata field.

#### Review and Confirm:

   - **Preview:** Check the preview to ensure data is correctly mapped.
   - **Import:** Click "Import" to add items to the collection. Monitor the import progress.

#### Verify Import:

   - **Check Items:** Ensure all items have been imported correctly.
   - **Review Media:** Verify that media files are associated with the correct items.

___________

## Modules and Extensions

Omeka S allows for the integration of modules that extend the platform’s functionality. Common modules include:

- **CSV Import:** Import items and metadata from CSV files.
- **Search:** Enhance search capabilities for users.
- **Mapping:** Display items on geographical maps.
- **Contact Us** Adds a contact form to front-end site

#### Contact Us Module

The Contact Us module adds a contact form to your site, allowing visitors to get in touch easily. For more information, refer to Omeka's [technical documentation.](https://omeka.org/s/modules/ContactUs/#:~:text=Contact%20Us%20is%20a%20module,directly%20in%20the%20interface%20too.) This step has already been completed, but in the case that it needs to be reinstalled, please refer to the below instructions. 

   - **Download and Install:** Obtain the module from the Omeka S repository and install it via the admin dashboard.
   - **Configure Settings:** Set up email addresses and form fields according to your needs.

#### Add Contact Us Page:

   - **Navigate to Pages:** Access the "Pages" section from the dashboard.
   - **Create New Page:** Click "Add New Page" and select the Contact Us layout.

   - **Customize Form:** Adjust form fields and settings as needed.


   - **Publish Page:** Click "Save" to publish the Contact Us page.
   - **Verify:** Test the form to ensure it functions correctly and that messages are received.
   
   As mentioned above, the KCSB module is already functioning, but feel free to remove and redownload using the above steps if anything ever goes wrong with module ops. 
____________

## Themes

Themes control the visual appearance of your Omeka S site. They can be customized to align with your branding and design preferences.

#### Changing Themes

1. **Navigate to "Themes":** Access this section from the admin dashboard.
2. **Select a Theme:** Choose from available themes or upload a custom theme.
3. **Activate Theme:** Click "Activate" to apply the theme to your site.

#### Backup and Security

- Regularly back up your database and files to prevent data loss.
- Implement security best practices, such as using strong passwords and updating software regularly.

#### Getting Help

For additional assistance, refer to the [Omeka S Documentation](https://omeka.org/s/docs/user-manual) or seek help from the [community forums](https://forum.omeka.org/).

A wonderful resource that was my personal Omeka bible was the Yale University Archives [Study Guide](https://docs.google.com/document/d/1SeHBTbae9Vy685ENqmGGENyf6H65pgDo0QsXo1rcWMQ/edit?usp=sharing). Use this resource frequently! 


