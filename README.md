# Selenium_Navigation
# 6/10/2026
Amazon Selenium Automation
This project automates the basic shopping flow on Amazon using Python and Selenium.
Automation Steps
1.Open Amazon
2.Search for phones
3.Open the first product
4.Add the product to cart
5.Open the cart
6.Proceed to checkout
7.Display the checkout page title and URL
# Code
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()
driver.maximize_window()

wait = WebDriverWait(driver, 20)

# 1. HOME PAGE
driver.get("https://www.amazon.in/")

print("Home Page:")
print(driver.title)


# 2. SEARCH PHONE
search = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "twotabsearchtextbox")
    )
)

search.send_keys("phones")
search.send_keys(Keys.ENTER)


# 3. SEARCH RESULTS → PRODUCT PAGE
product = wait.until(
    EC.element_to_be_clickable(
        (By.CSS_SELECTOR, "div[data-component-type='s-search-result'] h2 a")
    )
)

product.click()

print("Product Page:")
print(driver.title)


# 4. PRODUCT PAGE → CART
add_cart = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "add-to-cart-button")
    )
)

add_cart.click()


# 5. PRODUCT → CART PAGE
cart = wait.until(
    EC.element_to_be_clickable(
        (By.ID, "nav-cart")
    )
)

cart.click()

print("Cart Page:")
print(driver.title)


# 6. CART → CHECKOUT
proceed = wait.until(
    EC.element_to_be_clickable(
        (By.NAME, "proceedToRetailCheckout")
    )
)

proceed.click()


# 7. CHECKOUT / BILLING PAGE
print("Checkout Page:")
print(driver.title)
print(driver.current_url)


input("Press Enter to close...")
driver.quit()
```

# Output:
<img width="1851" height="950" alt="Screenshot 2026-10-07 103824" src="https://github.com/user-attachments/assets/4f4f9b0f-9c24-4c7f-a245-d29891604e4d" />
<img width="1875" height="987" alt="Screenshot 2026-10-07 103833" src="https://github.com/user-attachments/assets/aee4fa18-8b1f-4264-b55a-4b2dac663095" />
<img width="1870" height="958" alt="Screenshot 2026-10-07 103907" src="https://github.com/user-attachments/assets/8ec176b0-c204-429c-a0b2-5dd02c13c100" />

