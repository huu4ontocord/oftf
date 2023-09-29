# oftf
One File Text Filter

oftf.py allows you to filter text at scale for potentially unwanted text, including noisy text.

For interdocument filtering, such as dedup or removal of duplicate paras or sentences, there is no gurantee that all duplicates will be removed. This is because we keep dictionaries per processes. 
```
usage: oftf.py [-h] [-input_dir INPUT_DIR] [-output_dir OUTPUT_DIR] [-num_jobs NUM_JOBS] [-buffer_size BUFFER_SIZE] [-min_text_len MIN_TEXT_LEN] [-lang LANG] [-dedup_window DEDUP_WINDOW] [-cleanup_header_footer_len CLEANUP_HEADER_FOOTER_LEN]
               [-cleanup_num_header_footer CLEANUP_NUM_HEADER_FOOTER] [-cleanup_header_footer_agressive CLEANUP_HEADER_FOOTER_AGRESSIVE] [-cleanup_dup_para_len CLEANUP_DUP_PARA_LEN] [-sentence_ratio SENTENCE_RATIO] [-stopword_score_cutoff STOPWORD_SCORE_CUTOFF]
               [-junk_char_score_cutoff JUNK_CHAR_SCORE_CUTOFF] [-ngram_cutoff NGRAM_CUTOFF] [-force_overwrite FORCE_OVERWRITE] [-flagged_score_cutoff FLAGGED_SCORE_CUTOFF] [-hate_score_cutoff HATE_SCORE_CUTOFF] [-banned_score_cutoff BANNED_SCORE_CUTOFF]
               [-english_stopwords_header_ratio ENGLISH_STOPWORDS_HEADER_RATIO]

optional arguments:
  -h, --help            show this help message and exit
  -input_dir INPUT_DIR  the directory where the input jsonls are stored
  -output_dir OUTPUT_DIR
                        the directory where the output jsonls are stored
  -num_jobs NUM_JOBS    the number of jobs
  -buffer_size BUFFER_SIZE
                        buffer for document reading for multiprocessing
  -min_text_len MIN_TEXT_LEN
                        minimum document length in chars
  -lang LANG            the expected language of the documents
  -dedup_window DEDUP_WINDOW
                        use the first N chars and the last N chars to do exact dedup
  -cleanup_header_footer_len CLEANUP_HEADER_FOOTER_LEN
                        lines above this length that are repteated will be filtered out. lines below this length that are repeated >= 20 times are also filtered
  -cleanup_num_header_footer CLEANUP_NUM_HEADER_FOOTER
                        remove repetitive sentences or linnes in the header or footer within the first or last N sentences
  -cleanup_header_footer_agressive CLEANUP_HEADER_FOOTER_AGRESSIVE
                        whether to remove everything beffore the repeated line in the header and everything after the repeated line in the footer
  -cleanup_dup_para_len CLEANUP_DUP_PARA_LEN
                        minimum para length required before deciding to remove this paragraph as repetitive
  -sentence_ratio SENTENCE_RATIO
                        ratio of sentence to all chars cutoff for first 200 words
  -stopword_score_cutoff STOPWORD_SCORE_CUTOFF
                        ratio of stopwords to non-stopwords cutoff for first 200 words
  -junk_char_score_cutoff JUNK_CHAR_SCORE_CUTOFF
                        ratio of special chars to all words for first 200 words
  -ngram_cutoff NGRAM_CUTOFF
                        ratio repeated n grams to all words cutoff for first 200 words
  -force_overwrite FORCE_OVERWRITE
                        overwrite existing processed files
  -flagged_score_cutoff FLAGGED_SCORE_CUTOFF
                        cutoff proportion of flagged words
  -hate_score_cutoff HATE_SCORE_CUTOFF
                        cutoff proportion of hate words
  -banned_score_cutoff BANNED_SCORE_CUTOFF
                        cutoff proportion of banned words
  -english_stopwords_header_ratio ENGLISH_STOPWORDS_HEADER_RATIO
                        cutoff of ratio of english stopwords in the header
```
TODO: we can bucketize files and do continued filtering for n-passes.

More documentation to come.
