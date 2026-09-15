# Tutor guide

## Preparation

Prepare an independent demo clone and an individual writable repository for each learner. Learners start on main. For a fresh tutor demonstration, create a new branch from demo-start:

```bash
git switch -c tutor-demo demo-start
```

If you cloned from a host and only have a remote-tracking demo branch, use `git switch -c tutor-demo origin/demo-start`. Use a fresh branch name for each run. Do not reset learners' work.

The app uses unittest rather than pytest to avoid installations. Use `python3 -m unittest discover -s tests -v` throughout (Windows: `py`). These commands supersede illustrative pytest commands in the e-learning.

## Demonstration (15 minutes)

### Baseline (3 minutes)

Run the five baseline tests. All should pass. Run `python3 booking.py 0`: the application incorrectly confirms the booking. Ask what the passing suite has missed.

### Regression and correction (4 minutes)

Add this method inside BookingTests in tests/test_booking.py:

```python
    def test_zero_attendees_are_rejected(self):
        with self.assertRaises(ValueError):
            validate_attendees(0)
```

Run tests: exactly this test should fail because ValueError is not raised. Change `if attendees < 0:` to `if attendees < 1:` in booking.py. Run tests again: all six pass. CLI input 0 now exits with status 1 and a rejection message.

### Review and recording (4 minutes)

Show git status and git diff. Stage booking.py and tests/test_booking.py, then inspect git diff --staged. Commit with `Reject bookings with zero attendees`.

### Sharing (4 minutes)

Push the new demo branch with `git push -u origin tutor-demo`, using its actual name. Show it remotely. This does not alter learner main. If working entirely offline, use a prepared local bare remote and explain it simulates a shared server.

## Learner starting point

main already includes the zero correction and six passing tests. Learners implement the upper limit independently. Supply method scaffolds if necessary, but ask them to choose assertions and explain boundaries. Expected final behaviour is reject 0/11 and accept 1/10. Their tests should check both boundaries. Keep the solution out of learner commits until they have attempted it.

## Recovery

Use the learner guide. The confirmation test checks the count rather than exact wording, allowing the disposable wording change to pass tests. Explicitly demonstrate a manual check for wording and discuss this test limitation. After reverting, rerun validation tests too.

## Hosting

The outer START-HERE.md explains how to upload the bundled branches and allocate repositories. No remote account or URL is embedded in this package. Source files and instructions can be edited for the cohort before publishing.
