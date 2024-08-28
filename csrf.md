CSRF: Cross-site request forgery

A cross-site request forgery attack tricks a victim into using their credentials to invoke a state-changing activity.

Scenario:

Victim User:
Alice is logged into her online banking account on Bank.com and has a session cookie that authenticates her.

Attacker:
Eve, the attacker, creates a malicious website (Evil.com) that contains a hidden form submission targeting Bank.com.

The Attack:
Eve sends a crafted email to Alice, enticing her to click a link to Evil.com.
Upon visiting Evil.com, in the background, a hidden form is automatically submitted to Bank.com on behalf of Alice without her knowledge.

The Form:
The hidden form on Evil.com might look like this
<form action="http://Bank.com/transfer" method="POST">
    <input type="hidden" name="toAccount" value="EveAccount">
    <input type="hidden" name="amount" value="1000">
</form>

The Consequence:
Since Alice is authenticated on Bank.com, her browser automatically includes the session cookie in the request sent to Bank.com.
As a result, a transfer of $1000 is made from Alice's account to Eve's account without Alice's consent.

Impact:
Eve successfully initiated a fraudulent transaction exploiting Alice's authenticated session on Bank.com without her knowledge

Prevent:
implement a mechanisms like CSRF tokens, which are unique tokens generated for each user session to validate the origin of a request.
