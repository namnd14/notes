// Set cookie Java Spring
HttpServletResponse response
Cookie cookie = new Cookie("username", "value");
cookie.setHttpOnly(true);
response.addCookie(cookie);

// Get cookie
HttpServletRequest request
Cookie[] cookies = request.getCookies();

// Delete cookie
HttpServletResponse response
Cookie cookie = new Cookie("username", null); => use the same name as the cookie you set before
cookie.setMaxAge(0); => inportant
cookie.setHttpOnly(true);
response.addCookie(cookie);

// Explanation
setMaxAge: set the cookie expiration time
setSecure: only sent over HTTPS, not HTTP
setHttpOnly:
- tells the browser that this particular cookie should only be accessed by the server
- prevent XSS attack
- canot get from document.cookie
