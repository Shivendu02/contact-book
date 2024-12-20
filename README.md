class ContactBook:
    def __init__(self):
        self.contacts = {}

    def add_contact(self, name, phone, email):
        if name in self.contacts:
            print(f"Contact with the name '{name}' already exists.")
        else:
            self.contacts[name] = {"Phone": phone, "Email": email}
            print(f"Contact '{name}' added successfully.")

    def view_contacts(self):
        if not self.contacts:
            print("No contacts available.")
        else:
            print("\nContact List:")
            for name, details in self.contacts.items():
                print(f"Name: {name}, Phone: {details['Phone']}, Email: {details['Email']}")

    def search_contact(self, name):
        contact = self.contacts.get(name)
        if contact:
            print(f"\nFound Contact: Name: {name}, Phone: {contact['Phone']}, Email: {contact['Email']}")
        else:
            print(f"Contact with the name '{name}' not found.")

    def update_contact(self, name, phone=None, email=None):
        if name in self.contacts:
            if phone:
                self.contacts[name]["Phone"] = phone
            if email:
                self.contacts[name]["Email"] = email
            print(f"Contact '{name}' updated successfully.")
        else:
            print(f"Contact with the name '{name}' does not exist.")

    def delete_contact(self, name):
        if name in self.contacts:
            del self.contacts[name]
            print(f"Contact '{name}' deleted successfully.")
        else:
            print(f"Contact with the name '{name}' does not exist.")


def main():
    contact_book = ContactBook()

    while True:
        print("\nContact Book Menu:")
        print("1. Add Contact")
        print("2. View Contacts")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")

        choice = input("Enter your choice (1-6): ")

        if choice == "1":
            name = input("Enter name: ")
            phone = input("Enter phone number: ")
            email = input("Enter email address: ")
            contact_book.add_contact(name, phone, email)
        elif choice == "2":
            contact_book.view_contacts()
        elif choice == "3":
            name = input("Enter the name to search: ")
            contact_book.search_contact(name)
        elif choice == "4":
            name = input("Enter the name to update: ")
            phone = input("Enter new phone number (or press Enter to skip): ")
            email = input("Enter new email address (or press Enter to skip): ")
            contact_book.update_contact(name, phone if phone else None, email if email else None)
        elif choice == "5":
            name = input("Enter the name to delete: ")
            contact_book.delete_contact(name)    
        elif choice == "6":
            print("Exiting Contact Book. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")


if __name__ == "__main__":
    main()
