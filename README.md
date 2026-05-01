# Demo Web Shop – Pytest-Playwright E2E Test Suite

This repository contains **end-to-end (E2E) tests** written using **pytest-playwright** for the [Demo Web Shop](https://demowebshop.tricentis.com) application, covering user registration, login, and shopping cart functionality.

**Application under test:** [https://demowebshop.tricentis.com](https://demowebshop.tricentis.com)

---

## Project Overview

The purpose of this project is to validate key user flows in the Demo Web Shop using
**Python-based browser automation**. The tests simulate real user interactions to
ensure that critical features — registration, authentication, and cart management —
behave correctly across different browsers.

This project uses **pytest** as the test runner and **Playwright for Python**
for browser automation.

---

## Project Structure

```
ecommerce-playwright-tests/
├── conftest.py               # Shared pytest fixtures
├── requirements.txt          # Python dependencies
├── helpers/
│   ├── config.example.py     # Credentials template (copy to config.py)
│   └── random_email.py       # Utility: random email generator
├── pages/
│   ├── cart_page.py          # Cart page object
│   ├── login_page.py         # Login page object
│   └── register_page.py      # Registration page object
├── testdata/
│   ├── data.json             # Registration test data
│   └── products.json         # Product test data for cart tests
└── tests/
    ├── test_register.py      # User registration tests
    ├── test_login.py         # User login tests
    └── test_add_to_cart.py   # Shopping cart tests
```

---

## Test Scope

The automated tests cover (but are not limited to):

**Registration**

- Registering a new user account with valid data
- Validating form fields and error messages
- Parameterised registration using test data from `testdata/data.json`

**Login**

- Logging in with valid credentials
- Navigating to the login page and verifying successful authentication

**Shopping Cart**

- Navigating to the Demo Web Shop
- Adding products to the shopping cart
- Opening and validating the cart page
- Updating product quantities
- Removing products from the cart
- Verifying cart totals, messages, and UI elements
- Basic assertions for page content and behavior

---

## Tech Stack

- **Python** – Programming language
- **pytest** – Test framework
- **Playwright (Python)** – Browser automation library
- **pytest-playwright** – Pytest plugin for Playwright integration

---

## Prerequisites

Ensure the following are installed on your system:

- **Python 3.9+**
- **pip** (Python package manager)

## Installation

1. Clone the repository:

```bash
git clone https://github.com/ekundayoSO/ecommerce-playwright-tests.git
cd ecommerce-playwright-tests
```

2. Create and activate a virtual environment (recommended):

```bash
python -m venv venv
source venv/bin/activate      # macOS / Linux
venv\\Scripts\\activate         # Windows
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Install Playwright browsers:

```bash
playwright install
```

5. Set up credentials:

```bash
cp helpers/config.example.py helpers/config.py
```

Then open `helpers/config.py` and replace the placeholder values with your Demo Web Shop account credentials:

```python
class LoginCredentials:
    email = "your_email@example.com"
    password = "your_password"
```

> **Note:** `config.py` is excluded from version control. Never commit real credentials.

---

## Running Tests

Run all tests in headless mode:

```bash
pytest
```

Run tests in headed (UI) mode:

```bash
pytest --headed
```

Run tests in a specific browser:

```bash
pytest --browser chromium
pytest --browser firefox
pytest --browser webkit
```

Run a specific test file:

```bash
pytest tests/test_add_to_cart.py
pytest tests/test_login.py
pytest tests/test_register.py
```

---

## Test Reports

Pytest output is shown in the terminal by default.

To generate an HTML report (optional), install `pytest-html` and run:

```bash
pytest --html=report.html
```

---

## Supported Browsers

Using pytest-playwright, tests can run on:

- Chromium
- Firefox
- WebKit

Browser selection is controlled via pytest command-line options.

---

## Best Practices Followed

- Clear and descriptive test names
- Reusable pytest fixtures
- Independent and repeatable test cases
- Reliable Playwright locators
- No hard-coded waits (uses auto-waiting and assertions)

---

## Notes

- The Demo Web Shop is a **public demo application**, so product data or cart behavior may reset.
- Tests should not depend on persistent cart state between runs.

---

## License

This project is intended for **learning, practice, and demonstration purposes only**.

---

## Author

Created by **Ekundayo** as a **pytest-playwright E2E testing practice project**.
