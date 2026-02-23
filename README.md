# KTH 3rd Cycle Thesis Template (Restructured)
**An unofficial-but-highly-functional LaTeX framework for KTH Doctoral Students.**

[🚀 Getting Started](#getting-started) | [📂 Key Files](#key-files-at-a-glance) | [🚀 For more advanced users](#for-more-advanced-users) | [🤖 Automation](#enhancements-and-workflows) | [🛠 Troubleshooting](#for-problems-with-compile-timeouts)



This Overleaf project is for the LaTeX template called "KTH 3rd cycle template restructured," designed by Gerald Q. Maguire Jr. for use by third-cycle students (i.e., doctoral students - be they licentiate or Ph.D. students) at KTH. One of the main goals of this project is to support all phases of the thesis (process) and all the different *readers* (be they human or machine).

> [!NOTE]
> This template is not an official template; it has been developed to try to address the weakness of the existing templates while trying to be consistent with the graphical design.

One of the key aims of the template is to have you enter information _once_ and reuse this data. This is rather important as some of this information will be used in many different systems (including the announcement for your presentation, the requests for ISBN and TRITA numbers, the metadata and thesis in DiVA, the final grade in LADOK, and even on your diploma). My experiments in quality control of previous theses revealed that manually entering this information across these many different systems results in numerous errors and inconsistent data.

A second aim is to help you write your thesis and avoid many common problems that have occurred in the past. These common problems range from having an incorrect subject on the cover of the thesis to errors in numbering of the pages/sections/... in the thesis; missing lists of acronyms, figures, tables, and nomenclature; and missing bibliographic data, missing SDGs, national subjects, and other data that will help your readers. 

A third aim is that if there are errors, the errata.tex document should help you produce an errata document that can be introduced before the start of the defense and added to DiVA to help your subsequent readers.

The project contains many README files; consult them for further details.

# The "3-Minute Setup" summary
1. Fork/Clone Repo - to create your personal workspace.
2. Run scripts/config_wizard.py - enter your metadata.
3. Create a new project in Overleaf and Import from GitHub - syncronize with GitHub
4. Start writing with a working template.

## Core Features

* Bilingual Support: Easy switching between English and Swedish.

* Multilingual support: Supports abstracts and content in all the languages (and then some) used in earlier theses.

* Compilation Theses: Native support for including previous publications. There are even tools to help you access the information in DiVA about your previous publications and to produce a list of included (or excluded) publications. 

* Multi-system Sync: Automatically collects data for later use in DiVA, LADOK, and your diploma.

* Support for UTF-8 text: Automatic conversion of many titles and subtitles to their UTF-8 (plain text) versions, as these are needed for many of the record systems, such as LADOK. 

* Error Avoidance: Built-in checks for missing SDGs and national subject(s), thesis subject from your education code, ... .



## Getting started
A student should begin by reading the `Quick_Start_Guide` (.tex or .pdf) file. This three-page guide gives the four most important steps to get started.

The `README_3rd_cycle_author` (.tex or .pdf) file provides information the student will want to know about working with the template.

Most students will only need to configure their thesis-specific values (author information (name, KTHID, ...), supervisors, titles, etc.) in custom_configuration, and then can start turning the file examplethesis.tex into their thesis. Acronyms should be added to the file `lib/acronyms.tex`. If you need to include additional LaTeX libraries, look at `lib/includes.tex` or `lib/includes-after-hyperref.tex` (the latter file is for packages that must be loaded after hyperref).

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

If you need to add additional fonts, take a look at `kth/kth-fonts.tex`

The folder `README_notes` contains more specialized information for users, supervisors, administrators, and programmers. It also contains files that describe the KTH DOCX template and another LaTeX template (called here the Tekla template) that started with my template (but unfortunately removed most of the important functionality).

## For problems with compile timeouts
If you run into (compile) timeouts and have added additional fonts, take a look at Saving_and_restoring_font_cache.tex. By modifying and compiling this file, you can cache the fonts you use, saving a lot of time when compiling.

This requires manually copying the files from the compilation results into a directory in your project. This is necessary because the LaTeX compiler runs in a container that does not have write access to the Overleaf project itself; instead, it only gets a copy of these files when the container is run.

## Enhancements and Workflows
By making this template available via GitHub, we exploit the ability of CI/CD (GitHub Actions) to automate thesis metadata management. This repository currently supports:

* **Automated Publication Discovery:** Metadata is pulled directly from DiVA based on the author's KTHID.
* **Controlled Inclusion:** A JSON-based mapping system (`publications_map.json`) allows authors to curate which publications are "included" or "not included" in the thesis with custom labels (e.g., `paper:A`, `patent:B`).
* **LaTeX Generation:** Direct insertion of formatted publication lists into the document. The system supports LaTeX math mode in titles, citation validation against `references.bib`, and automatic character escaping.

## Getting Started with GitHub
To leverage the automation features, you should establish a workflow between your local machine, GitHub, and Overleaf. For information about GitHub and Overleaf integration see [GitHub synchronization](https://docs.overleaf.com/integrations-and-add-ons/git-integration-and-github-synchronization/github-synchronization)

### 1. Repository Setup
1. **Create your own Repository:** It is recommended to create a new private repository on GitHub to host your thesis.
2. **Clone & Push:**
   * Clone this template repository to your local machine:
     ```bash
     git clone https://github.com/gqmaguirejr/KTH-3rd-cycle-template-restructured.git
     ```
   * Change the "remote" to point to your new personal repository:
     ```bash
     git remote set-url origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
     ```
   * Push the content: `git push -u origin main`

### 2. Establish Overleaf Integration
1. In Overleaf, create a **New Project** and select **Import from GitHub**.
2. Select your newly created repository.
3. Overleaf is now "coupled" to your GitHub repository. You can push changes from Overleaf to GitHub using the **Menu > GitHub** sync feature.

### 3. Synchronized Workflow
Because GitHub Actions automatically commit changes back to your repository (such as the generated publication list), you must synchronize these your local Git, your GitHub Repository, and your Overleaf project:

	Local Git <==== push/pull ====> GitHub Repository <==== Overleaf sync (push/pull) ====> Overleaf project

* **In Overleaf:** Best for writing your thesis text. Once you have finished a section, use the Overleaf menu to **Push** your changes to GitHub.
* **On GitHub:** Use the **Actions** tab to manually trigger the **Manual DiVA Discovery Test** workflow when you have added new records in DiVA for your publications.
* **Locally:** Best for managing the `publications_map.json` file or debugging scripts. **Important:** Always run `git pull --rebase` locally before starting work to ensure you have the latest files generated by GitHub Actions.

> [!IMPORTANT]
> **Granting Workflow Permissions:**
> For the automated scripts to commit the generated `lib/publications_generated.tex` file back to your repository, you must enable write permissions:
> 1. In your GitHub repository, go to **Settings > Actions > General**.
> 2. Scroll down to the **Workflow permissions** section.
> 3. Select **Read and write permissions**.
> 4. Click **Save**.

> [!CAUTION]
> **Write Permissions Required:** Automated publication lists will fail to update unless you set **Workflow permissions** to **Read and write permissions** in your repository settings.


## Customizing custom_configuration.tex
You can locally edit the `custom_configuration.tex` file and the commit it to your repository and then sync with Overleaf.

Alternatively, it you prefer to point-and-click, there is now configuration wizard (`config_wizard.py`). You can invoke this wizard on your local machine:

```bash
streamlit run ./scripts/config_wizard.py
```

This will run the script with your local browser via the URL: http://localhost:8501 so you can fill in the form, then download the resulting LaTeX and upload the `config_snippet.tex` file to your repository.
> [!TIP]
> Before running script the first time, be sure you have installed the relevant libraries with

```bash
pip install streamlit requests beautifulsoup4
```

> [!NOTE]
> This script may not always be able to get the KTHID for a given user or supervisor (as the script is **not** using the KTH Profile API -- since this would require an API key). As a result you may need to collect this information manually by asking your KTH supervisors for this missing information or if you are logged into KTH you may be able to see the KTHID at the bottom of the user's profile page.

If you downloaded the file to `~/Downloads/config_snippet.tex` you can upload it with:

```bash
cp ~/Downloads/config_snippet.tex .
git add config_snippet.tex
git commit -m "introduced config_snippet.tex" config_snippet.tex
```

This will automatically trigger the **Merge Wizard Configuration** workflow (`.github/workflows/merge_wizard.yml`) and it will run a script to merge your snippets with the `custom_configuration.tex` file and it will delete the file with your snippets from the repository.  Now sync your Overleaf project with your GitHub repository.

## Managing your Publications
Once you have your KTHID in your `custom_configuration.tex` file and you have added all of your publications to your `references.bib` file; then, you can automate the generation of your list of publications (for example, essential in a compilation thesis). You do this via the following steps:

1. **Discovery:** Go to the **Actions** tab in GitHub and manually run the **Manual DiVA Discovery Test** workflow. This fetches your data from DiVA and populates `publications_map.json`.
2. **Curation:** Edit `publications_map.json` (either locally, in the GitHub web editor, or via Overleaf). 
   * Change `status` to `"included"` for papers in your thesis.
   * Assign a `label` (e.g., `"paper:A"`).
   * Optional: Provide a `"full title"` to override the DiVA title or a `"better_bib_key"` to override the automatically discovered BibTeX key.
3. **Generation:** Any push containing changes to `publications_map.json` triggers the generator script. This automatically creates `lib/publications_generated.tex`.
> [!NOTE]
> You can also manually run the **Sync Publications** workflow.

4. **Integration:** Pull the latest changes into Overleaf or your local environment. Your thesis will now contain the updated list of publications, cross-referenced correctly with your bibliography.
> [!TIP]
> If you have (1) made changes in Overleaf and pushed them to the repository or (2) a script has updated files in the repository be sure to do a `git pull` on your local git **before you start working locally**.

> [!TIP]
> **Handling Synchronization with `git pull --rebase`**
> Because GitHub Actions commit the generated LaTeX files directly to your repository, your local environment will frequently fall "behind" the remote server.
> 
> If you see an error stating you have **divergent branches**, run:
> ```bash
> git pull --rebase origin main
> ```
> This command takes your local changes and "replays" them on top of the latest automated commits from GitHub, maintaining a clean, linear project history. 
> 
> *Note: If you have unstaged changes, run `git stash` before pulling, and `git stash pop` after.*

## Potential enhancements
It would be nice to:
* automate the configuration of custom_configuration.tex (currently, this can be done via a python script from the English language PDF file of your eISP; but could perhaps been done better with another integration) and
* automatically fetch the PDFs of included publications

Expect futher automation, but it may occur slowly.


## Contributing and Feedback
As this is a template designed to address specific workflow gaps, feedback from the KTH community is welcome.

* **Reporting Issues:** If you find a bug or a discrepancy with KTH's current graphical profile, please [open an issue](https://github.com/gqmaguirejr/KTH-3rd-cycle-template-restructured/issues). Please include a description of the problem and the relevant LaTeX error or log.
* **Feature Suggestions:** Have an idea for further automation (like the DiVA or LADOK integrations)? Feel free to share your thoughts in the "Issues" tab.
* **Pull Requests:** To ensure stability for all students, please open an issue to discuss any significant changes before submitting a Pull Request.
