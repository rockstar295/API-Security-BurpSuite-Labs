# API Security Labs Report (Burp Suite)

## 👤 Author

Name: Gaurav Jangir
Course: BCA (2nd Year)

---

# 📌 Introduction

This project demonstrates practical API security testing using Burp Suite. The objective was to identify vulnerabilities in web applications by intercepting and manipulating API requests.

---

# 🔬 Lab 1: Exploiting API Endpoint Using Documentation

## 🎯 Objective

Discover hidden API endpoints and perform unauthorized actions.

## 🛠️ Steps

1. Login using credentials (wiener:peter)
2. Intercept PATCH request: `/api/user/wiener`
3. Send request to Repeater
4. Modify endpoint:

   * `/api/user` → Error
   * `/api` → API documentation found
5. Open documentation in browser
6. Use DELETE endpoint

## 💥 Exploit

```
DELETE /api/user/carlos
```

## ✅ Result

User "carlos" deleted successfully.

## ⚠️ Vulnerability

* Broken Access Control
* Exposed API Documentation

---

# 🔬 Lab 2: Exploiting API for Price Manipulation

## 🎯 Objective

Modify product price using API request.

## 🛠️ Steps

1. Intercept product API request
2. Change method: GET → PATCH
3. Add header:

```
Content-Type: application/json
```

4. Add body:

```
{"price":0}
```

## 💥 Exploit

```
PATCH /api/products/1/price
```

## ✅ Result

Product price changed to $0.00.

## ⚠️ Vulnerability

* Broken Access Control
* Business Logic Flaw
* Mass Assignment

---

# 🔬 Lab 3: Checkout Manipulation

## 🎯 Objective

Place order using manipulated data.

## 🛠️ Steps

1. Intercept checkout request
2. Analyze JSON body
3. Modify parameters (optional):

   * price
   * discount
   * quantity

## 💥 Exploit Example

```
{
  "chosen_discount": {"percentage": 100},
  "chosen_products": [{"product_id": "1", "quantity": 1}]
}
```

## ✅ Result

Order placed successfully with manipulated price.

## ⚠️ Vulnerability

* Client-side trust issue
* Business Logic Vulnerability

---

# 🧠 Key Learnings

* API endpoint discovery techniques
* Importance of authorization checks
* Risks of trusting client input
* Practical use of Burp Suite (Proxy, Repeater)

---

# 🛡️ Prevention (Security Measures)

* Implement proper authentication & authorization
* Validate all inputs on server-side
* Restrict API documentation access
* Use role-based access control (RBAC)
* Monitor API activity

---

# 🚀 Conclusion

This project highlights how insecure API implementations can lead to critical vulnerabilities such as unauthorized access, data manipulation, and financial loss. Proper security controls are essential to protect modern web applications.

---

# ⭐ GitHub Upload Suggestion

Repo Name: `API-Security-BurpSuite-Labs`

Include:

* README.md (this report)
* Screenshots (Burp requests/responses)
* Notes (commands & payloads)

---

✅ Project Ready for Submission & GitHub Portfolio
