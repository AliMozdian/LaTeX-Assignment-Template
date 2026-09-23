# LaTeX Assignment Template

A clean, reusable **Persian LaTeX homework/assignment template** for
teaching assistants and instructors who want to release assignments in a
polished, consistent format without having to build the page design from
scratch.

The template is designed around:

-   Persian text and right-to-left typesetting
-   XeLaTeX + `xepersian`
-   A polished assignment cover page
-   IUST branding by default
-   Decorative page frames and information cards
-   A separate `questions.tex` file for assignment-specific questions
-   A single, clearly marked configuration section in `main.tex`

The goal is simple: **change the assignment information, write the
questions, compile, and you're done.**

------------------------------------------------------------------------

## Preview

The first page contains:

-   University logo
-   Course name
-   Assignment title
-   Semester
-   Release and deadline dates
-   Professors/instructors
-   Assignment designers/TAs
-   Required slides or course material
-   Submission and grading policies
-   A decorative page frame

The visual design is already handled by the template, so you can focus
on the actual assignment.

------------------------------------------------------------------------

## Repository structure

A typical copy of the template should look like this:

``` text
LaTeX-Assignment-Template/
│
├── main.tex
├── questions.tex
│
├── iust-logo.png
├── vazirmatn-regular.ttf
├── vazirmatn-bold.ttf
│
└── README.md
```

### What each file does

  File                      Purpose
  ------------------------- -------------------------------------------------------
  `main.tex`                Main template, cover page, styling, and configuration
  `questions.tex`           Assignment-specific questions
  `iust-logo.png`           Logo used on the cover page
  `vazirmatn-regular.ttf`   Regular Persian font
  `vazirmatn-bold.ttf`      Bold Persian font
  `README.md`               This guide

You normally only need to edit **`main.tex`'s configuration section**
and **`questions.tex`**.

------------------------------------------------------------------------

# Quick Start

If you already have a working LaTeX/XeLaTeX installation:

1.  Clone or download this repository.

2.  Keep all the files in the same folder.

3.  Open `main.tex`.

4.  Find the section called:

    ``` text
    ASSIGNMENT CONFIGURATION
    ```

5.  Change the course, assignment, dates, staff, and policies.

6.  Open `questions.tex` and write your questions.

7.  Compile `main.tex` using **XeLaTeX**.

8.  Your assignment PDF is ready.

------------------------------------------------------------------------

# 1. Configure the assignment

The most important design choice in this template is that all the
information that normally changes from one assignment to another is
collected near the top of `main.tex`.

You should see something similar to:

``` latex
% ================================================================
%                    ASSIGNMENT CONFIGURATION
% ================================================================
```

### Course and assignment information

``` latex
\newcommand{\courseName}{نظریهٔ زبان‌ها و ماشین‌ها}
\newcommand{\assignmentTitle}{تمرین سری دوم}
\newcommand{\term}{بهار ۱۴۰۵}
\newcommand{\assignmentCode}{Hw2}
```

Change these values for your assignment.

For example:

``` latex
\newcommand{\courseName}{ساختمان داده‌ها}
\newcommand{\assignmentTitle}{تمرین سری سوم}
\newcommand{\term}{پاییز ۱۴۰۵}
\newcommand{\assignmentCode}{Hw3}
```

`assignmentCode` is also used when generating the suggested answer-file
name.

------------------------------------------------------------------------

## 2. Set the dates

Change:

``` latex
\newcommand{\releaseDate}{۱۴۰۵/۰۱/۱۰}
\newcommand{\dueDate}{۱۴۰۵/۰۱/۲۴}
```

For example:

``` latex
\newcommand{\releaseDate}{۱۴۰۵/۰۷/۰۱}
\newcommand{\dueDate}{۱۴۰۵/۰۷/۱۵}
```

The template does not calculate dates automatically; you simply enter
the dates you want displayed.

------------------------------------------------------------------------

# 3. Add the teaching staff

Change:

