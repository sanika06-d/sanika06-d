NAME: SANIKA BOTE. 
#include <stdio.h>
#include <string.h>
typedef struct {
 char name[100];
 float price;
 int quantity;
} Product;
void displayProducts(Product products[], int numProducts) {
 printf("Available Products:\n");
 for (int i = 0; i < numProducts; i++) {
  printf("%d. %s - $%.2f (%d available)\n", i + 1, products[i].name, products[i].price, products[i].quantity);
    }
}
void addToCart(Product products[], int numProducts, int *cart, int *cartSize) {
    int choice;
    printf("Enter the number of the product to add to cart: ");
    scanf("%d", &choice);
    choice--;
    if (choice >= 0 && choice < numProducts && products[choice].quantity > 0) {
        cart[*cartSize] = choice;
        (*cartSize)++;
        products[choice].quantity--;
        printf("Product added to cart successfully.\n");
    } else {
        printf("Invalid choice or product out of stock.\n");
    }
}
void viewCart(Product products[], int numProducts, int cart[], int cartSize) {
    printf("Your Cart:\n");
    float total = 0;
    for (int i = 0; i < cartSize; i++) {
        printf("%d. %s - $%.2f\n", i + 1, products[cart[i]].name, products[cart[i]].price);
        total += products[cart[i]].price;
    }
    printf("Total: $%.2f\n", total);
}

void checkout(Product products[], int numProducts, int cart[], int cartSize) {
    float total = 0;
    for (int i = 0; i < cartSize; i++) {
        total += products[cart[i]].price;
    }
    printf("Thank you for shopping! Your total is: $%.2f\n", total);
}

int main() {
    
    Product products[] = {
        {"Apple iPhone", 80000, 5},
        {"Samsung TV", 35000, 3},
        {"Sony Headphones"25000, , 10},
        {"Dell Laptop", 75000, 7},
        {"Canon Camera", 50000, 8}
    };
    int numProducts = sizeof(products) / sizeof(products[0]);
    int cart[100];
    int cartSize = 0;

    while (1) {
        printf("Online Shopping\n");
        printf("1. Display Products\n");
        printf("2. Add Product to Cart\n");
        printf("3. View Cart\n");
        printf("4. Checkout\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        int choice;
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                displayProducts(products, numProducts);
                break;
            case 2:
                displayProducts(products, numProducts);
                addToCart(products, numProducts, cart, &cartSize);
                break;
            case 3:
                viewCart(products, numProducts, cart, cartSize);
                break;
            case 4:
                checkout(products, numProducts, cart, cartSize);
                return 0;
            case 5:
                return 0;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}
