Both CI checks now pass locally and are pushed:
nbfmt  ✓  examples/legal-ai/Legal_Document_Analysis_with_Gemini.ipynb
nbfmt  ✓  examples/github-api/GitHub_API_with_Gemini.ipynb

nblint ✓  gemini_cookbook::copyright_check
nblint ✓  gemini_cookbook::license_check
nblint ✓  gemini_cookbook::button_colab
nblint ✓  google::second_person
nblint ✓  google::inclusive_language
       ... (all 10 checks pass for both notebooks)
Root cause: the CLAUDE.md had the wrong lint style (--styles=google,tensorflow). The actual CI uses --styles=google,gemini_cookbook, which has a different button_colab regex that accepts colab-badge.svg. Also needed: a standalone ##### Copyright markdown cell as cell 0 (the license code cell alone doesn't satisfy the copyright check) and the badge in its own dedicated cell.
