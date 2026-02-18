# 📚 Study Notes: Fundamentals of Web Apps (Part 0b)

## 1. The Developer Console is Your Best Friend
* **Rule #1 of Web Development:** Always keep the developer console open (`F12` or `Ctrl+Shift+I` / `Cmd+Opt+I`).
* **Console Tab:** Used to view application logs (`console.log`), errors, and execute JavaScript directly in the browser.
* **Network Tab:** Used to monitor HTTP requests and responses between the browser and the server. 
    * 💡 **Pro-Tip - Disable Cache:** Always check "Disable cache" while developing to ensure you are loading the newest code, not a saved version.
    * 💡 **Pro-Tip - Preserve Log:** Check "Preserve log" when tracking form submissions. Otherwise, page redirects will instantly erase the network history you are trying to inspect!

## 2. HTTP Protocol & Status Codes
The browser and server communicate using the HTTP protocol. 
* **HTTP GET:** Used to fetch resources (HTML, CSS, images, JS scripts, JSON data). 
* **HTTP POST:** Used to send data *to* the server (like submitting a new note).
* **Common HTTP Status Codes to Memorize:**
    * `200 OK`: Request succeeded (used for successful GET requests).
    * `201 Created`: Request succeeded and a new resource was created (used in SPAs for POST requests).
    * `302 Found / Redirect`: Server tells the browser to go to a new URL (used in traditional web apps after a POST).
    * `404 Not Found`: The requested resource doesn't exist.
    * `500 Internal Server Error`: The server crashed or had an error processing the request.

## 3. Traditional Web Apps vs. Single Page Applications (SPAs)
* **Traditional Web Apps:**
    * The server dynamically builds the exact HTML string and sends it to the browser.
    * The browser is "dumb" and just renders what it receives.
    * **Form Submissions:** Sending a POST request usually results in an **HTTP 302 Redirect**, forcing the browser to issue a new GET request and *reload the entire page* to show new data.
* **Single Page Applications (SPAs):**
    * The browser fetches a single, mostly empty HTML skeleton and a JavaScript file.
    * JavaScript takes over, fetches raw data (JSON), and builds the UI dynamically.
    * **Form Submissions:** JavaScript intercepts the form submit (`e.preventDefault()`). It instantly updates the screen locally, sends the new data via an async POST request, and receives a **201 Created** response. *No page re
