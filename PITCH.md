# PITCH.md

Six lines and a lever. Your words. The last two are scored.

Built: A disruption-care chat agent for Larkspur Airlines on the Claude Messages API, using Larkspur's nine tools plus five of our own that we wrote and connected locally: seats_left, ground_stop_status, hold_time_left, what_automation_will_not_do and next_available_day.
Does: For a customer whose flight is cancelled or delayed, it finds the booking, checks the flight status, looks up what Larkspur owes under policy, searches alternative flights, checks they have free seats for the whole party, and holds one for 15 minutes. It also hands groups, minors and refunds to a human.
Number: 17,214 tokens in per contact (mean of 15 runs across the five tickets, baseline saved as "before"). TODO: run `python3 bench.py --label after` once the lever has moved and replace this with "17,214 to <after> tokens in per contact".
Safety check: The agent holds a seat but never books it. confirm_rebooking needs a confirmation_token that only the customer's own Confirm click produces, and "yes" in chat does not count. TODO: confirm by naming the PNR and turn in your own `--trace` where the agent stopped at the hold.
Next: Let the agent warn the customer when a hold is about to expire and offer a new one, using hold_time_left, instead of only answering when asked.
Still broken: Dates are not checked against today. The K7PQ2M booking is for 8 May 2025 and the agent flagged it, but it spent turns on a stale booking instead of stopping early. TODO: replace with a failure you saw yourself if you have a sharper one.
Lever: <cost | speed | intelligence>

## Priya asked

Costs:
Wrong:
Runs it:
Left out:
