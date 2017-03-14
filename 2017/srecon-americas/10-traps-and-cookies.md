# Traps and Cookies

- Power switch on the LDAP server crushed by a toolbox

## Postmortem
- Human error?
- Force majeure?
- TRAP!
  - Forced the user to act perfectly.

## Planning for a perfect user
- "We had been told many times that astronauts would not make any mistakes.
  They were trained to be perfect."
- Humans are not at their best at 0300.
  - Can you make things safer?
  - Yes. Leave people cookies.
    - Documentation? (Can also be a trap.)
  - Don't write documentation examples that delete your CEO.
  - Principle of least astonishment. Humans don't compute/evaluate things all
    the time.

## The thing that is different
- tar -v, ln -v, ...
  - pkill -v # Oops.
- Be predictable.
  - Make predictable cookie.

## Big enticing red buttons
- People will find big red threatening buttons.
  - Clean up old customer records.
  - If there are checkboxes, add another one "I'm not reading these and I'm
    reading all the checkboxes."

## Excessive --force
- sudo is granular
- -f / --force is not.
- Alertmanager silences

## Being too helpful
- Tools that do helpful (but dangerous) things by default.
- Downing loadbalancers
- Diskerasing all the webservers.

## Runbooks/fixit weeks
- Information about the alert.
- Link to it from the alert.

## Fear
- No haunted graveyards.
- Make sure stuff breaks on your own term.
- "Blame is technical debt."
  - "Thank you for finding this edge case."

## Traps in production
- 

## Cookies for future-you
- Documents
- Comments
- Greppable search terms.
- Hi future self.
