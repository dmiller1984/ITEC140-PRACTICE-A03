# Wage Calculator — independent practice

**PRACTICE ONLY — NOT RICHARD’S A03 README — NOT FOR SUBMISSION**

This is a separate, ungraded practice exercise for Medicine Hat College ITEC 140, Richard Hobson. It is not an official assignment or an instructor-approved template. It contains a blank C# .NET 10 Windows Forms starter with `Form1`. You build the GUI, create the events, and write every wage-calculation statement yourself. No completed Calculate, Clear, or Exit handlers are supplied.

## Confirmed course facts and what remains unknown

Research date: **September 30, 2026, America/Edmonton**.

| Item | Evidence/status |
| --- | --- |
| Real assignment title | **A03 — Wage Calculator**, confirmed in Richard’s live Blackboard Course Schedule. |
| Scheduled issue date | **Monday, October 5, 2026**, confirmed in the live schedule. |
| Scheduled due date | **Tuesday, October 13, 2026**, confirmed in the live schedule. An exact submission time was not established for A03. |
| Module at issue | **Module 4: Decisions and Logic**, confirmed in the live schedule. |
| Nearby reading | Week 5 lists **Chapter 4, Making Decisions**; Week 6 has no new reading. Live Module 3 Class Preparation says to read Chapter 4 **before Thursday, October 1** and that Module 4 covers it next. |
| Real A03 README | **Not found in the accessible sources checked.** This does not prove that Richard has not prepared it privately. |
| Real A03 controls, fields, formulas, tests, marks, rubric, validation, hand-in and AI rules | **Unverified.** None of the practice choices below establishes a real A03 requirement. |

The accessible course content, announcements, course repository listing, and saved notes were checked. The source log below explains the scope. When the real A03 is released, read its complete README and Blackboard instructions afresh. Do not rename this practice repository into a submission or copy a finished practice file into graded work.

## AI and ownership of your work

The student reports that Richard directly clarified that AI may act as a tutor/teaching tool, provided it does not complete graded work. That clarification was supplied by the student; it was not independently retrieved as a written A03 rule.

The existing Circle and A02 READMEs contain written prohibitions on AI use for those assessments. Their rules must not be silently treated as permission for A03. This independently created practice exercise uses those projects only to understand the skill level. Follow Richard’s actual instructions for every graded assessment and quiz.

Use tutoring to explain concepts, ask you questions, or help you diagnose your own attempt. Type your own code and be able to explain each statement. No generated wage solution is included here. There is **no Blackboard submission, grade, official deadline, or official rubric** for this practice repository.

## Get the blank project into Visual Studio

Use **Visual Studio Community 2026 on Windows**, the **.NET desktop development** workload, and the **.NET 10 SDK**. This targets modern .NET, not the older Windows Forms App (.NET Framework) template.

1. Open this repository on GitHub: <https://github.com/dmiller1984/ITEC140-PRACTICE-A03>.
2. Click the green **Code** button.
3. Select **HTTPS** and copy the URL: `https://github.com/dmiller1984/ITEC140-PRACTICE-A03.git`.
4. Open Visual Studio.
5. On the start screen, choose **Clone a repository**. If a project is already open, use **File → Clone Repository**.
6. Paste the HTTPS URL. Choose a new local folder clearly named `ITEC140-PRACTICE-A03`, separate from every graded repository. Click **Clone**.
7. Open **ITEC140-PRACTICE-A03.sln**. If you only see folder view, double-click that solution file in Solution Explorer.
8. In Solution Explorer, right-click **Form1.cs → View Designer**. Build the GUI yourself using the control table below.
9. Create each button’s Click event in the Designer and write the code yourself in **Form1.cs**.
10. Build, run, and test repeatedly using the manual test table. Commit and push your practice progress so it is available on your other computer.

Before editing, **Build → Build Solution**, then **Start** or **F5** should display an empty form titled `PRACTICE ONLY - Wage Calculator`. Empty is intentional. Buttons and calculation results do not exist until you add them.

If .NET 10 is missing, use Visual Studio Installer to add the .NET desktop development workload and .NET 10 SDK. If Visual Studio opens the code instead of the form, choose View Designer. Set `WageCalculatorPractice` as the startup project if necessary.

### What the starter files do

| File | Job |
| --- | --- |
| `ITEC140-PRACTICE-A03.sln` | Opens the single practice project in Visual Studio. |
| `WageCalculatorPractice/WageCalculatorPractice.csproj` | Selects C#, Windows Forms, and `net10.0-windows`. |
| `WageCalculatorPractice/Program.cs` | Standard startup plumbing: opens Form1. It does not calculate wages. |
| `WageCalculatorPractice/Form1.cs` | Your work area. Initially contains only the constructor that initializes the form and guidance comments. |
| `WageCalculatorPractice/Form1.Designer.cs` | Blank form settings managed by the Designer. It has no wage controls or Click subscriptions. |
| `.gitignore` | Keeps build output and local Visual Studio settings out of Git. |
| `.gitattributes` | Keeps text line endings consistent. |

