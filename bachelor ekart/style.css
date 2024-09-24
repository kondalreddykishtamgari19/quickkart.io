const products = [
    { id: 1, name: "Apples", category: "Fruits", price: 2, img: "https://via.placeholder.com/150", description: "Fresh and juicy apples." },
    { id: 2, name: "Bananas", category: "Fruits", price: 1, img: "https://via.placeholder.com/150", description: "Sweet bananas." },
    { id: 3, name: "Carrots", category: "Vegetables", price: 1.5, img: "https://via.placeholder.com/150", description: "Crunchy carrots." },
    { id: 4, name: "Potatoes", category: "Vegetables", price: 0.5, img: "https://via.placeholder.com/150", description: "Starchy potatoes." },
    { id: 5, name: "Soap", category: "House Needs", price: 3, img: "https://via.placeholder.com/150", description: "Antibacterial soap." },
    { id: 6, name: "Toothpaste", category: "House Needs", price: 2, img: "https://via.placeholder.com/150", description: "Whitening toothpaste." },
];

let order = [];
let selectedProduct = null;
const payeeUPI = "example@upi";  // Replace with your UPI ID

const productList = document.getElementById('product-list');
const productDetails = document.getElementById('product-details');
const productName = document.getElementById('product-name');
const productImage = document.getElementById('product-image');
const productDescription = document.getElementById('product-description');
const productPrice = document.getElementById('product-price');
const addToCartButton = document.getElementById('add-to-cart-btn');

const cartItems = document.getElementById('cart-items');
const totalPriceElement = document.getElementById('total-price');
const proceedPaymentButton = document.getElementById('proceed-payment');

// Display products in the store
function displayProducts() {
    productList.innerHTML = '';
    products.forEach(product => {
        const productDiv = document.createElement('div');
        productDiv.classList.add('product');
        productDiv.innerHTML = `
            <img src="${product.img}" alt="${product.name}">
            <h2>${product.name}</h2>
            <p>${product.description}</p>
            <p>Price: $${product.price.toFixed(2)}</p>
            <button onclick="showProductDetails(${product.id})">View Details</button>
        `;
        productList.appendChild(productDiv);
    });
}

// Show product details when clicked
function showProductDetails(productId) {
    const product = products.find(p => p.id === productId);
    selectedProduct = product;
    productName.innerText = product.name;
    productImage.src = product.img;
    productDescription.innerText = product.description;
    productPrice.innerText = product.price.toFixed(2);
    productList.style.display = 'none';
    productDetails.style.display = 'block';
}

// Add product to cart
addToCartButton.addEventListener('click', () => {
    if (selectedProduct) {
        order.push(selectedProduct);
        updateOrderSummary();
        productDetails.style.display = 'none';
        productList.style.display = 'flex';
    }
});

// Update order summary after adding items to the cart
function updateOrderSummary() {
    cartItems.innerHTML = '';
    let total = 0;
    order.forEach(item => {
        cartItems.innerHTML += `<p>${item.name} - $${item.price.toFixed(2)}</p>`;
        total += item.price;
    });
    totalPriceElement.innerText = total.toFixed(2);

    if (order.length > 0) {
        proceedPaymentButton.style.display = 'block';
    }
}

// Open the payment modal after clicking "Proceed to Payment"
function openPaymentModal() {
    document.getElementById('payment-modal').style.display = 'block';
}

// Close payment modal
function closeModal() {
    document.getElementById('payment-modal').style.display = 'none';
}

// Show UPI options when UPI is selected as payment method
function showPaymentOptions() {
    const method = document.getElementById('payment-method').value;
    const upiOptions = document.getElementById('upi-options');
    
    if (method === 'upi') {
        upiOptions.style.display = 'block';
    } else {
        upiOptions.style.display = 'none';
    }
}

// Redirect to selected UPI app for payment
function redirectToUPI() {
    const upiApp = document.getElementById('upi-app').value;
    const totalAmount = parseFloat(totalPriceElement.innerText).toFixed(2);
    const upiLink = generateUPILink(upiApp, payeeUPI, totalAmount);

    window.location.href = upiLink;
}

// Generate UPI payment link based on the app selected
function generateUPILink(upiApp, upiID, amount) {
    let appScheme;
    switch (upiApp) {
        case "phonepe":
            appScheme = "phonepe://pay";
            break;
        case "gpay":
            appScheme = "tez://upi/pay";
            break;
        case "paytm":
            appScheme = "paytmmp://pay";
            break;
        default:
            return;
    }
    
    return `${appScheme}?pa=${upiID}&pn=OnlineStore&am=${amount}&tn=OrderPayment`;
}

// Initial display of products
displayProducts();
