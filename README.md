

<h1 align="center">📂 SleuthKit Ubuntu </h1>

<p align="center">
    This repository contains a demonstration of applying various commands to image files . Below are detailed steps, commands, and the expected results with images.
</p>

---

## 📋 Table of Contents
- [Project Overview](#-project-overview)
- [Prerequisites](#-prerequisites)
- [Setup Project Directory](#-setup-project-directory)
- [Steps](#-steps)
  - [1. Download Required Files](#1-download-required-files)
  - [2. Extract Files](#2-extract-files)
  - [3. Apply Commands](#3-apply-commands)
  - [4. Verify Results](#4-verify-results)
- [Expected Output](#-expected-output)
- [Resources](#-resources)
- [Notes](#-notes)

---

## 🔍 Project Overview

This project focuses on digital forensics, where a forensic image is downloaded, analyzed, and processed using several tools from the Sleuth Kit. The main goal is to extract valuable information from the image, such as file system details, inode data, and deleted files, to simulate a real-world forensic investigation. 

The steps include downloading the image, verifying its integrity through hash functions, and applying multiple commands to analyze its content. The tools used in this project enable the extraction of file system metadata, recovery of deleted files, and a detailed breakdown of blocks and inodes within the image. This analysis helps in understanding the structure and contents of the image in a forensic context.


---

## 🛠 Prerequisites

Ensure the following tools are installed:

- **Linux OS** (Ubuntu recommended)
- **Packages**: `gzip`, `tar`, `afflib-tools` , `build-essential`, `libtool`, `autoconf`, `automake`, `git`, `libewf-dev`, `sleuthkit`, `afflib3`, `libssl-dev`, `libvmdk-dev`, `libvslm-dev`

You can install them using:

### gzip tar afflib-tools
```bash
sudo apt update
sudo apt install gzip tar afflib-tools
```
### build-essential libtool autoconf automake git libewf-dev
```bash
sudo apt install build-essential libtool autoconf automake git libewf-dev
```
### build-essential libtool autoconf automake git libewf-dev
1. Download sleuthkit from github
```bash 
git clone https://github.com/sleuthkit/sleuthkit.git
```

2. Start install requirement by using script bootstrap.sh
```bash 
./bootstrasp
or
sh bootstrap.sh
```
3. checking all needed requirement for installing sleuthkit
```bash 
./configure
```

### afflib3 (to support image of type “.aff”)
    
1. Download sleuthkit from github
```bash 
git clone https://github.com/sshock/AFFLIBv3.git
```
    
2. Start install requirement by using script bootstrap.sh
```bash 
./bootstrasp
or
sh bootstrap.sh
```
    
3. checking all needed requirement for installing AFFLIB3
```bash 
./configure
```
### libssl-dev (missing library for AFFLIB3)
1. install 
```bash 
sudo apt install libssl-dev
```
2. checking all needed requirement for installing AFFLIB3
```bash 
./configure
```
**pass**

3. go to AFFLIB3 directory
```bash 
cd AFFLIB3
```

4. make to billd
```bash 
make
sudo make install
```
5. go out then go to sleurhkit directory
```bash 
cd
cd sleurhkit
```
6. checking all needed requirement for installing sleurhkit
```bash 
./configure
```
**sleuthkit now supports afflib**

### sleuthkit supports all type of images
```bash 
cd
sudo apt install libvhdi-dev libvmdk-dev libvslm-dev
cd sleurhkit
./configure
```
after that 
```bash
make
sudo make install
```
Check images that sleuthkit support
```bash
mmls –i list
```
<p align="center">
  <img src="https://github.com/user-attachments/assets/7f7de936-e4d7-4263-9a28-3700acd4a8b9" alt="AFF Info Output" />
</p>

---

## 📁 Setup Project Directory

First, create a dedicated directory for this project:

```bash
cd Documents/
cd GitHub/
git clone https://github.com/batooldshilleh/SleuthKit-Ubuntu.git
ls
cd SleuthKit-Ubuntu/
```

This directory will store all the downloaded files and the results of applied commands.
<p align="center">
  <img src="https://github.com/user-attachments/assets/0bcc5e25-0f34-43fd-aa44-c38cf4b31ca4" alt="AFF Info Output" />
</p>


---

## 📝 Steps

### 1. Download Required Files

Download the necessary files using the commands below:

```bash
wget https://linuxleo.com/Files/gptimage.raw.gz
wget https://dftt.sourceforge.net/test10/index.html
wget https://linuxleo.com/Files/able2.tar.gz
wget https://digitalcorpora.s3.amazonaws.com/corpora/drives/nps-2009-ntfs1/ntfs1-gen1.aff
```
or 
```bash
curl -O https://linuxleo.com/Files/gptimage.raw.gz
curl -O https://dftt.sourceforge.net/test10/index.html
curl -O https://linuxleo.com/Files/able2.tar.gz
curl -O https://digitalcorpora.s3.amazonaws.com/corpora/drives/nps-2009-ntfs1/ntfs1-gen1.aff
```
**Note** :
### Difference between `wget` and `curl`:

- **`wget`**:
  - Specialized in **downloading files** from the internet.
  - Easy to use for direct file downloads.
  - Can resume downloads if the connection is interrupted.
  - Useful for downloading entire websites.

- **`curl`**:
  - A **multi-purpose tool** for server communication.
  - Can download, upload files, and send data over the network.
  - Flexible in handling REST APIs and complex HTTP requests.
  - Requires additional setup for resuming downloads.

**In short**:
- Use `wget` if you need simple file downloads.
- Use `curl` if you need more flexibility or to interact with REST APIs.
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/d147db9c-997d-4932-b182-061e2a74c490" alt="AFF Info Output" />
</p>
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/8d221922-6dcf-471d-b8fd-34a6bba3311e" alt="AFF Info Output" />
</p>
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/06811447-34f6-452e-8bdb-a70424f32329" alt="AFF Info Output" />
</p>
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/984a1c3c-776d-4732-a3a1-faa0d19246b4" alt="AFF Info Output" />
</p>
<br>

### 2. Extract Files

After downloading, extract the compressed files:

```bash
# Extract .gz file
gzip -d gptimage.raw.gz

# Extract .tar.gz file
tar -xzvf able2.tar.gz
```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/afd4df9c-4fea-463d-907c-6ffe73f5f305" alt="AFF Info Output" />
</p>
<br>

### 3. Apply Commands

Now, apply the necessary commands to the extracted files:
<br>
__**10-ntfs-disk.dd**__
- **To list the partitions on an NTFS disk image:`**:

    ```bash
    cd 10b-ntfs-autodetect/
    ls
    cd 10b-ntfs-autodetect/
    mmls 10-ntfs-disk.dd
    ```

<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/03f8552b-83dd-4f64-a639-f580ff1cf951" alt="AFF Info Output" />
</p>
<br>
<br>


- **To get the statistics of a disk image:**

    ```bash
    img_stat 10-ntfs-disk.dd
    ```

<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/7c77a4c2-0ab1-4f19-ac0d-0ec3c44683e7" alt="AFF Info Output" />
</p>
<br>
<br>

- **To display the metadata statistics of a disk image**:

    ```bash
   mmstat 10-ntfs-disk.dd
    ```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/71fbcd82-1dcd-4e86-9ad2-26d628d61089" alt="AFF Info Output" />
</p>
<br>
<br>

- **To display file system statistics for a specific offset in an NTFS disk image**
 ```bash
   fsstat -o 63 -f ntfs 10-ntfs-disk.dd
 ```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/3ee9730f-a83f-4956-8605-d4a47b9f5f63" alt="AFF Info Output" />
</p>
<br>
<br>

__**gptimage.raw.gz**__

- **To list the partitions on an NTFS disk image:`**:

    ```bash
    # back to main dir
    cd .. / ..
    ls
    mmls gptimage.raw.gz
    ```

<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/0a9edf3f-1402-47a3-9cc7-b2b5a9d837d0" alt="AFF Info Output" />
</p>
<br>
<br>

- **To get the statistics of a disk image:**

    ```bash
    img_stat gptimage.raw
    ```

<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/70baf6a2-4746-4f2a-9b59-7bdbbe16a094" alt="AFF Info Output" />
</p>
<br>
<br>

- **To display the metadata statistics of a disk image**:

    ```bash
   mmstat gptimage.raw
    ```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/24b95f3e-0113-4962-b64c-691e3802e926" alt="AFF Info Output" />
</p>
<br>
<br>

- **To display file system statistics for a specific offset in an NTFS disk image**
 ```bash
   fsstat -o 2048 gptimage.raw
 ```
<br>
<br>
<p align="center">
  
https://github.com/user-attachments/assets/904da836-42ff-4bd6-938e-a98c1053016f

</p>
<br>
<br>

__**able2.dd**__
- **To list the partitions on an NTFS disk image:`**:

    ```bash
    ls
    mmls able2.dd
    ```

<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/84de8e25-5b54-4fa2-9a99-289ade8d8915" alt="AFF Info Output" />
</p>
<br>
<br>

- **To get the statistics of a disk image:**

    ```bash
    img_stat able2.dd
    ```

<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/ed8a9fdb-1185-4703-a437-46d47c32db77" alt="AFF Info Output" />
</p>
<br>
<br>

- **To display the metadata statistics of a disk image**:

    ```bash
   mmstat able2.dd
    ```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/b95b7ac9-7490-4002-b5a2-d1a9d3e9c2df" alt="AFF Info Output" />
</p>
<br>
<br>

- **To display file system statistics for a specific offset in an NTFS disk image**
 ```bash
   fsstat -o 57 able2.dd
 ```
<br>
<br>
<p align="center">
    
https://github.com/user-attachments/assets/d67dccca-2c29-4756-af19-66041761350a

</p>
<br>
<br>

__**ntfs1-gen1.aff**__
- **To get the statistics of a disk image:**

    ```bash
     ls
    img_stat ntfs1-gen1.aff
    ```

<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/0491574a-8da7-4215-9d84-225709ff15ad" alt="AFF Info Output" />
</p>
<br>
<br>

- **To display the metadata statistics of a disk image**:

    ```bash
   fls -o 0 ntfs1-gen1.aff
    ```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/56a59370-c618-41b7-b193-db01d48dc9bd" alt="AFF Info Output" />
</p>
<br>
<br>

- **To display file system statistics for a specific offset in an NTFS disk image**
 ```bash
   fsstat -o 0 ntfs1-gen1.aff
 ```
<br>
<br>
<p align="center">
    
https://github.com/user-attachments/assets/2bb7ce23-60cf-409f-8746-2b18741bd85d

</p>
<br>
<br>

---

## 📚 Resources
- [Sleuth Kit Documentation](https://www.sleuthkit.org/sleuthkit/docs.php) - Official documentation for Sleuth Kit tools used for forensic analysis.
- [Linux Commands Reference](https://man7.org/linux/man-pages/) - Linux command manual for executing commands in the terminal.
- [7-Zip](https://www.7-zip.org/) - Tool used to extract the compressed image file.
- [Dropbox](https://www.dropbox.com/) - Platform used to download the forensic image.
- [Digital Forensics Wiki](https://forensicswiki.xyz/) - A community-driven resource for digital forensics information and best practices.
- [MD5 Hash Calculator](https://emn178.github.io/online-tools/md5_checksum.html) - Online tool to verify MD5 hashes.
- [SHA1 Hash Calculator](https://emn178.github.io/online-tools/sha1_checksum.html) - Online tool to verify SHA1 hashes.