## Practice assumptions — every item here is invented for practice

**All rules, names, formulas, messages, and test expectations in the remainder of this exercise are PRACTICE ASSUMPTIONS, not verified A03 instructions.**

| Practice choice | Assumption used in this exercise |
| --- | --- |
| Inputs | Total hours worked in one week and one hourly rate. Fractional hours and rates are allowed. |
| Regular-hours limit | Up to and including **40 hours** are paid at the hourly rate. |
| Overtime | Only hours above 40 receive **1.5 times** the hourly rate. Exactly 40 has no overtime. |
| Output | Regular pay, overtime pay, and gross pay, displayed as currency with two decimal places (`C2`). Use Canadian dollar display settings for the supplied `$` examples. |
| Meaning of overtime pay | The full pay for overtime hours at 1.5 times the rate, not just the extra half-rate premium. |
| Gross pay | Regular pay plus overtime pay, before deductions. No tax, benefits, holiday pay, or payroll-law calculations. |
| Input validation | Hours must be a number at least zero; hourly rate must be a number greater than zero. Reject blanks, letters, and negatives. |
| Numeric storage | Use five `decimal` fields for the two inputs and three outputs; practise named constants for 40 and 1.5. This choice is not inferred from the Circle requirement to use `double`. |
| Decision | Use `if / else` to choose the regular-only or overtime calculation. |
| Repeated clicks | Recalculate the current inputs from scratch; do not accumulate previous wages. |
| Clear | Blank both inputs, reset all five fields to zero, restore all pay displays to zero currency, clear the error, and focus the hours input. |
| Exit | Close the form using code you write. |
| Error behavior | Show a specific message in `lblError`, reset the output fields/displays to zero to prevent stale results, and focus the input needing correction. Clear the message after a successful calculation. |
| GUI and naming | Use the practice control table below. Its exact names are for this exercise only. |

These simplified pay rules are a learning model, not a statement of Alberta employment law or an actual payroll system.

## Part 1 — build the GUI yourself

Add all controls in the Designer **before** writing handlers. Set the **(Name)** property, not just the visible Text. Name and Text perform different jobs: Name is how code refers to the control; Text is what the user sees.

| Control (Name) | Type | Initial Text | Job |
| --- | --- | --- | --- |
| `txtHoursWorked` | TextBox | blank | Input: weekly hours, such as 35 or 40.5. |
| `txtHourlyRate` | TextBox | blank | Input: hourly rate, such as 20 or 18.75. Enter numbers without a dollar sign. |
| `btnCalculate` | Button | Calculate | Starts validation, decision, calculation, and display. |
| `btnClear` | Button | Clear | Restores the initial state. |
| `btnExit` | Button | Exit | Closes this practice form. |
| `lblRegularPay` | Label | `$0.00` | Displays regular pay; the user does not type here. |
| `lblOvertimePay` | Label | `$0.00` | Displays overtime pay; the user does not type here. |
| `lblGrossPay` | Label | `$0.00` | Displays gross pay; the user does not type here. |
| `lblError` | Label | blank | Displays helpful validation feedback. Make it wide enough for a sentence. |

Also add five caption Labels for **Hours worked**, **Hourly rate**, **Regular pay**, **Overtime pay**, and **Gross pay**. Their names are your choice. That makes **14 controls** in this practice design: nine named controls and five captions. No ListBox is needed; this is a single wage calculation rather than a receipt.

Keep the inputs together, the three results together, and the buttons together. Use consistent spacing and readable text. Consider a red ForeColor for `lblError`. Set TabIndex so keyboard focus goes hours → rate → Calculate → Clear → Exit. Output/caption labels should not be input stops. The form title is already set.

Run the form once with only the GUI built. It will not calculate yet. Save, commit, and push with a message such as **Build practice wage calculator GUI**.

## Part 2 — choose and declare your storage

In `Form1.cs`, create the following **practice-assumption** fields inside the Form1 class and outside its constructor or any event handler. Use `decimal` for all five:

| Field name | Job |
| --- | --- |
| `decHoursWorked` | Stores converted hours. |
| `decHourlyRate` | Stores converted hourly rate. |
| `decRegularPay` | Stores the regular part of the pay. |
| `decOvertimePay` | Stores the overtime part of the pay. |
| `decGrossPay` | Stores the sum of both parts. |

Practise two named `decimal` constants: `RegularHoursLimit` for 40 and `OvertimeMultiplier` for 1.5. A constant explains a fixed practice rule. A field holds a value that changes as the form is used. Remember the decimal-literal suffix from Chapter 3 when you write these yourself.

