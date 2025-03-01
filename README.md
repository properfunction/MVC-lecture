# Model-View-Controller (MVC) Architecture

## Introduction
MVC (Model-View-Controller) is a design pattern used in software engineering to separate concerns and organize code efficiently. It is commonly used in web development frameworks like Express.js, React (with variations like MVVM), and other JavaScript-based applications.

## Components of MVC

### 1. Model
- Represents the data and business logic of the application.
- Interacts with the database or external data sources.
- Notifies the View of any changes in the data.

**Example (Mongoose Model in Node.js):**
```javascript
const mongoose = require('mongoose');

const productSchema = new mongoose.Schema({
    name: String,
    price: Number
});

const Product = mongoose.model('Product', productSchema);
module.exports = Product;
```

### 2. View
- Displays the data to the user.
- Listens for user interactions.
- Requests updates from the Model when necessary.

**Example (EJS Template in Express.js):**
```html
<h1><%= product.name %></h1>
<p>Price: <%= product.price %></p>
```

### 3. Controller
- Acts as an intermediary between the Model and View.
- Handles user input and updates the Model accordingly.
- Directs the flow of data between components.

**Example (Express.js Controller):**
```javascript
const Product = require('../models/Product');

exports.getProductDetail = async (req, res) => {
    try {
        const product = await Product.findById(req.params.id);
        res.render('product_detail', { product });
    } catch (err) {
        res.status(500).send('Error retrieving product');
    }
};
```

## MVC Workflow

![Alt Text](https://github.com/properfunction/MVC-lecture/raw/main/assets/images/3c8fe45bbf034516a5e39e00499c7d10.png)


1. The **user interacts** with the application (e.g., clicks a button).
2. The **Controller processes** the user input and requests data from the Model.
3. The **Model updates** the requested data and sends it to the View.
4. The **View renders** the updated data and displays it to the user.

## Benefits of MVC
- **Separation of Concerns:** Easier to manage and scale the application.
- **Reusability:** Components can be reused independently.
- **Maintainability:** Facilitates debugging and testing.

## Conclusion
MVC is a fundamental architectural pattern that helps in structuring applications efficiently. It promotes code organization and allows teams to work on different components independently, making development more efficient and scalable.