``` latex
\newcommand{\professors}{دکتر انتظاری ملکی و دکتر غیور باغبانی}
\newcommand{\designers}{علی مزدیان فرد}
```

For example:

``` latex
\newcommand{\professors}{دکتر علی احمدی و دکتر مریم رضایی}
\newcommand{\designers}{علی محمدی و سارا کریمی}
```

You can put one person, several people, or any text you want inside
these commands.

------------------------------------------------------------------------

# 4. Set the required slides/material

The template provides a field for required course material:

``` latex
\newcommand{\requiredSlides}{
    \lr{chp3\_1 \quad\textbullet\quad chp3\_2}
}
```

For English or Latin-heavy text, `\lr{...}` is useful because it tells
XePersian to typeset that part from left to right.

For example:

``` latex
\newcommand{\requiredSlides}{
    \lr{Chapter 3 \quad\textbullet\quad Chapter 4}
}
```

If you do not need this field, you can leave it empty:

``` latex
\newcommand{\requiredSlides}{}
```

------------------------------------------------------------------------

# 5. Configure submission

The template lets you specify:

``` latex
\newcommand{\totalScore}{۱۰۰}
\newcommand{\answerFileName}{\assignmentCode\_StudentID\_StudentName.pdf}
\newcommand{\submissionPlatformName}{کوئرا}
\newcommand{\submissionPlatformURL}{https://quera.org/course/assignments/99805/problems}
```

For example, if your course uses a different platform:

``` latex
\newcommand{\submissionPlatformName}{سامانه آموزشی}
\newcommand{\submissionPlatformURL}{https://example.com/submit}
```

You can also change the required filename format:

``` latex
\newcommand{\answerFileName}{HW3\_StudentID\_StudentName.pdf}
```

------------------------------------------------------------------------

# 6. Configure the assignment policies

One of the useful parts of the template is that the policy text is also
separated from the design.

The template currently provides policies for:

-   Assumptions
-   Collaboration / copying
-   AI usage
-   Late submission

Each policy has a switch.

For example:

``` latex
\newcommand{\useAIPolicy}{1}
```

means the AI policy is shown.

Change it to:

``` latex
\newcommand{\useAIPolicy}{0}
```

and that policy will not appear on the cover page.

The same mechanism exists for the other policies:

``` latex
\newcommand{\useAssumptionPolicy}{1}
\newcommand{\useCollaborationPolicy}{1}
\newcommand{\useAIPolicy}{1}
\newcommand{\useLatePolicy}{1}
```

Use `1` for **show** and `0` for **hide**.

------------------------------------------------------------------------

## Editing a policy

The actual text is stored in commands such as:

``` latex
\newcommand{\aiPolicy}{%
اگر از هوش مصنوعی استفاده می‌کنید، ...
}
```

Simply replace the Persian text with the policy used by your course.

For example:

``` latex
\newcommand{\aiPolicy}{%
استفاده از ابزارهای هوش مصنوعی در این تمرین مجاز است، اما دانشجو مسئول صحت پاسخ نهایی است.
}
```

This means you can reuse the same template for courses with completely
different rules without touching the visual design.

------------------------------------------------------------------------

## Late submission

If your course allows late submission, configure:

``` latex
\newcommand{\useLatePolicy}{1}
\newcommand{\lateDaysPerAssignment}{۵}
\newcommand{\lateDaysTotal}{۱۵}
```

If there is no late-submission policy:

``` latex
\newcommand{\useLatePolicy}{0}
```

The late-policy card will then disappear automatically.

------------------------------------------------------------------------

# 7. Write the questions

The actual assignment questions belong in:

``` text
questions.tex
```

This is intentional.

You should **not** put another `\documentclass` or another complete
LaTeX document inside `questions.tex`.

A simple `questions.tex` can look like:

``` latex
\section*{سؤال اول — ۲۰ نمره}

متن سؤال اول را اینجا بنویسید.

\begin{enumerate}
    \item بخش اول سؤال
    \item بخش دوم سؤال
\end{enumerate}


\section*{سؤال دوم — ۳۰ نمره}

متن سؤال دوم را اینجا بنویسید.
```

