# Manual: Reproducibility Test

------

**The Reproducibility Test contains two crucial aspects in total, which determine all steps of this manual and which should always be kept in mind:**

- **<u>A. Reproduction of the analyses</u>: Can all the authors' figures and results be reproduced with the available data and scripts?**

  **➔ If this criterion cannot be fulfilled, it does not make sense to continue with B). Therefore, two termination criteria have been built into the manual. Each of them leads to a direct report of the problems/discrepancies to the authors.**

- **<u>B. Reusability:</u> Are all files (e.g. raw data, scripts) structured in such a way that they can be easily reused by external persons for their own research?**

  **➔ The document offers some central guiding questions in the second part, which can be used as orientation regarding this aspect. However, you should simply note down everything that could make the reuse of any material/data/scripts difficult.**  

<br>

**Please carry out the following steps and note down the respective results regarding the requirements/ questions mentioned within this manual. Therefore, you can use the associated checklist (REPRO_CHECKLIST_PDF)) that follows the numbering from this manual regarding the requirements.**

------------------------------------------------------------------------

**0.** **Download all files of the project!**

> Requirement 0. Are they located in one place? Are they easy to find?
>   

<br>

**1.** **Code check**

**a\) Execute all analysis scripts in the correct order (e.g. following the instructions from the ReadMe document or the numbering of the documents)**

 - **Make sure that the respective programme version (e.g. R version) is used that the authors used for their analyses.** The programme version should be specified in the ReadMe document or a separately attached file (e.g. labelled "session_info"). Using the R-installation manager (<https://github.com/r-lib/rig>) you ca easily install, remove and switch between different R versions within the same R session on MacOs, Windwos and Linux. Other alternatives are Rswitch (<https://rud.is/rswitch/>) for MacOs or suggestions that can be found at <https://support.rstudio.com/hc/en-us/articles/200486138-Changing-R-versions-for-RStudio-desktop>.

 - **Make sure that the respective software package versions (e.g. R package versions) are used that the authors used for their analyses.** To do this, it may be necessary to install older, out-of-date versions of packages that were used when writing the script. Ideally, authors should therefore include a renv file and an R Project file in the project. Then, by calling the R Project file, the whole project can be loaded into R with the correct package versions. Subsequently, you just simply have to execute all the individual scripts in the R project. These then automatically use the versions specified in the renv file, although your current versions can still be used outside the project. However, not all authors follow this optimal procedure. Sometimes the package versions are only specified in the ReadMe document or a separately attached file (e.g. labelled "session_info"). Then, you have to manually load the package versions. In R this is possible using the command `install_version("psych", version = "2.1.6", repos = "http://cran.us.r-project.org")`; see <https://support.rstudio.com/hc/en-us/articles/219949047-Installing-older-versions-of-packages> for more information. Anyway, the ReadMe file should include instructions for using the correct software versions.

 - **Make sure to execute all scripts once and in the correct order**, especially if a "set.seed" is used at any point in the code. Otherwise, the results can differ considerably. The "set.seed" ensures that the same random values are selected in random processes (see also: <https://r-coder.com/set-seed-r/>).If a "set.seed" command is used, this should also be noted in the ReadMe file, e.g. in the description of all necessary steps for the complete reproduction of the analyses.

> Requirement 1.1. Do all analyses run without errors or are there any error messages/omissions? Make a note of the errors and the scripts which produced them! How long does it take to run through all the scripts? Does the time roughly correspond to the authors' specifications in the ReadMe document (if available)? Make a note of the time and report back!
> 

**➔ 1st Termination criterion (➔ direct feedback to authors):**

*If the scripts cannot be run through, first look for a solution to the problem yourself (e.g. with the help of the ReadMe file or a quick google search). Note down successful solutions in order to be able to report them back to the authors later as a tip/hint. If no solution is found: Please report the problem directly to the authors and interrupt the reproducibility test at this point until a solution is found!*  
<br>

**b\) Do the actual check by comparing the reproduced results with the authors' results! Using the scripts or the README-file it should be easy to identify which tables, figures and in-text numbers are produced by which script. List the comparisons in an Excel spreadsheet according to the following scheme (see Table below) and describe any differences:**

 - In the results section of the paper, mark all passages (including tables/figures/results within the body text) that contain results (especially figures, graphs) of the analyses carried out. Compare these individually with your own results from the executed scripts. The numbers within the body text do not have to be added individually to the spreadsheet; it is sufficient if all sections within the Results are listed with their headings. The authors should make clear where the respective results can be found (e.g. within ReadMe document and/or the scripts by adding appropriate comments).

 - If there are data sets in the project folder that were created by other pre-processing scripts (e.g. in folders called "Processed Data"), these data sets should also be compared with the data sets that were created during the reproduction test. For this purpose, there are so-called dif tools that can be used to look for differences between two files (e.g. csv). This way you don't have to go through every single line yourself, which can be very time-consuming with long data sets. A recommendation of different dif tool programmes can be found at <https://www.git-tower.com/blog/diff-tools-windows> (for Windows) or <https://www.git-tower.com/blog/diff-tools-mac/> (for Mac). If you find differences in these generated data sets and report them, it makes it easier for the authors to find out where the problems occurred during the reproduction attempt.

| **Preprocessing script**                        | **Data sets created**                              |                            | **Successfully reproduced?** *If not, list all differences here!* |
| :----------------------------------------------- | :------------------------------------------------- | :-------------------------- | :------------------------------------------------------------ |
| e.g. 0a preprocessing                           | e.g. processed_data.csv                            |                            | e.g. Yes                                                     |
| ...                                             | ...                                                |                            | ...                                                          |
| **Graphic/table/number in text**                | **Script *which produced the respective output*** | **Line in the manuscript** | **Successfully reproduced? *If not, list all differences here!*** |
| e.g. Figure 1                                   | e.g. 2-Analyses                                    | After line 300             | e.g. different size of the last bar (chart)                  |
| e.g. Descriptive statistics of the participants | e.g. 1-Demographics                                | e.g. line 320              | e.g. Yes                                                     |
| ...                                             | ...                                                | ...                        | ...                                                          |

**➔ 2nd Termination criterion (➔ direct feedback to authors):**

*If any results cannot be reproduced, first very briefly check possible simple sources of error yourself (e.g. wrong sequence when executing the scripts; different software versions). If no solution is found: Please report back directly to the authors (➔send completed excel spreadsheet) and interrupt the repro test at this point until a solution is found!*  
<br>

> Requirement 1.2. Are all tables from the manuscript reproducible? Make a note and SAVE file (screen-shot/jpg) if any table looks different!
>

> Requirement 1.3. Are all figures from the manuscript reproducible? Make a note and SAVE file (screen-shot/jpg) if any figure looks different!
> 

> Requirement 1.4. All all in-text-numbers from the manuscript reproducible? Make a note of the numbers if any in-text-number is different!
> 
  
> Requirement 1.5. Is it possible and easy to identify which tables, figures and in-text numbers are produced by which script/program (e.g. using the README-document and/or the comments within the scripts)?
> 

**c\) Go through individual analysis scripts (e.g. R scripts)!**

