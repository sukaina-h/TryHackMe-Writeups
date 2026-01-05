# 🌐 Web Application Basics — TryHackMe Notes

These notes document my learning from the **Web Application Basics** room on TryHackMe.  
They cover how web applications work, their components, HTTP communication, and core security concepts.

---

## 🌍 Web Application Analogy: A Planet

A web application can be compared to a **planet**:

- **Astronauts** → Users with a web browser
- **Planet surface** → What users can see and interact with
- **Under the surface** → Systems that keep the application running

Users only see the surface, but many critical components operate behind the scenes.

---

## 🎨 Front End (Client Side)

The **Front End** is what users interact with in their browser.

### HTML (HyperText Markup Language)
- Provides the **structure** of a web page
- Tells the browser *what* to display
- Comparable to **DNA instructions** for simple organisms

📌 Without CSS or JavaScript, HTML pages appear plain and static.

---

### CSS (Cascading Style Sheets)
- Controls the **appearance** of the web page
- Defines colours, layouts, fonts, and spacing
- Comparable to DNA traits like **colour, shape, and texture**

📌 CSS makes the web page visually appealing.

---

### JavaScript (JS)
- Adds **logic, interaction, and dynamic behavior**
- Enables decisions and responses based on user actions
- Comparable to the **brain** of an organism

📌 JavaScript allows features like form validation, animations, and dynamic content updates.

---

## ⚙️ Back End (Server Side)

The **Back End** includes everything that users don’t directly see but rely on.

---

### 🗄️ Database
- Stores, modifies, and retrieves data
- Examples:
  - User profiles
  - Preferences
  - Login details

📌 Similar to libraries, maps, and filing cabinets on a planet.

---

### 🏗️ Infrastructure
Includes:
- Web servers
- Application servers
- Storage systems
- Networking devices

📌 Comparable to roads, vehicles, fuel, and power systems on a planet.

---

### 🔥 Web Application Firewall (WAF)
- Filters malicious or suspicious requests
- Protects the web server from attacks

📌 Similar to a planet’s **atmosphere** protecting against harmful radiation.

---

## 🧾 Uniform Resource Locator (URL)

A **URL** is the web address used to access online resources.

### URL Components

| Component | Description |
|---------|------------|
| Scheme | Protocol used (HTTP / HTTPS) |
| User | Credentials in URL (rare & insecure) |
| Host / Domain | Identifies the website |
| Port | Specifies service (80 = HTTP, 443 = HTTPS) |
| Path | Location of the resource |
| Query String | User-supplied parameters |
| Fragment | Points to a specific section |

📌 Security risks include:
- Typosquatting
- Injection via query strings
- Insecure path access

---

## 📡 HTTP Messages

HTTP messages are how **clients (browsers)** and **servers** communicate.

### Two Types
- **HTTP Requests** → Sent by the client
- **HTTP Responses** → Sent by the server

---

### HTTP Message Structure

1. **Start Line**
2. **Headers**
3. **Empty Line**
4. **Body**

📌 Proper structure ensures correct communication and security.

---

## 📤 HTTP Requests

An HTTP request is sent by a user to perform an action on a web application.

---

### Request Line Format

METHOD /path HTTP/version
---

### Common HTTP Methods

| Method | Purpose | Security Consideration |
|------|--------|------------------------|
| GET | Retrieve data | Avoid sensitive data in URLs |
| POST | Send data | Validate & sanitise input |
| PUT | Update data | Authorisation required |
| DELETE | Remove data | Restrict access |
| PATCH | Partial update | Validate data |
| HEAD | Headers only | Metadata exposure |
| OPTIONS | Available methods | Often restricted |
| TRACE | Debugging | Usually disabled |
| CONNECT | Secure tunneling | Used for HTTPS |

---

### URL Path Security
- Validate paths
- Prevent unauthorised access
- Protect sensitive resources

---

### HTTP Versions

| Version | Key Features |
|------|-------------|
| HTTP/0.9 | GET only |
| HTTP/1.0 | Headers added |
| HTTP/1.1 | Persistent connections |
| HTTP/2 | Multiplexing, compression |
| HTTP/3 | QUIC-based, faster & secure |

