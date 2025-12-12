# Objectives

- Examine metadara and watermark information of a file to help determine who created it.
- Differentiate between overt, contextual and hidden markers that could be present in a file.
  
**Task 1: Quick Search for Classified Data**
I learned to:

- Use grep with Perl-style regular expressions
- Search both text and binary files
- Perform case-insensitive searches

Identify true positives vs. false positives in data classification

Understand the difference between filename metadata and file contents

## Tools Used

- Linux command line

- grep (with -P, -a, -i, -l flags)
- Mounted CD-ROM/ISO filesystem
- LibreOffice Writer (to open .doc files)

## Commands Executed
1. Navigate to the mounted ISO directory
cd /media/sec401/CDROM

2. Search for sensitive keywords inside all files
grep -PaIl '(secret|confidential|sensitive)' *

## Flag Breakdown
Flag	Meaning
-P	  Enables Perl-style regex (allows `secret
-a	  Search binary files as if they were text
-i	  Case-insensitive search
-l	  Print only filenames containing a match

Searches for:

- secret
- confidential
- sensitive
(acting as logical OR conditions)

## Result

Merger Offer Letter to Beta Industries.doc was the only file containing sensitive keywords.

## Why Other Files Didn’t Match

grep searches inside file contents, not filenames.

Example: Secret_Lair_HQ.png contains “Secret” only in its name, not inside the file data.

## Analysis

The .doc file contains “CONFIDENTIAL” and “sensitive,” making it a true positive.

**This demonstrates how keyword searches help classify sensitive documents.**

## Conclusion

This lab reinforces using grep to locate potentially sensitive information, evaluate results for accuracy, and distinguish real classified data from false positives.


# Task 2: Manual Document Review

## Steps Taken

= Opened a pdf file in the PDF viewer.
- Performed a manual visual review for classification labels.
- Used the built-in search function to locate the keywords:

secret
confidential
sensitive

Documented whether the keywords appeared and whether the content represented sensitive data.

## Findings

The PDF includes the terms “secret” and “confidential”, indicating the presence of sensitive business information.

This is a true positive: the document should be treated as classified.

The file did not appear in earlier grep searches because PDF text may be compressed, encoded, or stored in formats unreadable to simple string-search tools.

**Why grep Failed to Detect the PDF** 

PDF text is not always stored as plaintext. Text may be encoded, compressed, or embedded in objects.Tools like grep can only search raw bytes, not rendered document text.
Therefore, manual review is required for accurate data classification.

## Conclusion

Automated detection tools have limitations.
Analysts must supplement them with manual document review to identify sensitive data in formats like PDFs that use non-plaintext text encoding.


# Task 3: Analyze Watermarks and File Metadata
