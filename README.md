# 📚 ABL Library Master Database

## What Is It?
A relational database built in Microsoft Access that manages a library's day-to-day operations — tracking the book catalog, registered members, active borrowing transactions, and returns (including overdue days and fines).

## Technologies Involved
- **Microsoft Access (.accdb)** — the database engine, tables, forms, and queries all live here
- **Access Forms & Queries** — used for entering and viewing borrower/book records (`frmBorrowers`, `frmBookAuthor`, backed by `qryBorrowers`)
- **Excel (.xlsx)** — used as an external source for member data (`ABL_Member.xlsx`)
- **Delimited text (.txt)** — used as an external source for return records (`ABL_Return.txt`)

## Features
- **`tblBooks`** — the book catalog: title, author, genre, publisher, and availability status
- **`tblMembers`** — registered members and their standing (Admin, Active, or Block)
- **`tblBorrowers`** — every borrowing transaction, linking a member to a book with a borrow date, expected return date, and status (Borrowed, Returned, or Overdue)
- **`tblReturns`** — each completed return, tracking the expected return date, actual return date, days late, and any fine charged
- Forms for entering and browsing borrower and book/author records
- Support for importing member and return data from external Excel and text files, instead of entering everything by hand
- A backup copy of the full database included alongside the working file

## Process
The database is organized around four connected tables — books, members, borrowers, and returns — so that a single borrowing transaction can be traced end-to-end: which member borrowed which book, when it was due back, and whether it came back late with a fine attached. Forms sit on top of the tables to make entering and reviewing records easier than editing the raw tables directly, and queries pull combined views across tables (for example, matching borrowing records to the members who made them). Member and return data can also be brought in from outside sources (Excel and a tab-delimited text file) using Access's import tools, rather than requiring every record to be typed in manually.

## What I Learned
- How to design a relational database with multiple connected tables instead of one flat spreadsheet
- How to build Access forms and queries for data entry and lookups
- How to import external data (Excel spreadsheets, delimited text files) into an Access database
- How to calculate and store derived values, like late days and fine amounts, based on other fields in the database

## How It Can Be Improved
- Add a report that lists all currently overdue books and total fines owed per member
- Add a dedicated Return form so staff can log a return directly, instead of only importing return data from a file
- Add a dashboard view summarizing how many books are available, borrowed, or overdue at a glance
- Add fine payment tracking, separate from the fine calculation itself
- Automate the LateDay/Fine calculation with a formula tied to the due date, instead of entering it manually

## Running the Project
1. Install **Microsoft Access** (part of Microsoft 365 or Office).
2. Open `ABL_Library_Master_Database.accdb`.
3. Browse the tables directly, or use the Borrowers/Book-Author forms for data entry.
4. To bring in new member or return data, use **External Data → Import** and select the corresponding Excel or text file.
