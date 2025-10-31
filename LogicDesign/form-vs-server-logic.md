# 🧠 Form-level vs Server-level Logic in Dynamics 365

When designing automation or validation in **Microsoft Dynamics 365**, one of the key architectural decisions is:

> **Where should the logic run?**  
> On the **form (client-side)** or on the **server (backend)**?

This choice determines **performance**, **user experience**, and **data reliability** — and is one of the first questions a professional consultant or architect should answer during solution design.

---

## 🔹 1. Form-level Logic (Client-side)

### 🧩 Concept  
Form-level logic runs **directly on the user interface (UI)** — before the record is saved.  
It reacts instantly to user actions and provides real-time feedback.

### ⚙️ Common Tools
- **Business Rules**
- **JavaScript (Client API)**
- **Form Scripts (onChange, onLoad events)**

### 💡 When to Use
| Scenario | Example |
|-----------|----------|
| Simple validation | Warn if *Discount > 20%* |
| Field visibility | Hide “Credit Limit” when “Customer Type = Retail” |
| Real-time calculation | Update “Total Price” when Quantity × Unit Price changes |

### ✅ Advantages
- Instant feedback — no need to save the record  
- Great for improving user experience  
- Easy to configure (especially Business Rules)

### ⚠️ Limitations
- Executes **only** when the form is open  
- Doesn’t run during **imports, API calls, or workflows**  
- Complex logic may require JavaScript coding

---

## 🔹 2. Server-level Logic (Backend)

### 🧩 Concept  
Server-level logic executes **after the record is saved**, within the CRM backend.  
It ensures that the business rule applies to **all data sources** — including forms, API, Power Automate, or integrations.

### ⚙️ Common Tools
- **Workflow / Power Automate**
- **Plugin (C#)**
- **Custom Action / API**
- **Business Process Flow (BPF)**

### 💡 When to Use
| Scenario | Example |
|-----------|----------|
| System-wide validation | Prevent duplicate Accounts during record creation |
| Post-save automation | Auto-create an Invoice when an Order is confirmed |
| Complex calculations | Update parent entity totals after child records are added |

### ✅ Advantages
- Runs for all record updates (UI, import, API)  
- Reliable for complex, multi-entity or hierarchical logic  
- Can be synchronous (real-time) or asynchronous (background)

### ⚠️ Limitations
- Feedback is not instant (user sees result after save)  
- Requires deeper technical setup (especially Plugins)  
- Debugging and maintenance can be more complex

---

## 🔹 3. Comparison Table

| Criteria | Form-level Logic | Server-level Logic |
|-----------|------------------|--------------------|
| **Runs in** | User form (UI) | CRM Server |
| **Timing** | Before save | After save |
| **Tools** | Business Rule / JavaScript | Workflow / Plugin / Power Automate |
| **Scope** | UI only | All operations (UI, API, Import) |
| **Best for** | Real-time validation, UX improvements | Complex automation, data consistency |

---

## 🔹 4. Design Considerations

When choosing between client and server logic, consider the following:

| Design Criterion | Description |
|------------------|--------------|
| **Performance** | Client-side logic is faster for simple checks, but heavy scripts can slow down forms. |
| **Data integrity** | Use server-side logic to enforce rules regardless of input method. |
| **User experience** | Use form logic to guide the user before saving data. |
| **Reusability** | Plugins and Custom Actions can be reused in multiple processes. |
| **Maintainability** | Business Rules are easiest to maintain; Plugins offer flexibility but require version control. |

---

## 🔹 5. Best Practices

✅ Use **Business Rules** for simple, UI-level logic (no code).  
✅ Use **JavaScript** for custom UI interactions and dynamic calculations.  
✅ Use **Workflows / Power Automate** for lightweight server-side automation.  
✅ Use **Plugins** for complex, high-performance backend logic.  
✅ Document where each rule runs (form or server) for maintainability and audits.  
✅ Keep heavy logic out of forms to improve performance.

---

## 🔹 6. Real-World Example

**Scenario:**  
A company wants to automatically approve Orders above 50M and show a red warning if Discount > 20%.

| Requirement | Logic Type | Tool |
|--------------|-------------|------|
| Show red warning for high discount | Form-level | Business Rule / JS |
| Auto-approve order and notify manager | Server-level | Plugin / Power Automate |

---

## 🧭 Summary

Choosing the right execution layer is the foundation of any well-designed Dynamics 365 solution.

> 💬 *Smart solution design starts with one question:*  
> **Where should this logic run — on the form or on the server?**

---

**Author:** Fatima Khodaei  
**Repository:** [BusinessAnalysisDocs](https://github.com/fatima-co/BusinessAnalysisDocs)  
**Tags:** Dynamics 365, Power Platform, Plugins, Business Rules, Solution Architecture, CRM Design
