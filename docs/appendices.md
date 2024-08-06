# Glossary
_______

### API
An Application Programming Interface (API) is a set of tools and protocols for building software and applications. Omeka S provides an API to allow developers to interact with and extend the platform programmatically.

### Archive
A collection of historical records and documents that are preserved for research, historical, or cultural purposes. In Omeka, an archive can be digital, consisting of digitized or born-digital content.

### Collection
A group of related items within Omeka that are organized under a specific theme or category. Collections help users navigate and discover content more efficiently.

### Cron Job
A cron job is a scheduled task on Unix-like operating systems. It allows users to schedule scripts or commands to run automatically at specified times and intervals. Cron jobs are often used for automating repetitive tasks such as backups, updates, and system maintenance.

### CSV Import
A module or plugin that allows users to upload items in bulk using CSV (Comma-Separated Values) files. This feature simplifies the process of adding large numbers of items and metadata to Omeka.

### Digital Collection
A curated set of digital items, often organized around a specific theme, subject, or purpose. Digital collections in Omeka can include text, images, audio, and video content.

### Dublin Core
A set of metadata elements used to describe digital resources. Omeka uses Dublin Core as its default metadata schema, which includes fields like Title, Subject, Description, Creator, and Date.

### Exhibit
A curated presentation of items and collections in Omeka, designed to tell a story or provide insight into a particular topic. Exhibits can include text, images, and multimedia content to enhance the user's experience.

### Item
A single piece of content in Omeka, such as a photograph, document, video, or audio file. Each item can be described using metadata fields and assigned to collections or exhibits.

### JSON-LD
A lightweight data interchange format used to structure linked data in Omeka S. JSON-LD (JavaScript Object Notation for Linked Data) is used to represent complex metadata relationships.

### Linked Data
A method of connecting and sharing structured data on the web, allowing for improved interoperability and discoverability. Omeka S supports linked data principles, enabling richer metadata connections.

### Metadata
Information that describes a digital resource, such as title, creator, date, and format. Metadata helps users find and understand the context of digital items within Omeka.

### Module
A software component that adds specific functionality to Omeka S, such as data import/export, user authentication, or visual customization. Modules can be installed and configured through the Omeka admin dashboard.

### Omeka Classic
The original version of Omeka, designed for small to medium-sized digital collections. It offers basic features for item management, collection organization, and exhibit creation.

### Omeka S
A more scalable and flexible version of Omeka, designed for larger institutions with multiple sites and collections. Omeka S supports linked data, advanced metadata schemas, and custom themes.

### Plugin
An extension for Omeka Classic that adds additional features and capabilities, such as enhanced search, batch processing, or integration with other platforms.

### Resource Template
In Omeka S, a predefined set of metadata fields used to create items with consistent descriptions. Resource templates help standardize data entry across collections and sites.

### SSH Key
An SSH key is a pair of cryptographic keys used to authenticate and secure communication between computers over a network. The keys consist of a private key (kept secret) and a public key (shared with servers), providing a secure method of logging into a server remotely without a password.

#### How to Create an SSH Key:

1. **Open a Terminal**:
   Open a terminal on your local machine.

2. **Generate SSH Key**:
   Use the following command to generate a new SSH key pair:

   ```sh
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```

   Replace `"your_email@example.com"` with your email address.

3. **Save the Key**:
   When prompted, press `Enter` to save the key in the default location (`~/.ssh/id_rsa`) or specify a different location.

4. **Set a Passphrase**:
   Optionally, enter a passphrase for added security.

5. **Add SSH Key to SSH Agent**:
   Start the SSH agent and add your SSH private key:

   ```sh
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_rsa
   ```

6. **Copy Public Key to Clipboard**:
   Use the following command to copy your public key to the clipboard:

   ```sh
   pbcopy < ~/.ssh/id_rsa.pub
   ```

   If `pbcopy` is not available, you can manually copy the key from the `~/.ssh/id_rsa.pub` file.

7. **Add Public Key to Server**:
   Add your SSH public key to the `~/.ssh/authorized_keys` file on the server you want to access.

### Theme
The visual design and layout of an Omeka site. Themes determine how content is displayed to users and can be customized or developed to fit the branding of an organization.

### User Role
The permissions and access levels assigned to users within Omeka. Common roles include Administrator, Editor, and Viewer, each with different capabilities for managing content and settings.

_______

## Quick Links

For additional assistance, refer to the following resources:

- **[Omeka S Documentation](https://omeka.org/s/docs/user-manual/):** Access comprehensive user manuals and guides to help you navigate and make the most of Omeka S.
  
- **[Omeka Community Forums](https://forum.omeka.org/):** Engage with the community,  ask questions,  and share knowledge about Omeka S. This is a great place to seek help from fellow users and experts.
  
- **[Project Documentation on Google Docs](https://docs.google.com/document/d/1SeHBTbae9Vy685ENqmGGENyf6H65pgDo0QsXo1rcWMQ/edit?tab=t.0#heading=h.2ycpukh4lmq2):** As mentioned before, this sheet, from Yale University Library, is a goldmine of information. Please use. 

---

These resources provide valuable information and support to help you effectively use and troubleshoot Omeka S. Thanks for reading.

