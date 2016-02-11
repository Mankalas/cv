# cv
My CV, written in LaTeX.

## Presentation

Sick of manually maintaining several versions of my résumé, I decided to take advantage of LaTeX to easily produce a highly versatile CV. The compilation process is slightly more complex, but the maintenance is clearly less time-consuming.

## How it works

This project uses the LaTeX package [CurVe](http://www.ctan.org/tex-archive/macros/latex/contrib/curve/), a Curriculum Vitæ package written by Didier Verna (a cool guy, you should check his [website](http://didierverna.com/)).

Thanks to this package, I can generate different "flavors" of a CV in order to, as the CurVe doc says, "emphasize on different aspects of [my] background".

The entry point of the generator, `cv.<flavor>.ltx`, includes:
  - flavorless_preamble is where everything is common is defined, like the used packages and some custom commands;
  - flavored_preamble includes the contact informations and some custom strings;
  - cv_body, which includes (order may varies according to the flavor):
    - professionnal objectives;
    - experience;
    - skills;
    - education;
    - languages;
    - hobbies & interests;
    - referees
    
## Where the magic happens
  
The true trick that helps me deal with changes and fixes is the fact that all my experiences and skills are defined as LaTeX commands and grouped in files like `skills_def.ltx` and `experience_def.ltx`. These commands are used in the actual rubrics, therefore any change is automatically propagated to every possible flavor I've defined.

Also, French and English versions of the same command are side-by-side. Therefore, I can check that my CV is up-to-date in both languages. I doubt I will ever need another language, but using the same system, I could easily update my skills and experience in, say Spanish, add a new flavor (you can't elude that because you must have a way to select your language) and

Speaking of languages, there's files suffixed by a language code (`education` and `header`). They contain "absolute" content which does not depend on the CV's flavor - only the language.
