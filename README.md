# Lab 1 – Digital Forensics Case Handling, Autopsy and Sleuth Kit Analysis

## About This Project

This repository contains my practical work for Lab 1 of the Computer and Digital Forensics course.

The aim of the practical was to examine the authorised forensic disk image `Ch01InChap01.dd` while following proper digital forensic procedures. The original evidence was protected throughout the investigation, and all analysis was carried out using a verified working copy.

The investigation was completed using both Autopsy and The Sleuth Kit so that the findings could be checked using graphical and command-line forensic methods.

---

## Material Information
**Course:** Computer and Digital Forensics   
**Lab:** Lab 1 – Digital Forensics Case Handling, Autopsy and Sleuth Kit Analysis  

---

## Main Objectives

The practical involved:

- Creating a structured forensic working environment
- Preserving the original evidence image
- Calculating MD5 and SHA-256 hashes
- Creating and verifying a forensic working copy
- Recording evidence handling using a mini chain-of-custody worksheet
- Examining the image with Autopsy
- Identifying deleted files
- Performing keyword searches
- Recovering relevant files
- Examining file metadata and data sectors
- Using The Sleuth Kit for command-line analysis
- Comparing recovered files using hashes
- Examining unallocated space
- Confirming that the recovered spreadsheet could be opened successfully

---

## Tools Used

The main tools used during the practical were:

- Kali Linux
- VMware Workstation
- Autopsy Forensic Browser 2.24
- The Sleuth Kit 4.12.1
- `md5sum`
- `sha256sum`
- `cmp`
- `img_stat`
- `fsstat`
- `fls`
- `istat`
- `icat`
- `blkcat`
- `tsk_recover`
- `blkls`
- `file`
- `strings`
- `grep`
- LibreOffice Calc

---

## Evidence Information

**Evidence Image:** `Ch01InChap01.dd`  
**Image Size:** 1,474,560 bytes  
**Filesystem:** FAT12  

### Original Evidence Hashes

**MD5**

`a117773bcf1fc88ec0ab8e0a349fbbcb`

**SHA-256**

`3ce8053e4f3d9c8ab98b3aadb2480685efb8e4980d34297b83bd5a09b1a7b122`

The original image was made read-only, and a separate working copy was created for analysis. The working copy was compared with the original to confirm that both were identical.

---

## Autopsy Analysis

A forensic case was created in Autopsy and the working copy of the disk image was added as the evidence source.

Autopsy identified the image as a FAT12 volume and successfully verified its MD5 hash.

During file analysis, several deleted files were identified, including:

- `Billing Letter.doc`
- `confirmation.txt`
- `letter1.txt`
- `Regrets.doc`

The file `INCOME.XLS` was also identified and examined in detail.

### INCOME.XLS Details

- Metadata address: `13`
- File size: `13,824 bytes`
- Data sectors: `285–311`
- MD5: `6a2e65afc5af4fc5f9da2859df134eac`

Keyword searches were also carried out for:

- `income`
- `billing`
- `client`

Relevant evidence notes were added for `INCOME.XLS` and the deleted `Billing Letter.doc`, and an Autopsy report was generated.

---

## Sleuth Kit Analysis

The disk image was also examined using The Sleuth Kit command-line tools.

`img_stat` was used to examine the image information, while `fsstat` confirmed the FAT12 filesystem structure.

`fls` was used to list files and identify deleted entries. A recursive deleted-file listing was also performed.

`INCOME.XLS` was independently located with metadata address `13`.

The `istat` command confirmed its metadata, size and data sectors.

---

## File Recovery

`INCOME.XLS` was recovered using several different methods:

1. Autopsy export
2. `icat`
3. `blkcat`
4. `tsk_recover`

The recovered copies were checked using MD5 and SHA-256 hashes.

### Recovered INCOME.XLS Hashes

**MD5**

`6a2e65afc5af4fc5f9da2859df134eac`

**SHA-256**

`8d7cd7204d3dae161a8fa879e184865b3bc4a57a4e688abd522a9ff03f62252d`

The recovered copies were also compared using `cmp`, which confirmed that all four copies were byte-for-byte identical.

---

## Deleted File Recovery

The deleted `Billing Letter.doc` was examined and recovered.

Details recorded during the analysis included:

- Metadata address: `8`
- Status: Not Allocated
- File size: `24,064 bytes`
- Data sectors: `237–283`
- MD5: `9fe241d0dde27e83442010b3eee5ad32`

`tsk_recover` was also used to recover deleted files from the image.

---

## Unallocated Space Examination

`blkls` was used to extract the unallocated space from the forensic image.

The extracted data was then examined using `strings` and `grep` as part of the unallocated-space analysis.

---

## Spreadsheet Examination

The recovered `INCOME.XLS` file was successfully opened in LibreOffice Calc.

The spreadsheet displayed a January Cash Flow worksheet, with worksheet tabs for January, February and March. This confirmed that the recovered spreadsheet was readable and usable.

---

## Repository Contents

The repository contains supporting material from the practical, including:

- Forensic report
- Sleuth Kit command outputs
- Recovered files
- Hash records
- Screenshots
- Investigation notes
- Chain-of-custody information
- Autopsy report
- Terminal logs

---

## Evidence Handling Note

The original `Ch01InChap01.dd` forensic image is not included in this repository.

The original evidence was kept separate and protected during the investigation. Analysis and recovery activities were performed using the verified working copy.

---

## Conclusion

This practical gave me hands-on experience with the main stages of a digital forensic investigation, from protecting and verifying evidence to analysing, recovering and validating files.

Using both Autopsy and The Sleuth Kit made it possible to confirm the findings in more than one way. The deleted files were identified, `INCOME.XLS` was recovered through different methods, and the matching hashes confirmed that the recovered copies were consistent.

The practical also showed the importance of keeping clear records, preserving the original evidence and verifying recovered data throughout an investigation.
