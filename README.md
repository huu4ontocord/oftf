# oftf
One File Text Filter

oftf.py allows you to filter text at scale for potentially unwanted text, including noisy text.

For interdocument filtering, such as dedup or removal of duplicate paras or sentences, there is no gurantee that all duplicates will be removed. This is because we keep dictionaries per processes. 

TODO: we can bucketize files and do continued filtering for n-passes.

More documentation to come.
