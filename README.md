# KTH 3rd cycle template restructured
This Overleaf project is for the LaTeX template called "KTH 3rd cycle template restructured," designed by Gerald Q. Maguire Jr. for use by third-cycle students (i.e., doctoral students - be they licentiate or Ph.D. students) at KTH. One of the main goals of this project is to support all phases of the thesis (process) and all the different *readers* (be they human or machine).

**Note** This template is not an official template; it has been developed to try to address the weakness of the existing templates while trying to be consistent with the graphical design.

One of the key aims of the template is to have you enter information _once_ and reuse this data. This is rather important as some of this information will be used in many different systems (including the announcement for your presentation, the requests for ISBN and TRITA numbers, the metadata and thesis in DiVA, the final grade in LADOK, and even on your diploma). My experiments in quality control of previous theses revealed that manually entering this information across these many different systems results in numerous errors and inconsistent data.

A second aim is to help you write your thesis and avoid many common problems that have occurred in the past. These common problems range from having an incorrect subject on the cover of the thesis to errors in numbering of the pages/sections/... in the thesis; missing lists of acronyms, figures, tables, and nomenclature; and missing bibliographic data, missing SDGs, national subjects, and other data that will help your readers. 

A third aim is that if there are errors, the errata.tex document should help you produce an errata document that can be introduced before the start of the defense and added to DiVA to help your subsequent readers.

The project contains many README files; consult them for further details.

[Getting Started](#getting-started) | [Key Files](#key-files-at-a-glance) | [For more advanced users](#For-more-advanced-users) | [Fixing Timeouts](#for-problems-with-compile-timeouts)

## Core Features

* Bilingual Support: Easy switching between English and Swedish.

* Multilingual support: Supports abstracts and content in all the languages (and then some) used in earlier theses.

* Compilation Theses: Native support for including previous publications. There are even tools to help you access the information in DiVA about your previous publications and to produce a list of included (or excluded) publications. 

* Multi-system Sync: Automatically collects data for later use in DiVA, LADOK, and your diploma.

* Support for UTF-8 text: Automatic conversion of many titles and subtitles to their UTF-8 (plain text) versions, as these are needed for many of the record systems, such as LADOK. 

* Error Avoidance: Built-in checks for missing SDGs and national subject(s), thesis subject from your education code, ... .



## Getting started
A student should begin by reading the Quick_Start_Guide (.tex or .pdf) file. This three-page guide gives the four most important steps to get started.

The README_3rd_cycle_author (.tex or .pdf) file provides information the student will want to know about working with the template.

Most students will only need to configure their thesis-specific values (author information (name, KTHID, ...), supervisors, titles, etc.) in custom_configuration, and then can start turning the file examplethesis.tex into their thesis. Acronyms should be added to the file lib/acronyms.tex. If you need to include additional LaTeX libraries, look at lib/includes or lib/includes-after-hyperref (the latter file is for packages that must be loaded after hyperref).

At the top of examplethesis.tex you will see that it is easy to configure (within \documentclass) whether your thesis is being written in English or Swedish, which bibliographic tool you want to use, whether you are including publications (for a compilation style thesis) or not, and what languages of abstracts you want to have (beyond the required English and Swedish abstracts and keywords).

### Key Files at a Glance

| File | Purpose |
| :--- | :--- |
| **Quick_Start_Guide.pdf** | **Read this first.** A 3-page guide to get you started. |
| **examplethesis.tex** | Your main document. Start writing here. |
| **custom_configuration.tex** | Personal info: Name, KTHID, supervisors, and titles. |
| **lib/acronyms.tex** | Define all your abbreviations here. |
| **lib/includes.tex** | Add your LaTeX packages/libraries here. |
| **lib/includes-after-hyperref.tex** | Add LaTeX packages/libraries here that must be loaded after the hyperref package, e.g., packages like cleveref. |
| **errata.tex** | Use this to generate an errata sheet if errors are found after printing. |

## For more advanced users
More advanced users might also want to modify or add to the definitions in lib/defines.tex.

If you need to add additional fonts, take a look at kth/kth-fonts.tex

The folder README_notes contains more specialized information for users, supervisors, administrators, and programmers. It also contains files that describe the KTH DOCX template and another LaTeX template (called here the Tekla template) that started with my template (but unfortunately removed most of the important functionality).

## For problems with compile timeouts
If you run into (compile) timeouts and have added additional fonts, take a look at Saving_and_restoring_font_cache.tex. By modifying and compiling this file, you can cache the fonts you use, saving a lot of time when compiling.

This requires manually copying the files from the compilation results into a directory in your project. This is necessary because the LaTeX compiler runs in a container that does not have write access to the Overleaf project itself; instead, it only gets a copy of these files when the container is run.
