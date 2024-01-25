# Manual Researchers: Reproducibility Test

------

**If you want to guarantee the reusability of your data and code, and a successful reproducibility attempt by the reproducer, you should keep in mind the following when finalizing your data, script and other project files.**  

<br>

**The Reproducibility Test generally contains these two aspects:**

  - **<u>A. Reproduction of the analyses</u>: Can all your figures and results be reproduced with the available data and scripts?**

    **➔ If this criterion cannot be fulfilled, it does not make sense to continue with B). Therefore, two termination criteria (1. scripts cannot be run through; 2. Figures/results cannot be reproduced) have been built into the manual for the reproducer. Each of them leads to a direct report of the problems/discrepancies to you as the author.**

  - **<u>B. Reusability:</u> Are all files (e.g. raw data, scripts) structured in such a way that they can be easily reused by external persons for their own research?**

    **➔ You should think about everything that could make the reuse of your material/data/scripts difficult. Three central aspects to improve the reusability are a helpful code description (e.g.  understandable comments within your scripts), reasonable and consistent variable names within both data files and codebooks and some kind of meta-data that provide a quick overview what your data and project are about.**

<br>

**It is important to provide all necessary documents and information so that the reproducer can at least complete a full Reproducibility Test. The following manual aims to provide you with some central steps to a) make sure that the reproducibility test can be conducted completely and b) guarantee some minimal standards which will help to make the reproducibility attempt as successful as possible.**

------------------------------------------------------------------------

0. **Upload all files of your project into one place (e.g. an osf-project)** or at least make sure that all information how all files are accessible can be found at one place. The project and its link should be a persistent archive that will not be removed or change its address.

   0.1. Make sure that files containing your (raw) data have a CSV-, TSV- or TAB-format (necessary to ensure compatibility with various programmes).
   0.2. Use UTF-8 (or UTF-16) encoding for all files to avoid problems in an international context (e.g., so characters like ü or é aren’t mangled)
   0.3. Make sure to include codebooks for at least all raw data files.  
   0.4. Optimally, your project contains a R project file and such a structure of the folders and data files that the reproducer can simply download and save the complete project folder and then execute the scripts without further changes. Therefore, the scripts should use relative paths for loading data/ other scripts (e.g. ".../data/raw_data")
   0.5. Create a "Master" script file (e.g. named 0_Make.R) that can be executed by the reproducer to automatically run all other scripts without having to run them individually.
   0.6. You should use a "set.seed" (https://r-coder.com/set-seed-r/) in your scripts if you simulate something or use a random number generator to guarantee that the same "random numbers" will be used.
   0.7. Make sure that the project includes a ReadMe-file (see 2. for what should be included in this file).
   0.8. Ethical sharing: No uploaded data should contain any information that makes participants identifiable.
   0.9. Add individual citation info for (raw) data and analysis script(s), so that people can use it to cite your work when reusing it. Optimally, you add a DOI for code and data that is also included in this citation info. This makes your code and data findable.

   <br>

1. **Make sure that the correct versions of the software and software packages (e.g. versions of R packages) can be used by the reproducer (dependency management)**. Therefore, you might choose between the following options ranked by their quality (best option first):

    a) Provide a completely reproducible workflow with R Markdown, Git, a "Make-file", and containers like Docker (https://www.docker.com/products/docker-desktop/) or CodeOceanHQ (https://codeocean.com/). This automatically guarantees that the analysis will be reproduced in the exact same environment that you used to conduct them. A more concrete suggestion on how to implement such a workflow can be found in a paper by Peikert & Bramdmaier(2021, https://www.imprs-life.mpg.de/318048/12_peikert_brandmaier_21.pdf).
    b)  To guarantee a kind of minimal dependency management, so that the author can at least automatically use the correct package versions: Include a renv file that specifies the used package versions and an R Project file in the project. More information about this option can be found at https://www.rstudio.com/blog/renv-project-environments-for-r/. Another option among others for R would be packrat (see https://rstudio.github.io/packrat/).
    c) Include an additional file where all package versions are specified. Therefore, you can include the output of the code “devtools::session_info()” from the R session where you have produced your results or "requirements.txt" in python.

  <br>

2. **Add a ReadMe-file (in a TXT, MD or PDF-format) to the project** that explains all steps necessary to reproduce your analyses, especially the following points:  
  2.1. Programme version (e.g. R-version) that you used or that is necessary to reproduce your analyses.  
  2.2. Information about requirements regarding the computational environment (e.g. working memory of the computer, Mac/Windows version of the computer, approximate running time of your code)  
  2.3. Information about how to make sure that the correct versions of the software packages (e.g. versions of R packages) can be used by the reproducer. Therefore, you might choose between the options stated in point 1.  
  2.4. Information on where to find all (raw) data files necessary to reproduce your analyses. Here, you can also shortly add a short note if any data files included in your project are no raw data but instead should be reproduced by the reproducer himself/herself (e.g. by running the pre-processing scripts using raw data files)  
  2.5. Information on how to save the data files in order to be able to successfully execute the scripts. Optimally, your project contains a R project file and such a structure of the folders and data files that the reproducer can simply download and save the complete project folder and then execute the scripts without further changes.  
  2.6. Information on the order in which the R scripts should be executed to reproduce your results. If you use a "set.seed" ((see also: https://r-coder.com/set-seed-r/), it would be a good idea to add an additional comment about it within the ReadMe-file, so that the reproducer does not run into any error e.g. repeatedly executing parts of this script. Here, you can also mention your "Master" script file (e.g. named 0_Make.R) if you included one.
  2.7. Indication of which parts of the code produce which figures/tables/numbers. Alternatively, you can also use RMarkdown so that the whole paper will be reproduced.

  <br>

3. **Add a LICENCE.txt file** that defines the license under which the code can be reused. Typical choices are MIT (a permissive license) or GPLv3 (a copyleft license). See https://choosealicense.com or https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002598 for guidance on how to choose an appropriate license.  

  <br>

4. **Self-check the reproduction of your analyses** by downloading data and code from the created project and follow the instructions that you give in the ReadMe file. Optimally, you do that on your own and another computer (e.g. your colleague's).

  <br>

4. **Write an e-mail to the reproducer** including…  
  4.1. …the paper whose analyses should be reproduced  
  4.2. …a link to your project or an information about where to find all documents necessary to reproduce your analyses  
  4.3. …a short reference to the ReadMe-file telling the reproducer that it should contain all instructions to reproduce your analyses
