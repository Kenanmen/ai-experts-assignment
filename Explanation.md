# Explanation of Bug Fix

**What was the bug?**  
If `Client.oauth2_token` was a dictionary instead of an `OAuth2Token` object, the token was never refreshed.  
This caused API requests to use stale credentials and fail the authorization check.

**Why did it happen?**  
The original code only refreshed the token if it was `None` or an expired `OAuth2Token`.  
It ignored tokens that were dictionaries, so the stale dict token stayed in use.

**Why does my fix actually solve it?**  
We now refresh the token if it is missing, expired, or not an `OAuth2Token` instance.  
This ensures that every API request uses a valid `OAuth2Token` object, so the Authorization header is always correct.

**One realistic case / edge case your tests still don’t cover**  
A malformed token dictionary that is missing the `access_token` or `expires_at` keys could still cause unexpected behavior.  
For example, `{"access_token": "ok"}` without `expires_at` would not be fully handled.
