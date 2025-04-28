- 👋 Hi, I’m @candleVerse108
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
candleVerse108/candleVerse108 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CandleVerse - Online Store</title>
    <script src="https://cdn.jsdelivr.net/npm/qrcode@1.4.4/build/qrcode.min.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #333;
            color: white;
            padding: 10px 0;
            text-align: center;
        }
        header a {
            color: white;
            text-decoration: none;
            margin: 0 15px;
        }
        .main-content {
            padding: 20px;
            text-align: center;
        }
        .product {
            display: inline-block;
            margin: 20px;
            padding: 10px;
            border: 1px solid #ccc;
            width: 200px;
            text-align: center;
        }
        .cart {
            text-align: center;
            margin-top: 20px;
        }
        .payment-container {
            margin-top: 20px;
            padding: 20px;
            border: 2px solid #ccc;
            border-radius: 10px;
            width: 300px;
            margin: 0 auto;
        }
        .qr-code {
            margin-top: 20px;
        }
    </style>
</head>
<body>

<header>
    <a href="#">Home</a>
    <a href="#about">About</a>
    <a href="#contact">Contact</a>
    <a href="#login">Login</a> | <a href="#signup">Sign Up</a>
</header>

<div class="main-content">
    <h1>Welcome to CandleVerse</h1>
    <p>Your one-stop shop for amazing candles!</p>

    <div class="product">
        <h3>Candle 1</h3>
        <p>Price: ₹500</p>
        <button onclick="addToCart(500)">Add to Cart</button>
    </div>
    <div class="product">
        <h3>Candle 2</h3>
        <p>Price: ₹300</p>
        <button onclick="addToCart(300)">Add to Cart</button>
    </div>

    <div class="cart" id="cart-details">
        <h3>Your Cart</h3>
        <p>Total: ₹<span id="total-amount">0</span></p>
        <button onclick="checkout()">Proceed to Checkout</button>
    </div>
</div>

<div id="checkout" class="payment-container" style="display: none;">
    <h2>Pay with UPI</h2>
    <p>Scan the QR code below to make payment.</p>
    <div id="qrcode" class="qr-code"></div>
</div>

<script>
    let totalAmount = 0;

    function addToCart(price) {
        totalAmount += price;
        document.getElementById('total-amount').innerText = totalAmount;
    }

    function checkout() {
        var upiAddress = "your-upi-id@upi";  
        var amount = totalAmount;
        var note = "Payment for CandleVerse Order";

        var upiPaymentLink = `upi://pay?pa=${upiAddress}&pn=CandleVerse&mc=1234&tid=2025&tr=123456&tn=${note}&am=${amount}&cu=INR`;

        QRCode.toCanvas(document.getElementById('qrcode'), upiPaymentLink, function (error) {
            if (error) console.error(error);
            console.log("QR Code Generated!");
        });

        document.getElementById('checkout').style.display = 'block';
    }
</script>

<div id="about" class="main-content">
    <h2>About Us</h2>
    <p>At CandleVerse, we offer a wide variety of handcrafted candles to brighten up your space and make every occasion special.</p>
</div>

<div id="contact" class="main-content">
    <h2>Contact Us</h2>
    <p>Email: contact@candleverse.com</p>
    <p>Phone: +91 123 456 7890</p>
</div>

<div id="login" class="main-content">
    <h2>Login</h2>
    <p>Enter your credentials to log in.</p>
</div>

<div id="signup" class="main-content">
    <h2>Sign Up</h2>
    <p>Create an account to enjoy exclusive offers.</p>
</div>

</body>
</html>
