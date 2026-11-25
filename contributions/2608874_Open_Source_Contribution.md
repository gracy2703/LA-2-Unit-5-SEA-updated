Open-Source Software Engineering: Documenting Issue and Return of Books in a Library Management System
1. Title and Student Details
Field	Details
Name	Harshitha Chintakayala
USN	2608874 (SAN)
Assigned Case Study	Question 4: Open-Source Software Engineering
Topic	Improving the documentation of an open-source Library Management System using the GitHub fork, commit and Pull Request workflow
2. Introduction
2.1 What is open-source software engineering?

Open-source software is software whose source code is public and released under a licence (for example MIT, Apache 2.0 or GPL) that lets anyone read, use, change and share it.

Open-source software engineering is the way such software is planned, built and maintained by a community instead of a single closed team. The community relies on:

Git, to record every change and who made it
GitHub, to host the code and coordinate the work
Issues, to report bugs and request improvements
Forks and Pull Requests, to propose changes without touching the original code
Reviews, where maintainers read and approve changes before they go live

Linux, Python, Git and Firefox are well-known examples.

2.2 Why contributing to open-source projects matters

For the contributor

Hands-on practice with Git, GitHub and working in a team
A public record of work that employers can see
Exposure to code review, coding standards and professional communication

For the project

More people checking the work means problems are found sooner
Clear documentation makes the project easier to adopt
Fresh contributors keep the project active and growing

A contribution does not have to be code. Documentation, bug reports, tests and translations are all valuable, and documentation is one of the easiest ways for a beginner to start.

3. Problem Analysis

A group of developers maintains an open-source Library Management System (LMS) on GitHub. A student using it notices that the project has no documentation explaining:

how a librarian or member issues a book, and
how a book is returned, including due dates and late fines.

Effects of this gap

Users cannot work confidently with the main features of the system.
Maintainers spend time answering the same basic questions again and again.
New contributors have to read the source code just to understand what the system does, which discourages them.

Root cause: features were developed, but user-facing documentation was never treated as part of the development work.

4. Proposed Solution

The student fixes the gap by contributing a documentation file through the standard open-source workflow. Write access to the original repository is not needed: the fork and Pull Request model lets any GitHub user propose changes safely.

Step 1: Open an Issue (recommended)

In the original repository, go to Issues → New issue. Use a title such as Docs: Add guide for issuing and returning books and describe what is missing. This tells the maintainers what you plan to do and avoids duplicate work.

Step 2: Fork the repository
Sign in to your own GitHub account.
Open the original repository page.
Click Fork at the top right.
Choose your account as the owner and keep the repository name unchanged.
Tick Copy the main branch only, then click Create fork.

You now have your own copy, marked "forked from <original owner>". Changes made here do not affect the original project.

Step 3: Create or modify the documentation file

In your fork:

Open the docs folder (or the root folder if there isn't one).
Click Add file → Create new file. To improve an existing file instead, open it and click the pencil icon.
Name the file docs/Issue_and_Return_Books.md.
Write the guide. Example content:
markdown
# Issuing and Returning Books

## Issuing a Book
1. Log in with a librarian account.
2. Open **Books → Issue Book**.
3. Enter the member ID and the book ID or ISBN.
4. The system verifies that:
   - at least one copy is available
   - the member is under the borrowing limit
   - the member has no unpaid fines
5. Click **Issue**. The due date is displayed and the available copies drop by one.

## Returning a Book
1. Open **Books → Return Book**.
2. Enter the book ID or scan its barcode.
3. The issue date and due date are displayed.
4. If the book is late, the fine is calculated automatically.
5. Click **Return**. The available copies increase by one and the transaction is
   saved in the member's history.

## Common Messages
| Message | Meaning | What to do |
|---------|---------|------------|
| Book not available | Every copy is already issued | Reserve the book |
| Limit exceeded | Member is at the borrowing limit | Return a book first |
| Pending fine | Member has an unpaid fine | Clear the fine at the desk |
Add a link to this guide in the main README.md so users can find it.

Documentation practices followed: clear headings, numbered steps, a table of common messages, plain language, and Markdown that displays well on GitHub.

Step 4: Commit the changes
Scroll down to Commit changes.
Write a meaningful message, for example: Added guide for issuing and returning books.
Select Commit directly to the main branch of your fork (creating a separate branch is the cleaner habit on real projects).
Click Commit changes.
Step 5: Submit a Pull Request
Return to the main page of your fork.
Click Contribute → Open pull request.
Verify the settings:
Setting	Expected value
Base repository	Original repository (maintainer's account)
Base branch	main
Head repository	Your fork
Compare branch	main
Add a clear title and a short description of what you added and why.
Click Create pull request.

If Contribute is not shown, use Pull requests → New pull request → compare across forks and select the same repositories and branches.

Step 6: Review and merge
Maintainers open the Pull Request and check Files changed.
If they ask for changes, you edit the file in your fork and the Pull Request updates itself.
Once approved, a maintainer clicks Merge pull request → Confirm merge.
The guide is now part of the original repository and you are listed as a contributor.
Same workflow using the command line
bash
# Copy your fork to your computer
git clone https://github.com/<your-username>/<repository>.git
cd <repository>

# Keep a link to the original project
git remote add upstream https://github.com/<maintainer>/<repository>.git

# Work on a separate branch
git checkout -b docs/issue-return-guide

# Add the file, then save the change
git add docs/Issue_and_Return_Books.md README.md
git commit -m "Added guide for issuing and returning books"

# Send the branch to your fork, then open the Pull Request on GitHub
git push origin docs/issue-return-guide
GitHub contribution workflow diagram
Changes requested
Approved
Student finds missingissue and returndocumentation
Open an Issue inthe original repository
Fork the repository toown GitHub account
Create or edit thedocumentation file
Commit with ameaningful message
Open a Pull Requestfork to original main
Maintainer review
Merge Pull Request
Documentation live inthe original project
5. Benefits and Challenges
5.1 Benefits of collaborative software development
Better quality: every change is reviewed before it is merged, so mistakes are caught early.
Faster progress: many people can work on features, bugs and documentation at the same time.
Shared knowledge: good documentation lets users and newcomers understand the system without reading the code.
Traceability: Git history, issues and Pull Requests show who changed what and why.
Safe experimentation: forks and branches allow trying ideas without risking the main project.
Learning and community: contributors gain real experience and projects gain long-term helpers.
5.2 Expected results for the Library Management System
Users can issue and return books correctly without asking for help.
Maintainers receive fewer basic "how do I...?" questions.
New contributors understand the core features faster and start contributing sooner.
5.3 Challenges and limitations
Challenge	How to handle it
The fork falls behind the original repository	Use Sync fork on GitHub, or fetch from upstream and merge
Merge conflicts when others edit the same file	Pull the latest changes before editing and resolve conflicts carefully
Pull Request is slow to be reviewed or is rejected	Discuss in an Issue first and follow the project's CONTRIBUTING.md
Documentation becomes outdated as features change	Update the docs in the same Pull Request that changes the feature
Newcomers are unfamiliar with project rules	Read the README, contribution guide and code of conduct before starting
6. Conclusion

The Library Management System had no documentation for its most important features, issuing and returning books. Using open-source engineering practices, a student can close this gap without any special access: fork the repository, write a clear guide with steps and a table of common messages, commit it with a meaningful message, and submit a Pull Request for the maintainers to review and merge.

This fork, commit and Pull Request workflow is the foundation of open-source collaboration. It protects the original project, makes sure every change is reviewed, and lets anyone, including students, improve real software. Even a documentation-only contribution makes a project easier to use, easier to maintain and more welcoming to new contributors.
