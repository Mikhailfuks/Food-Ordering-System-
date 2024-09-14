<!DOCTYPE html>
<html>
<head>
  <title>Food Ordering System</title>
  <style>
    /* Basic styling for the example */
    .menu-item {
      border: 1px solid #ccc;
      padding: 10px;
      margin-bottom: 10px;
    }
    #cart-items {
      margin-top: 20px;
      border: 1px solid #ccc;
      padding: 10px;
    }
  </style>
</head>
<body>
  <h1>Food Ordering</h1>

  <div id="menu">
    <!-- Menu items will be displayed here -->
  </div>

  <h2>Your Cart</h2>
  <div id="cart-items">
    <!-- Cart items will be displayed here -->
  </div>

  <button onclick="placeOrder()">Place Order</button>

  <script src="script.js"></script>
</body>
</html>


// Sample menu data
const menuItems = [
  { id: 1, name: "Pizza", price: 12.99, description: "Classic pepperoni pizza" },
  { id: 2, name: "Burger", price: 8.99, description: "Juicy beef burger with cheese" },
  { id: 3, name: "Salad", price: 6.99, description: "Fresh mixed greens with dressing" },
  // Add more menu items
];

// Cart array to store selected items
const cart = [];

// Function to display the menu
function displayMenu() {
  const menuContainer = document.getElementById('menu');
  menuContainer.innerHTML = ''; // Clear previous menu

  menuItems.forEach(item => {
    const menuItem = document.createElement('div');
    menuItem.classList.add('menu-item');
    menuItem.innerHTML = 
      <h3>${item.name}</h3>
      <p>${item.description}</p>
      <p>Price: $${item.price.toFixed(2)}</p>
      <button onclick="addToCart(${item.id})">Add to Cart</button>
    ;
    menuContainer.appendChild(menuItem);
  });
}

// Function to add an item to the cart
function addToCart(itemId) {
  const item = menuItems.find(item => item.id === itemId);
  cart.push(item);
  updateCart();
  console.log(${item.name} added to cart);
}

// Function to update the cart display
function updateCart() {
  const cartItemsContainer = document.getElementById('cart-items');
  cartItemsContainer.innerHTML = ''; // Clear previous cart

  if (cart.length === 0) {
    cartItemsContainer.innerHTML = '<p>Your cart is empty</p>';
    return;
  }

  let totalPrice = 0;
  cart.forEach(item => {
    const cartItem = document.createElement('div');
    cartItem.innerHTML = 
      <h3>${item.name}</h3>
      <p>Price: $${item.price.toFixed(2)}</p>
    ;
    cartItemsContainer.appendChild(cartItem);
    totalPrice += item.price;
  });

  const totalPriceElement = document.createElement('p');
  totalPriceElement.textContent = Total: $${totalPrice.toFixed(2)};
  cartItemsContainer.appendChild(totalPriceElement);
}

// Function to simulate placing an order (would send data to a server in a real system)
function placeOrder() {
  if (cart.length === 0) {
    alert('Your cart is empty!');
    return;
  }

  console.log('Order placed!');
  console.log('Items:', cart);
  cart.length = 0; // Clear the cart
  updateCart();
}

// Display the initial menu
displayMenu();