The main template automatically includes this file after the cover page:

``` latex
\input{questions}
```

This separation makes it easy to reuse `main.tex` for every assignment
in a course.

------------------------------------------------------------------------

# 8. Creating a new assignment

Suppose you already used the template for Homework 2.

For Homework 3:

### Step 1 --- Copy the template

Create a new folder:

``` text
Homework-3/
```

Copy:

``` text
main.tex
questions.tex
iust-logo.png
vazirmatn-regular.ttf
vazirmatn-bold.ttf
```

into it.

### Step 2 --- Change the configuration

In `main.tex`, update:

``` latex
\newcommand{\assignmentTitle}{تمرین سری سوم}
\newcommand{\assignmentCode}{Hw3}
\newcommand{\releaseDate}{...}
\newcommand{\dueDate}{...}
```

and anything else that changed.

### Step 3 --- Replace the questions

Edit `questions.tex` and write the new questions.

### Step 4 --- Compile

Compile:

``` text
main.tex
```

with **XeLaTeX**.

That's it.

------------------------------------------------------------------------

# 9. Compiling the template

## Option A --- Overleaf

Overleaf is probably the easiest option if you have limited LaTeX
experience.

### Step 1

Create a new project on Overleaf.

### Step 2

Upload all of these files:

``` text
main.tex
questions.tex
iust-logo.png
vazirmatn-regular.ttf
vazirmatn-bold.ttf
```

### Step 3

Open the project settings.

Set the compiler to:

``` text
XeLaTeX
```

This is important because the template uses Persian typesetting through
XePersian.

### Step 4

Click **Recompile**.

You should get the assignment PDF.

------------------------------------------------------------------------

# 10. Compiling locally

You need a LaTeX distribution with XeLaTeX installed.

Common choices are:

-   **TeX Live** --- Windows, Linux, macOS
-   **MiKTeX** --- Windows, Linux, macOS

Then open a terminal in the project directory and run:

``` bash
xelatex main.tex
```

If everything is installed correctly, this will generate:

``` text
main.pdf
```

If you make changes, simply run the command again.

------------------------------------------------------------------------

# 11. Fonts

The template expects these two font files to be in the same directory as
`main.tex`:

``` text
vazirmatn-regular.ttf
vazirmatn-bold.ttf
```

They are loaded directly by the template:

``` latex
\settextfont[
  Path=./,
  UprightFont = vazirmatn-regular.ttf,
  BoldFont    = vazirmatn-bold.ttf
]{Vazirmatn}
```

Therefore, **do not rename the font files unless you also change the
corresponding lines in `main.tex`.**

Keeping the fonts inside the repository also makes the template much
more reproducible across different computers.

------------------------------------------------------------------------

# 12. Logo

The default template uses:

``` text
iust-logo.png
```

If you are using this for an IUST assignment, simply keep the provided
logo.

If you want to adapt the template for another university or
organization, replace the image and change:

``` latex
\includegraphics[width=3.7cm]{iust-logo.png}
```

in `main.tex`.

The rest of the design can remain unchanged.

------------------------------------------------------------------------

# 13. A little LaTeX you may need

You do **not** need to become a LaTeX expert to use this template.

Most of your work will just be writing Persian text.

### Bold text

``` latex
\textbf{این متن ضخیم است}
```

### Italic text

``` latex
\textit{این متن ایتالیک است}
```

### Left-to-right English text

``` latex
\lr{Binary Search Tree}
```

### Inline mathematics

``` latex
$O(n \log n)$
```

### Displayed mathematics

``` latex
\[
T(n) = 2T(n/2) + O(n)
\]
```

### Lists

``` latex
\begin{itemize}
    \item مورد اول
    \item مورد دوم
\end{itemize}
```

### Numbered lists

``` latex
\begin{enumerate}
    \item سؤال اول
    \item سؤال دوم
\end{enumerate}
```