> Requirement 1.6. Are the files named in a meaningful way, so that one can immediately derive from the title of each script what it is about and in which order the scripts should be executed?
>

> Requirement 1.7. Does a "Master" script file exist that can be executed to automatically run all other scripts without having to run them individually yourself?
>

> Requirement 1.8. Are the lines of code sufficiently commented so that one can basically understand which steps are carried out?  
> <br>

**2. Search for ReadMe file!**

>  Requirement 2.1.  Does it provide brief meta-information about the project (e.g. author, name of the paper, approximate topic)?
>

> Requirement 2.2.  Does it include an overview of all files (data, scripts) including their source and availability (e.g. name of specific folders)?
>

> Requirement 2.3.  Does it describe all the necessary steps to fully reproduce the analyses?
>

> Requirement 2.4.  Does it sufficiently point out requirements/prerequisites regarding the software to be used (e.g. versions of the R packages; running time of the scripts; working memory of the computer)?  
> <br>

**3. Get an overview of all research data!**

> Requirement 3.1.   Are there general descriptions/meta-data for all raw/primary data that give general information about their content (e.g. survey periods, survey locations, type of data)? These should allow potential re-users to quickly decide whether the data is useful for their purposes. This meta-data should be easily accessible via the link to the data in the paper (e.g. located directly on the website where the data is stored). Ideally, an additional meta file in json format should be included, following the recommendations within this google-document <https://docs.google.com/document/d/1u8o5jnWk0Iqp_J06PTu5NjBfVsdoPbBhstht6W0fFp0/edit#heading=h.v795m5ev9q> and the section there entitled "6.1. Dataset-level metadata (dataset_description.json)".

> Requirement 3.2.    Is there a direct link to the data in the paper?

> Requirement 3.3.   Do all raw/primary data have codebooks that describe all variables contained in the files in an understandable way? This does not apply to the data that is only created with the specified scripts (e.g. data in folders with names like "processed_data"), but only to the data that is actually necessary to run the scripts in the first place.  

> Requirement 3.4.   Are there summary statistics (e.g. mean values/standard deviations) for all raw/primary data?

> Requirement 3.5.   Is there a data citation provided somewhere? It should be provided within the paper if external data are used or within ReadMe/paper/project folder to reuse data if they were produced within the same project.
>

> Requirement 3.6.   Do all files have a CSV-, TSV- or TAB-format (necessary to ensure compatibility with various programmes) and can they be opened without any problems?
>

>  Requirement 3.7.   Are all variables in the data sets named?
>

> Requirement 3.8.   Are all data sufficiently anonymised (especially anonymisation/removal of personal details such as names/birth dates)? This point does not need to be checked specifically by independently searching for non-anonymised data. However, it is important to note and pass on any anomalies encountered when conducting the reproducibility test.

**Think of any additional aspects that could be pointed out to the authors, even if they are not mandatory.** Examples are:

- Are the data stored in a data archive? This makes the data easier to be found and thus easier to reuse.
- Are there any other parts of the workflow that authors could improve (e.g. shorten code)?
- Are the statistical methods used suitable for answering the research question?
- Would it be reasonable to provide a “toy” example, or smaller dataset that can be quickly analysed to demonstrate that the workflow runs correctly?
- ...
