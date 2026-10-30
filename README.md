# CAL02 Online Modules

Self-paced online modules for **Integral Calculus**
(Instr. Ryan M. Vitalez, LPT, Department of Earth and Space Sciences, Rizal Technological University),
following James Stewart, *Calculus*, 8th edition. Students use them on days when class cannot meet in person.

**Entry point:** https://mrvitalez.github.io/IntegCal-online-module/ sends students to the student site, which is a
Google Apps Script web app open only to **@rtu.edu.ph** accounts. The instructor has a separate admin site on the
same deployment (`?page=admin`). Setup: [INSTRUCTOR-SETUP.md](INSTRUCTOR-SETUP.md).

Each module has:

1. **Discussion**: one part per textbook section, with key equations, original figures and common mistakes.
2. **Worked examples**: three solved problems, solutions hidden until opened.
3. **Lecture video**: one free lecture (cited on the page) that pauses for three multiple-choice questions;
   answers are recorded.
4. **Activity**: 8 graded items plus a reflection. Answers can be numbers, exact values (`pi/4`) or formulas
   (`x^2 sin(x) + C`); formulas are checked for equivalence, so any correct form is accepted. The student's RTU
   email is detected automatically; they enter their name, student number and block and section, write solutions
   with a symbol/LaTeX toolbar and live preview, and see their score and per-item results on submit.

| # | Module | Stewart | Video |
|---|--------|---------|-------|
| 1 | Areas, Distances and the Definite Integral | §4.1, §4.2 | Lecture 18: Definite Integrals (MIT OpenCourseWare) |
| 2 | The Fundamental Theorem of Calculus | §4.3, §4.4 | Lecture 19: First Fundamental Theorem of Calculus (MIT OpenCourseWare) |
| 3 | The Substitution Rule | §4.5, §4.5 | Lecture 15: Differentials and Antiderivatives (MIT OpenCourseWare) |
| 4 | Areas Between Curves and Volumes | §5.1, §5.2 | Lecture 22: Volumes by Disks and Shells (MIT OpenCourseWare) |
| 5 | Cylindrical Shells, Work and Average Value | §5.3, §5.4, §5.5 | Lecture 23: Work, Average Value, Probability (MIT OpenCourseWare) |
| 6 | Integration by Parts and Trigonometric Integrals | §7.1, §7.2 | Lecture 30: Integration by Parts, Reduction Formulae (MIT OpenCourseWare) |
| 7 | Trigonometric Substitution and Partial Fractions | §7.3, §7.4 | Lecture 28: Integration by Inverse Substitution; Completing the Square (MIT OpenCourseWare) |
| 8 | Strategy for Integration and Improper Integrals | §7.5, §7.8 | Lecture 36: Improper Integrals (MIT OpenCourseWare) |
| 9 | Special Topics: Laplace and Fourier Transforms *(optional)* | special topic | Lecture 19: Introduction to the Laplace Transform; Basic Formulas (MIT OpenCourseWare) |
| 10 | Arc Length, Surface Area and Probability | §8.1, §8.2, §8.5 | Lecture 31: Parametric Equations, Arclength, Surface Area (MIT OpenCourseWare) |
| 11 | Parametric Curves and Their Calculus | §10.1, §10.2 | Lecture 5: Parametric Equations for Lines and Curves (MIT OpenCourseWare) |
| 12 | Polar Coordinates and Conic Sections | §10.3, §10.4, §10.6 | Lecture 32: Polar Coordinates; Area in Polar Coordinates (MIT OpenCourseWare) |
| 13 | Sequences and Series: First Convergence Tests | §11.1, §11.2, §11.3, §11.4, §11.5 | Lecture 37: Infinite Series and Convergence Tests (MIT OpenCourseWare) |
| 14 | Ratio and Root Tests, Power Series and Taylor Series | §11.6, §11.7, §11.8, §11.9, §11.10, §11.11 | Lecture 38: Taylor's Series (MIT OpenCourseWare) |
| 15 | Vectors and Vector Functions *(optional)* | §12.2, §12.3, §12.4, §13.1, §13.2 | Lecture 1: Dot Product (MIT OpenCourseWare) |

Problem sets (answered in the notebook, linked from the home page):

- Problem Set 1: Introduction to Integrals (modules 1, 2, 3)
- Problem Set 2: Applications of Integration (modules 4, 5)
- Problem Set 3: Techniques of Integration (modules 6, 7, 8, 9)
- Problem Set 4: Applications of Integration II (modules 10)
- Problem Set 5: Parametric Equations and Polar Coordinates (modules 11, 12)
- Problem Set 6: Infinite Sequences and Series (modules 13, 14)

The discussions, examples and problems are original and follow the order and notation of Stewart's *Calculus*;
no text or figures are copied from the book. Videos: MIT OpenCourseWare (CC BY-NC-SA 4.0).

## Files

```
index.html, modules/      Entry pages that send visitors to the RTU-only student site
assets/config.js          The student site URL (set once by the instructor)
assets/style.css          Shared styles (Midnight Navy with Emerald theme)
content/                  Lessons, activities, problem sets, manifest and syllabus (no answers)
img/                      Figures and the university seal
apps-script/              Code for the Apps Script project: Code.gs, Student.html, Admin.html, Styles.html
```

The answer key and the video question answers are **not** in this repository. They are seeded from a private
`Seed.gs` file and then kept only in the instructor's Google Sheet.
