# Learner activities

## Preparation

Clone your allocated writable repository, enter its folder and confirm `git status` reports branch main and a clean working tree. Run the application and tests using the README commands. If tests already fail, ask for help before editing.

## Practical 1: booking limits (20 minutes)

Requirement: a booking must contain between 1 and 10 attendees, inclusive. Retain the existing integer-input check.

1. Run the baseline tests.
2. In `tests/test_booking.py`, add checks for 10 (accepted) and 11 (rejected). Retain the checks for 0 and 1. Use the existing test methods as a scaffold.
3. Run tests before correcting the implementation. Identify which new test exposes the missing upper limit.
4. Change `validate_attendees` in `booking.py`. Use an error message that describes the permitted range.
5. Rerun the full test suite and check the CLI with 0, 1, 10 and 11.
6. Inspect `git diff`. Stage only `booking.py` and `tests/test_booking.py`:

```bash
git add booking.py tests/test_booking.py
git diff --staged
git commit -m "Limit bookings to ten attendees"
git push
```

Use the actual agreed branch workflow. Do not force push to overcome an error. Confirm your commit on the repository host.

Pair discussion: explain your requirement, test choices and commit. What behaviour remains untested?

## Practical 2: mark and recover (20 minutes)

Start with a tested, committed Practical 1 result and a clean working tree. Tag it:

```bash
git tag -a topic1-working -m "Tested booking limits"
git push origin topic1-working
```

Use a different agreed tag name if that name already exists. Shared tags should remain stable.

1. Change only the CONFIRMATION string in `booking.py`, replacing `Booking confirmed` with `Reservation accepted`. Keep `{attendees}` intact.
2. Run tests and manually check the wording with `python3 booking.py 5`.
3. Inspect the diff, stage booking.py and commit with `Change confirmation wording` as the message. Push this disposable change.
4. Run `git log --oneline`. Record the wording commit ID. Inspect it with `git show COMMIT_ID` (replace COMMIT_ID with the actual ID).
5. With a clean tree, reverse that specific commit:

```bash
git revert --no-commit COMMIT_ID
git diff --staged
```

6. Rerun tests. Check the original wording returns and that 0 and 11 fail while 1 and 10 succeed.
7. Record and share the reversal:

```bash
git commit -m "Revert confirmation wording change"
git push
```

If a revert conflicts, stop and ask your tutor. `git revert --abort` cancels a revert still in progress; it does not undo an already completed recovery commit.

Explain why the original wording commit remains in the history. Record evidence in `docs/evidence-log.md`. If you commit your completed log, keep it separate from the component change.

## Extension

Run `git fetch origin` and inspect `git status` and `git log --oneline --graph --decorate --all`. Explain local and remote-tracking references. Fetching does not integrate changes into your working branch.