------------------------------------------------------------------------

# 14. Common LaTeX mistakes

Some characters have special meanings in LaTeX.

If you want to write these characters literally, you may need to escape
them:

  Character   Write
  ----------- -------
  `%`         `\%`
  `_`         `\_`
  `&`         `\&`
  `#`         `\#`
  `$`         `\$`

For example:

``` latex
فایل HW\_2 با فرمت PDF ارسال شود.
```

instead of:

``` latex
فایل HW_2 با فرمت PDF ارسال شود.
```

------------------------------------------------------------------------

# 15. What you normally should NOT edit

Unless you want to redesign the template, you should generally leave the
sections below the configuration section alone.

They contain:

-   Page geometry
-   Fonts
-   Page frames
-   Colors
-   `tcolorbox` styling
-   Cover-page layout
-   TikZ drawings
-   Other formatting details

The intended workflow is:

``` text
                 main.tex
                    │
                    ▼
        ┌─────────────────────┐
        │ Assignment Config   │
        │                     │
        │ Course              │
        │ Title               │
        │ Dates               │
        │ Staff               │
        │ Policies            │
        │ Submission          │
        └─────────────────────┘
                    │
                    ▼
        ┌─────────────────────┐
        │ Template Design     │
        │                     │
        │ Frames              │
        │ Cards               │
        │ Fonts               │
        │ Layout              │
        └─────────────────────┘
                    │
                    ▼
             questions.tex
                    │
                    ▼
               Final PDF
```

This separation is the main idea behind the template.

------------------------------------------------------------------------

# 16. Troubleshooting

### `fontspec` cannot find Vazirmatn

Make sure these files are next to `main.tex`:

``` text
vazirmatn-regular.ttf
vazirmatn-bold.ttf
```

Also make sure their names have not been changed.

------------------------------------------------------------------------

### Persian text looks broken

Make sure you are compiling with:

``` text
XeLaTeX
```

and not pdfLaTeX.

------------------------------------------------------------------------

### `iust-logo.png` cannot be found

Make sure the image is in the same directory as `main.tex`.

------------------------------------------------------------------------

### `questions.tex` cannot be found

Make sure the file exists and is named exactly:

``` text
questions.tex
```

------------------------------------------------------------------------

### I changed something but the PDF still looks old

Compile the project again.

If you are using a local LaTeX installation, running:

``` bash
xelatex main.tex
```

again is usually enough.

------------------------------------------------------------------------

# 17. Why use this template?

Writing the content of an assignment is already enough work.

You shouldn't have to repeatedly solve:

-   How should the first page look?
-   How do I make the Persian typography look good?
-   How do I make a clean page frame?
-   How should the course information be aligned?
-   How do I keep every assignment visually consistent?
-   How do I change the policy without touching the layout?

This template tries to separate those two concerns:

> **Content changes. Design stays.**

You configure the assignment once, write your questions, compile, and
get a polished PDF.

------------------------------------------------------------------------

## Contributing

If you improve the design, add useful configuration options, fix a bug,
or make the template easier to use, contributions are welcome.

In particular, improvements that make the template easier for people
with limited LaTeX experience are especially useful.

------------------------------------------------------------------------

## Final checklist

Before releasing an assignment, check:

-   [ ] Course name is correct
-   [ ] Assignment title is correct
-   [ ] Semester is correct
-   [ ] Release date is correct
-   [ ] Deadline is correct
-   [ ] Professors are correct
-   [ ] Assignment designers/TAs are correct
-   [ ] Required slides/material are correct
-   [ ] Total score is correct
-   [ ] Submission platform and link are correct
-   [ ] Answer filename is correct
-   [ ] Policies are appropriate for the course
-   [ ] Late-submission settings are correct
-   [ ] `questions.tex` contains the correct questions
-   [ ] Fonts are present
-   [ ] Logo is present
-   [ ] Final PDF has been checked before release

I hope this can help you as it helped me a lot ^_^

This ReadMe file is generated by AI. Credits to ChatGPT :D
