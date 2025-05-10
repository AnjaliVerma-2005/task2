# Simple E-Commerce CLI App

products = {
    1: {"name": "Laptop", "price": 999.99},
    2: {"name": "Phone", "price": 599.99},
    3: {"name": "Headphones", "price": 199.99},
    4: {"name": "Smartwatch", "price": 149.99}
}

cart = []

def show_products():
    print("\nAvailable Products:")
    for pid, info in products.items():
        print(f"{pid}. {info['name']} - ${info['price']:.2f}")

def add_to_cart():
    show_products()
    try:
        pid = int(input("Enter the product number to add to cart: "))
        if pid in products:
            cart.append(products[pid])
            print(f"{products[pid]['name']} added to cart.")
        else:
            print("Invalid product ID.")
    except ValueError:
        print("Please enter a valid number.")

def view_cart():
    if not cart:
        print("\nYour cart is empty.")
        return
    print("\nYour Cart:")
    total = 0
    for idx, item in enumerate(cart, 1):
        print(f"{idx}. {item['name']} - ${item['price']:.2f}")
        total += item['price']
    print(f"Total: ${total:.2f}")

def checkout():
    if not cart:
        print("Your cart is empty. Add items before checking out.")
        return
    view_cart()
    confirm = input("Proceed to checkout? (y/n): ").lower()
    if confirm == 'y':
        print("Checkout complete! Thank you for your purchase.")
        cart.clear()
    else:
        print("Checkout canceled.")

def main():
    while True:
        print("\n--- E-Commerce Menu ---")
        print("1. View Products")
        print("2. Add to Cart")
        print("3. View Cart")
        print("4. Checkout")
        print("5. Exit")

        choice = input("Choose an option (1-5): ")

        if choice == '1':
            show_products()
        elif choice == '2':
            add_to_cart()
        elif choice == '3':
            view_cart()
        elif choice == '4':
            checkout()
        elif choice == '5':
            print("Thank you for visiting! Goodbye.")
            break
        else:
            print("Invalid choice. Please select from the menu.")

if __name__ == "__main__":
    main()
# task2
