// Set cookie Java Spring
<br>
HttpServletResponse response
<br>
Cookie cookie = new Cookie("username", "value");
<br>
cookie.setHttpOnly(true);
<br>
response.addCookie(cookie);

// Get cookie
<br>
HttpServletRequest request
<br>
Cookie[] cookies = request.getCookies();

// Delete cookie
<br>
HttpServletResponse response
<br>
Cookie cookie = new Cookie("username", null); => use the same name as the cookie you set before
<br>
cookie.setMaxAge(0); => inportant
<br>
cookie.setHttpOnly(true);
<br>
response.addCookie(cookie);

// Explanation
<br>
setMaxAge: set the cookie expiration time
<br>
setSecure: only sent over HTTPS, not HTTP
<br>
setHttpOnly:
- tells the browser that this particular cookie should only be accessed by the server
- prevent XSS attack
- canot get from document.cookie
