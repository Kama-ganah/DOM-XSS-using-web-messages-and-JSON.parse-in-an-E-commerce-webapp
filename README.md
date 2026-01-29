# Overview
As a penetration tester, I assessed the application’s client-side message handling and identified a DOM-based Cross-Site Scripting (XSS) vulnerability involving postMessage and unsafe use of JSON.parse(). By sending a crafted JSON message from a malicious iframe, it was possible to execute arbitrary JavaScript in the victim’s browser, demonstrated via the print() function. This project highlights the risks of unvalidated cross-origin messaging and unsafe parsing in modern web applications.

# Steps Undertaken

Step 1: Analyzed homepage JavaScript to locate window.addEventListener("message", ...) usage.

Step 2: Confirmed that JSON.parse() was applied directly to incoming messages without origin validation.

Step 3: Identified a code path where a load-channel message could set an iframe’s src attribute based on attacker-controlled input.

Step 4: Crafted a malicious iframe payload on the exploit server to deliver a JSON message with url: "javascript:print()".

Step 5: Verified JavaScript execution in the victim’s browser via the print() function, confirming successful exploitation.

# Conclusion

This assessment confirmed a high-severity DOM XSS vulnerability via unsafe postMessage handling. Proper origin checks, input validation, and safe handling of JSON data are essential to prevent arbitrary script execution and protect user sessions and data integrity.
