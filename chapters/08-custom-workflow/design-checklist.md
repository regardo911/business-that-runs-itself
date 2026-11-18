<!-- Chapter 8, A Finished quote-job/SKILL.md, Top to Bottom. The seven design questions verbatim; the book's version-it sentence split into four bullets. Source: ch08.md:152-160 -->
# Custom workflow design checklist

Answer these before you write a custom workflow:

- What is the one task this handles?
- What inputs does it need from me each time?
- Which context files should it read?
- What is the output format?
- What should it never do? (estimate facts it can't see, send anything, promise availability)
- Where does it stop and ask for my approval?
- How will I test it safely before trusting it on a real customer?

Version it:

- Save the original before you touch it.
- Name your copy clearly (`quote-job`, not `quote-job-final-v2`).
- Note the date you changed it.
- Run the first test on a fake or low-stakes job before you point it at a real customer.
