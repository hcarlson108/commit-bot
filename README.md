# commit-bot


GET STARTED - 5 STEPS
--------------------------------------

1. Create your new commit-bot repository

2. CD into your commit-bot repo and paste this one line: mkdir -p .github/workflows 

3. This creates two nested folders. Nothing visible happens — that's normal.


4. Next type: nano .github/workflows/daily-commit.yml This opens a blank file in a simple text editor inside your terminal.

5. Within the blank file, paste the following into the blank file:

name: Daily Commit
on:
  schedule:
    - cron: '0 12 * * *'
  workflow_dispatch:
permissions:
  contents: write
jobs:
  commit:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: |
          date >> streak-log.txt
          git config user.name "github-actions"
          git config user.email "actions@github.com"
          git add streak-log.txt
          git commit -m "Daily commit" || exit 0
          git push



Add to Git
----------------------------------
git add .
git commit -m "add daily auto commit"
git push



CONFIRM IT'S WORKING
----------------------------------
On GitHub, open your auto-commit repo in a browser, click the 'Actions' tab. You'll see 'Daily Commit' listed. 
Click 'Run workflow' to test it immediately instead of waiting until tomorrow. A green checkmark means it worked.
