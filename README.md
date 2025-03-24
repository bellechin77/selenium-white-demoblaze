# Test suite: Selenium White \- Demoblaze

## DemoBlaze Application Overview

## DemoBlaze is a simple e-commerce web application that allows users to browse, add products to a shopping cart, and complete purchases. It serves as a demo platform for testing web automation and UI interactions.

Key Features:  
✅ Product Catalog – Users can browse categories like Phones, Laptops, and Monitors.  
✅ Shopping Cart – Add, remove, and view selected items before checkout.  
✅ User Authentication – Signup, login, and logout functionality.  
✅ Order Placement – Users can enter their details and complete purchases.  
✅ Popup Alerts & Modals – Notifications confirm actions like adding products or completing an order.

### Test Automation created for User Stories

###  **(1) User Story: Sign Up** 

This story ensures that a new user can successfully create an account and receive confirmation of the action. 

| Given | When | Then |
| :---- | :---- | :---- |
| 🔹 A user is on the home page of the application. <br> 🔹 The user wants to create a new account. | 🔹 The user clicks on the "Sign up" link in the navigation bar. <br> 🔹 The sign-up form appears. <br> 🔹 The user enters a unique username and password. <br> 🔹 The user submits the sign-up form. | 🔹 The system displays an alert confirming that "Sign up successful".  |

###  **(2) User Story: Log in**

This user story ensures that a user can successfully log in with valid user credentials.

| Given | When | Then |
| :---- | :---- | :---- |
| 🔹 A user is on the home page of the application. <br> 🔹 The user has an existing account with a valid username and password. <br> 🔹 The "Log in" button is visible in the navigation menu. | 🔹 The user clicks on the "Log in" button. <br> 🔹 The login modal appears. <br> 🔹 The user enters valid credentials. <br> 🔹 The user clicks the "Log in" button in the modal.  | 🔹 The login modal closes. <br> 🔹 A welcome message appears in the navigation bar, displaying "Welcome \[username\]".  |

###  **(3) User Story: Order**

This user story outlines the key steps involved in adding products to the cart, confirming the order, and verifying the purchase success message.

| Given | When | Then |
| :---- | :---- | :---- |
| 🔹 A user is on the home page of the application. <br> 🔹 The category menu is visible, allowing the user to browse product categories. | 🔹 The user selects the Phones category and adds the first available phone to the cart. <br> 🔹 The user selects the Laptops category and adds the last available laptop to the cart. <br> 🔹 The user selects the Monitors category and adds a specific product, "Apple monitor 24," to the cart. <br> 🔹 The user navigates to the Cart page and verifies that all three selected products are present. <br> 🔹 The user proceeds to Place an Order, fills in the required details (Name, Country, City, Credit Card, Month, Year), and clicks on Purchase.  | 🔹 A confirmation popup appears with the message "Thank you for your purchase\!" <br> 🔹 The user clicks OK on the confirmation popup. <br> 🔹 The user is redirected back to the homepage, completing the purchase process.  |

### Test Cases added

| User story | Test case |
| :---- | :---- |
| Sign Up for a New Account | test\_signup.py |
| Log in | test\_login.py |
| Adding Multiple Products to the Shopping Cart | test\_order.py |

### Acceptance criteria

#### (1) Identifying web elements 

| Test | Interaction with different web elements |
| :---- | :---- |
| signup | `signup_btn = driver.find_element(By.ID, "signin2") username = driver.find_element(By.ID, "sign-username") password = driver.find_element(By.ID, "sign-password") signup_confirm = driver.find_element(By.XPATH, "//button[text()='Sign up']")` |
| login | `login_btn = driver.find_element(By.ID, "login2") username = driver.find_element(By.ID, "loginusername") password = driver.find_element(By.ID, "loginpassword") login_confirm = driver.find_element(By.XPATH, "//button[text()='Log in']")` |
| order | `cart_btn = driver.find_element(By.ID, "cartur") order_btn = driver.find_element(By.XPATH, "//button[text()='Place Order']") purchase_btn = driver.find_element(By.XPATH, "//button[text()='Purchase']") confirmation_text = driver.find_element(By.CLASS_NAME, "sweet-alert").text` |

#### (2) Simple interactions with web elements (ex: click, sendKeys)

| Class from parent code | Changes made to use selectors following best practices |
| :---- | :---- |
| signup | `signup_btn.click() username.send_keys(unique_username) password.send_keys("TestPass123") signup_confirm.click()` |
| login | `login_btn.click() username.send_keys(test_username) password.send_keys(test_password) login_confirm.click()` |
| order | `cart_btn.click() order_btn.click() driver.find_element(By.ID, "name").send_keys("John Doe") driver.find_element(By.ID, "country").send_keys("USA") driver.find_element(By.ID, "city").send_keys("New York") driver.find_element(By.ID, "card").send_keys("4111 1111 1111 1111") driver.find_element(By.ID, "month").send_keys("12") driver.find_element(By.ID, "year").send_keys("2025")` |
