📘 Field Naming Standards in Dynamics 365

A clear guide to designing clean, predictable, and future-proof field names in Microsoft Dynamics 365 / Dataverse.

🧩 Purpose

This document explains how to name fields in Dynamics 365 / Dataverse using a consistent, scalable, and readable structure.
It helps developers, analysts, admins, and solution architects avoid technical debt and ensure predictable schema design.

🏷️ 1. Publisher Prefix

A publisher prefix is the foundation of every custom component in Dataverse.

✔ Why it matters

Prevents naming conflicts

Identifies the owner of each component

Supports proper ALM & solution layering

Keeps environments clean and maintainable

✔ Rules

Every custom field must start with your publisher prefix

The prefix must remain the same across all solutions

Do not mix multiple prefixes in the same project

✔ Examples
Prefix	Meaning
new_	generic custom prefix
crm_	internal CRM/Dynamics team
ksd_	KimiaSpeedy Dynamics (example)
🅿️ 2. PascalCase & Descriptive Naming
✔ Rules

Schema names must use PascalCase

No spaces, hyphens, or special characters

Each word begins with a capital letter

Avoid cryptic abbreviations

✔ Good Examples
crm_ContractEndDate
crm_HealthStatus
crm_TotalInvoiceAmount

❌ Bad Examples
crm-contract_end_date
crm_Date1
crm_status

💡 Why PascalCase?

Originating from the Pascal programming language (Niklaus Wirth, 1970), PascalCase increases readability, consistency, and code clarity.

📊 3. Data Type Naming Patterns

Use standard naming conventions so field purpose and datatype are clear at a glance.

Data Type	Naming Pattern	Example
Lookup	ends with Id	crm_AccountId
Boolean	starts with Is / Has	crm_IsActive, crm_HasDiscount
Date	ends with Date	crm_ContractDate
Money	ends with Amount	crm_TotalAmount
Integer	ends with Count / Number	crm_ItemCount
Decimal	ends with Value	crm_ScoreValue
Text	ends with Text or descriptive name	crm_DescriptionText
🗂️ 4. Display Name ≠ Schema Name
✔ Display Name

User-friendly

Can have spaces

Editable anytime
Example: Contract End Date

✔ Schema Name

Technical

Permanent

Must follow naming standards
Example: crm_ContractEndDate

❌ Never do this
crm_Contract end date
crm_Contract_End_Date_Label
crm_contract_end_date

⚠️ 5. Common Naming Mistakes (Avoid These)

Using names with numbers (crm_Date1, crm_Field2)

Using abbreviations nobody knows (crm_CED)

Including datatype in schema name (crm_DateString)

Naming based on UI layout (crm_FieldOnMainForm)

Duplicating entity names (crm_Account_AccountId)

📌 6. Examples (Correct vs Incorrect)
✔ Correct
crm_EmployeeStartDate
crm_OrderTotalAmount
crm_ProductCategoryId
crm_IsPremiumCustomer
crm_InvoiceLineCount

❌ Incorrect
crm_start
crm_amt_total
crm_prodId
crm_yesorno
crm_txt

🧾 7. Final Checklist

Before creating any field, verify:

 Uses correct prefix (crm_, ksd_, etc.)

 Uses PascalCase

 Descriptive and meaningful

 Matches datatype pattern

 Display name ≠ schema name

 No numbers in the name

 No unnecessary abbreviations

 Future-proof & stable

🔚 Final Advice

Good field names are cheap to create — but very expensive to fix later.
Design them once, design them right.