---

## 🧩 Request Headers

| Header | Description |
|------|------------|
| Host | Target web server |
| User-Agent | Browser information |
| Referer | Source URL |
| Cookie | Stored session data |
| Content-Type | Data format |

---

## 📦 Request Body Formats

### URL Encoded
- key1=value1&key2=value2


### Form Data
- Used for file uploads
- Supports binary data

### JSON
`{
  "name": "Aleksandra",
  "age": 27,
  "country": "US"
}`

### XML
`<user>
  <name>Aleksandra</name>
  <age>27</age>
  <country>US</country>
</user>`

---

## HTTP Responses 

HTTP responses tell the client whether a request **succeeded or failed** and provide relevant data or error information.

---

## Status Line

The **Status Line** is the first line of an HTTP response and includes:

- **HTTP version**
- **Status code**
- **Reason phrase**

Example:
`HTTP/1.1 200 OK`

---

# 📊 HTTP Status Codes, Response Headers & Security Headers

---

## 📊 Status Code Categories

| Range | Meaning |
|------|--------|
| 100–199 | Informational |
| 200–299 | Success |
| 300–399 | Redirection |
| 400–499 | Client errors |
| 500–599 | Server errors |

---

## ✅ Common Status Codes

| Code | Meaning |
|----|--------|
| 200 | OK |
| 301 | Moved Permanently |
| 404 | Not Found |
| 500 | Internal Server Error |

---

## 📑 Response Headers

Response headers provide **metadata** about the HTTP response.

---

### 🔹 Required Headers

- **Date** – When the response was generated  
- **Content-Type** – Format of the response body  
- **Server** – Information about the server  
  *(Often hidden for security reasons)*

**Example:*Content-Type: application/json*


---

### 🔹 Other Common Headers

- **Set-Cookie** – Stores session or tracking data  
- **Cache-Control** – Controls caching behavior  
- **Location** – Used for redirection  

**Example:*Set-Cookie: sessionid=abc123; HttpOnly; Secure*


📌 **Best Practice:**  
Cookies should use the `HttpOnly` and `Secure` flags to reduce **XSS** and **MITM** risks.

---

## 🛡️ Security Headers

Security headers help protect web applications from common attacks.

---

### 🔐 Content-Security-Policy (CSP)

Controls which sources are allowed to load content.

**Example:*Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.tryhackme.com*


📌 Helps prevent **Cross-Site Scripting (XSS)** attacks.

---

### 🔒 Strict-Transport-Security (HSTS)

Forces browsers to use **HTTPS only**.

**Example:*Strict-Transport-Security: max-age=63072000; includeSubDomains; preload*


📌 Prevents **SSL stripping** attacks.

---

### 🚫 X-Content-Type-Options

Prevents MIME type sniffing.

**Example:*X-Content-Type-Options: nosniff*


📌 Protects against malicious file execution.

---

### 🔍 Referrer-Policy

Controls how much referrer information is shared.

**Common options:**
- `no-referrer`
- `same-origin`
- `strict-origin`
- `strict-origin-when-cross-origin`

**Example:*Referrer-Policy: strict-origin-when-cross-origin*


---

## 🧪 Practical API Requests (Static Site)

These requests were performed on the **TryHackMe static API**.

---

### 🔹 GET Request

*GET /api/users*

**Flag: THM{YOU_HAVE_JUST_FOUND_THE_USER_LIST}**


---

### 🔹 POST Request

*POST /api/user/2*

Updated **Bob’s country** from **UK → US**

**Flag:THM{YOU_HAVE_MODIFIED_THE_USER_DATA}**


---

### 🔹 DELETE Request

*DELETE /api/user/1*
Deleted a user record.

**Flag: THM{YOU_HAVE_JUST_DELETED_A_USER}**


---

## 🎯 Key Takeaways

- Understood **front-end vs back-end** components  
- Learned **URL anatomy** and associated security risks  
- Explored **HTTP requests and responses**  
- Practiced **API interaction** using multiple HTTP methods  
- Gained insight into **web security headers**
