# Booking workshop

Professional Software Practices, Topic 1: version control.

A deliberately small command-line Python application for practising tested changes, commits, remotes, tags and safe recovery. No third-party packages are needed. Uses Python 3 and its built-in unittest framework.

## Choose the right starting point

- `main`: learner starting point. Rejects zero and negative attendees, but has no upper limit. Practical 1 adds a limit of 10.
- `demo-start`: tutor starting point. Deliberately accepts zero attendees, and the supplied tests omit that boundary.

The lower-bound correction is already in main so learners can start independently of the live demo. The upper-bound solution is intentionally absent.

## Run and test

Open a terminal in the project root. On macOS/Linux:

```bash
python3 booking.py 5
python3 -m unittest discover -s tests -v
```

On Windows use `py` instead of `python3`. If your environment uses `python`, use that consistently. Tests are not run automatically by Git.

Read `docs/learner-activity.md` for the exercises and `docs/evidence-log.md` for the evidence template. `docs/tutor-guide.md` contains the demonstration walkthrough.

## Git identity

In your own clone, set the identity approved for your course:

```bash
git config user.name "Your name"
git config user.email "Your course email"
```

Replace the example values. These settings identify commits and do not authenticate remote access. The initial commits use a clearly labelled workshop author identity.

## Repository access

Your tutor supplies a writable repository URL. Clone that URL rather than downloading a source-code ZIP, so you retain history and the remote connection. Each learner should have their own writable repository. Read permission does not imply push permission.
