Where Client should use to store access token?
<br>
Problem: client need to store access token (usually JWT) to proceed protected request

Distinguish kind of client: smart devices OR web browser

Let SERVER decided
<br>
By:
- if client are smart devices => SERVER return token as casual => client use secure storage to store them
- if client are web browser => SERVER set token into cookie (httpOnly, secure)

another option: store in memory (RAM) only (not persistent)