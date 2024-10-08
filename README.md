

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
- [Resources](#-resources)

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
wget https://www.dropbox.com/s/1q4f0fowo8048mq/Image1.7z?dl=0

```
or 
```bash
curl -O https://www.dropbox.com/s/1q4f0fowo8048mq/Image1.7z?dl=0
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
  <img src="https://github.com/user-attachments/assets/440498f0-2855-4181-8293-ecc36c80170c" alt="AFF Info Output" />
</p>

### 2. Extract Files

After downloading, extract the compressed files:

```bash
# Extract .7z file
7z x Image1.7z
```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/dc7a1bcc-ac36-4c93-8585-d7d4f554557d" alt="AFF Info Output" />
</p>
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/967f3ffc-fc6e-4804-8262-b1fecd1f75bc" alt="AFF Info Output" />
</p>

### 3. Apply Commands

Now, apply the necessary commands to the extracted files:

- **View Content of .txt File**:

    ```bash
    cat HRServer_Disk0.txt
    ```

<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/7188fc14-8c52-422b-9973-db3013d18b39" alt="AFF Info Output" />
</p>
<br>
<br>

- **Generate MD5 Hash**:
   Calculates the MD5 hash of the image file to verify its integrity

    ```bash
    md5sum HRServer_Disk0.e01
    ```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/e4aa3cf3-828a-440d-a00c-661910d30f9c" alt="AFF Info Output" />
</p>
<br>
<br>


- **Generate SHA1 Hash**:
   Calculates the SHA1 hash of the image file for additional integrity verification

    ```bash
    sha1sum HRServer_Disk0.e01
    ```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/6b44a654-36cc-463f-b359-f8390562e614" alt="AFF Info Output" />
</p>
<br>
<br>

- **Get MMLS (Media Management Layer Statistics)**:
   Lists the partitions and their details within the image file.
   

    ```bash
    mmls HRServer_Disk0.e01 
    ```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/88bc9823-59f0-4664-9c25-b3c0159cc1ef" alt="AFF Info Output" />
</p>
<br>
<br>

 **Note** : from image the offset `0001026048`


- **Get Image Statistics**:
   Provides detailed statistics about the image file, such as size and format.

    ```bash
    img_stat HRServer_Disk0.e01
    ```
<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/02d03b74-99c5-4ee3-88bb-d5f254df469b" alt="AFF Info Output" />
</p>
<br>
<br>

- **Get File System Statistics**:
  Displays file system details, including the type and size of the file system.10

    ```bash
    fsstat -o 1026048 HRServer_Disk0.e01
    ```
<br>
<br>
<p align="center">

https://github.com/user-attachments/assets/c5e0db33-12c4-4c54-bc15-db65d7db6d81

</p>
<br>
<br>

- **List File and Directory Names**:
   Lists files and directories within the file system, showing their metadata.

    ```bash
    fls -o 1026048 HRServer_Disk0.e01
    ```
<br>
<br>
<p align="center">

https://github.com/user-attachments/assets/a55f085c-ca01-4198-b861-6f5356cdce8b

</p>
<br>
<br>

- **List Inode Entries**:
   Lists inode entries, showing metadata for each inode in the file system.

    ```bash
   ils -o 1026048 HRServer_Disk0.e01
    ```
<br>
<br>
<p align="center">

https://github.com/user-attachments/assets/8ff8e909-874b-4af6-92e5-15fbf8746662

</p>
<br>
<br>



- **Get Inode Metadata**:
   Lists inode entries, showing metadata for each inode in the file system.
**Note** : indo number from ils for example `172624`
    ```bash
   istat -o 1026048 HRServer_Disk0.e01 172624
    ```
<br>
<br>
<p align="center">

https://github.com/user-attachments/assets/9d06c963-7bda-45b5-b5a0-76d1a88730b6

</p>
<br>
<br>

- **Recover Deleted Files**:
 Recovers deleted files from the image and saves them to the specified output directory.

    ```bash
   tsk_recover -o 1026048 HRServer_Disk0.e01  recover
    ```
<br>
<br>
<p align="center">

<img src="https://github.com/user-attachments/assets/58e14cd5-f6c3-4143-82f7-9187b9e81d19" alt="AFF Info Output" />

</p>
<br>
<br>

- **Get Block Statistics**:
 Provides statistics about a specific block within the image.
**Note** : block number from ils for example `172624`
    ```bash
   blkstat -o 1026048 HRServer_Disk0.e01 172624
    ```
<br>
<br>
<p align="center">

<img src="https://github.com/user-attachments/assets/dcfc79df-6a49-43a1-9a14-586beb8b606b" alt="AFF Info Output" />

</p>
<br>
<br>

- **Extract Raw Block Data**:
Extracts raw block data from the image and saves it to the specified output directory.

    ```bash
  blkls -o 1026048 HRServer_Disk0.e01 

    ```
<br>
<br>
<p align="center">

<img src="https://github.com/user-attachments/assets/ec36c2cf-f9a5-4c6e-86aa-1580def4bb5b" alt="AFF Info Output" />

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