Explain why Clear can access fields shared with Calculate. Avoid declaring a second local variable with a field’s name: that can hide the field and leave confusing old values behind.

## Part 3 — create Click events, then solve one job at a time

Double-click each correctly named button in the Designer once. Visual Studio creates a Click handler in Form1.cs and connects the event. Do not double-click the form background by mistake. Do not manually paste calculation code into the Designer file.

### Calculate: the job of each step

1. **Read the text.** Get the two TextBox inputs. Their Text values are strings, even when the user types digits.
2. **Convert safely.** Turn the strings into decimal values. Chapter 3’s Parse with exception handling can practise the earlier skill; Chapter 4’s TryParse with an `if / else` can practise checking conversion success. Choose one approach you understand. Do not use a failed conversion result for wages.
3. **Check the range.** A successfully converted number can still be unacceptable. Reject negative hours and rates that are zero or negative. Zero hours is allowed in this practice exercise.
4. **Handle an invalid attempt.** Explain which input needs correcting in `lblError`; clear old pay values and focus the relevant TextBox. Stop the calculation path for that attempt. Suggested practice messages are “Enter valid hours of zero or more.” and “Enter a valid hourly rate greater than zero.” These messages are not official A03 text.
5. **Ask the decision question.** Are the hours at or below the practice limit? This picks one of two branches. Exactly 40 belongs to regular-only pay.
6. **Calculate regular and overtime pay for the selected branch.** Translate the arithmetic table below into your own statements. In the regular-only branch, explicitly make overtime pay zero so a previous overtime result cannot remain.
7. **Combine the pay.** Gross pay is the sum of the regular and overtime amounts from this attempt.
8. **Display the result.** Convert each numeric pay value to currency text with two decimal places. Formatting changes the display, not the stored calculation. Clear any previous error after success.
9. **Repeat.** Change the inputs and click Calculate again. Results should be replaced, not added to the previous calculation.

### Arithmetic specification — practice assumptions, not C# solution code

Let **H** be total hours and **R** be the hourly rate. The overtime rate is **1.5 × R**.

| Condition | Regular pay | Overtime pay | Gross pay |
| --- | --- | --- | --- |
| H is at most 40 | H × R | 0 | Regular pay + overtime pay |
| H is greater than 40 | 40 × R | (H − 40) × R × 1.5 | Regular pay + overtime pay |

For 45 hours at $20/hour, regular hours are 40 and overtime hours are 5. The first 40 are paid once at $20; the remaining 5 are paid once at $30. Do not pay all 45 at the overtime rate or count those 5 hours twice.

### Clear: the job of each step

1. Remove both input strings so a new example can be entered.
2. Reset all five numeric fields so earlier values do not survive.
3. Restore the three output labels to zero currency with two decimal places.
4. Empty the error label.
5. Put keyboard focus back in `txtHoursWorked`.

### Exit: the job

Close the form when `btnExit` is clicked. Use the form-closing skill from Chapter 2.9 and type it yourself.

## Part 4 — manual tests you run yourself

These expected results apply **only to the invented 40-hour / 1.5-times practice model**. They are not Richard’s tests. Dollar displays assume Canadian/compatible currency settings. All shown values avoid ambiguous half-cent rounding; no separate payroll rounding rule is specified for this practice.

| Hours | Rate | Expected regular pay | Expected overtime pay | Expected gross pay | What this tests |
| --- | --- | --- | --- | --- | --- |
| 35 | 20 | $700.00 | $0.00 | $700.00 | Below the threshold. |
| 40 | 20 | $800.00 | $0.00 | $800.00 | Exactly the threshold. |
| 45 | 20 | $800.00 | $150.00 | $950.00 | Five overtime hours. |
| 39.5 | 20 | $790.00 | $0.00 | $790.00 | Fractional regular hours. |
| 40.5 | 20 | $800.00 | $15.00 | $815.00 | Fractional overtime hours. |
| 35 | 18.75 | $656.25 | $0.00 | $656.25 | Decimal rate and currency display. |
| 0 | 20 | $0.00 | $0.00 | $0.00 | Valid zero hours. |
| blank | 20 | $0.00 | $0.00 | $0.00 | Reject missing hours and show an error. |
| abc | 20 | $0.00 | $0.00 | $0.00 | Reject nonnumeric hours without crashing. |
| -1 | 20 | $0.00 | $0.00 | $0.00 | Reject negative hours. |
| 35 | blank or abc | $0.00 | $0.00 | $0.00 | Reject missing/nonnumeric rate. |
| 35 | 0 or -20 | $0.00 | $0.00 | $0.00 | Reject a rate that is not positive. |

Run these sequence tests too:

- Calculate **45 at 20**, then **35 at 20** without Clear. Overtime must become $0.00 and gross $700.00.
- Calculate **45 at 20** twice. Gross must stay $950.00.
- Calculate a valid case, then try invalid input. Old valid pay must reset to zero and an error must appear.
- After an error, correct the input and calculate. The correct pay must appear and the error must disappear.
- Click Clear after a valid case and after an invalid case. Inputs/error must be blank, pay fields/displays zero, and hours focused.
- Click Exit. The practice form must close.

If a result is wrong, use a breakpoint in your own Calculate handler and inspect the fields. Check the input values, selected branch, regular amount, overtime amount, and gross in order. Fix the first value that becomes wrong.

## Self-check — no marks attached

- [ ] The GUI uses the practice names exactly, including capital letters.
- [ ] I can explain TextBox strings, decimal conversion, fields, and constants.
- [ ] I can explain which branch executes for 35, 40, and 45 hours.
- [ ] Bad input does not crash or leave old wages on screen.
- [ ] Repeated Calculate clicks replace results.
- [ ] Currency formatting shows two decimal places.
- [ ] Clear resets controls and fields; Exit closes the form.
- [ ] I ran every numeric test and sequence test.
- [ ] I wrote my own handlers and can explain every statement.
- [ ] My practice work is committed and pushed only to this repository.
- [ ] Nothing from this repository has been submitted to Blackboard.

## Study links to the earlier skills

Circle practice establishes input → numeric field → calculation → formatted output → bad-input handling. Its four double fields and N2 display belong to that Circle exercise. A02 establishes field-scoped decimal values, named controls, button Click events, currency output, and repeated interactions. This wage exercise combines those patterns with an if/else decision; it does not need Math.PI, a receipt ListBox, loops, files, a database, or a completed solution from either earlier project.

Useful sections in the saved Starting Out with Visual C#, 6th edition reading map:

| Job | Section and starting page |
| --- | --- |
| Read TextBox input | 3.1, p. 115 |
| Choose numeric types and calculate | 3.3–3.4, pp. 129, 134 |
| Convert and format | 3.5–3.6, pp. 140, 147 |
| Handle conversion exceptions | 3.7, p. 154 |
| Constants and fields | 3.8–3.9, pp. 163, 164 |
| Debug wrong results | 3.12, p. 183 |
| if and if/else | 4.1–4.2, pp. 199, 208 |
| TryParse and input validation | 4.7–4.8, pp. 235, 242 |

These page references come from the saved textbook contents map, not a newly published A03 reading list.

## Source log and research limits

Sources are read-only references. Private course files and graded source code have not been copied into this public starter.

| Source checked September 30, 2026 | Finding |
| --- | --- |
| Live Blackboard ITEC 140 lecture Course Schedule | Confirms A03 title, Oct 5 issue, Oct 13 due, Module 4, and nearby Chapter 4 reading. |
| Live lecture Course Content and Assignments & Exams folder | Visible modules run through Module 3; released assignments run through A02. No visible A03 item. |
| Live lecture Announcements | One announcement, about A02’s Sept 29 due date; no A03 announcement. |
| Live lecture Discussions | No discussion threads shown. |
| Live lecture Gradebook | No A03 item on its single visible page. |
| Live ITEC 140 lab content and announcements | No content posted and zero announcements. |
| Live Module 3 Class Preparation | Confirms text input, Parse, ToString, arithmetic, fields, constants, exception handling, debugging, and Chapter 4 before Oct 1. |
| Live “Your GitHub Repos” course document and its course-topic GitHub search | Four accessible classroom repositories: A00, A01, A02, Circle practice. No A03 repository appeared. |
| Live Circle practice README | Confirms exact control/field naming, numeric input, four double fields, circle arithmetic, N2 output, invalid-input feedback, and its written expectations. Used only to calibrate practice level. |
| Live A02 README | Confirms decimal fields, controls built before code, button events, receipt records, currency totals, 5% tax, and its written expectations. Used only to calibrate practice level. |
| Saved ITEC 140 checkpoint, MHC School Master Record, chapter map and study guide | Support the schedule and Chapter 3/4 skill progression. No exact A03 README was located. Historical notes are not treated as proof of current release status. |
| Connected Google Drive searches for ITEC and Wage | No relevant A03 source returned. |
| Public web search for MedicineHatCollege ITEC 140 wages | No matching authoritative A03 result returned. |

“Not found” means not found among the sources accessible in this review. Unreleased, unshared, instructor-only, or unindexed repositories are outside that evidence. This README will not automatically change when A03 is released.

Starter settings follow Microsoft’s documented modern Windows Forms project/startup pattern: [Windows Forms application configuration](https://learn.microsoft.com/en-us/dotnet/desktop/winforms/wfdev-diagnostics/wfac010) and [a .NET 10 Windows Forms project example](https://learn.microsoft.com/en-us/dotnet/desktop/winforms/advanced/how-to-use-host-builder). This starter does not use the host-builder example’s extra packages.
