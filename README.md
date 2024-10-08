# Cybersecurity Analysis: File Permissions in Linux

## Scenario

As part of my **Google Cybersecurity Professional Certificate**, I worked with the research team at my organization to ensure that file and directory permissions were set correctly, maintaining system security. My task was to examine and modify file permissions based on the required authorization levels, ensuring that only authorized users had appropriate access.

---

## Incident Analysis

During the exercise, I used Linux commands to identify the current permissions in the project directory. I ran the `ls -la` command to list all files, including hidden ones, and assess their associated permissions.

| **Command**              | **Description**                                                           |
|--------------------------|---------------------------------------------------------------------------|
| `ls -la`                 | Listed all contents in the directory, including permissions for files and directories. |

The output indicated that some files, such as `project_t.txt`, had unnecessary write permissions for **other users**. I also identified hidden files, such as `.project_x.txt`, that required permission adjustments.

---

## Permissions Breakdown

In Linux, file permissions are represented by a 10-character string. Each part of the string indicates specific permissions for different users:

| **Character**         | **Meaning**                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| 1st character         | `d` for directory, `-` for file.                                             |
| 2nd-4th characters    | User permissions: read (r), write (w), execute (x).                          |
| 5th-7th characters    | Group permissions: read (r), write (w), execute (x).                         |
| 8th-10th characters   | Other (world) permissions: read (r), write (w), execute (x).                 |

For example, the permissions for `project_t.txt` were `-rw-rw-r--`, meaning it was a file with **read/write** access for the user and group, and **read-only** access for others.

---

## Modifying Permissions

After reviewing the permissions, I used the **chmod** command to adjust the file and directory permissions according to the organization’s security policies. Here are the steps I took:

### 1. Remove Write Access from Others

The organization wanted to ensure that **other users** could not modify certain files. I used the following command to remove write access from the file `project_k.txt`:

| **Command**              | **Description**                                                           |
|--------------------------|---------------------------------------------------------------------------|
| `chmod o-w project_k.txt` | Removed write permissions for other users from the file `project_k.txt`.  |

### 2. Change Permissions on a Hidden File

The file `.project_x.txt` was a hidden file, and the research team wanted to ensure that no one had write access. I modified the permissions with the following command:

| **Command**              | **Description**                                                           |
|--------------------------|---------------------------------------------------------------------------|
| `chmod u-w,g-w,g+r .project_x.txt` | Removed write permissions for the user and group, and granted read permissions for the group. |

### 3. Restrict Access to a Directory

For the directory `drafts`, only the **researcher2** user was allowed access. I used the following command to restrict permissions:

| **Command**              | **Description**                                                           |
|--------------------------|---------------------------------------------------------------------------|
| `chmod g-x drafts`       | Removed execute permissions for the group on the `drafts` directory.       |

---

## Summary

This project involved checking and modifying file and directory permissions in a Linux environment to align with the organization's security policies. By using the **ls -la** and **chmod** commands, I was able to ensure that sensitive files and directories had the correct authorization, preventing unauthorized access.

---

## Tools & Technologies Used

| **Tool/Technology**        | **Purpose**                                                      |
|----------------------------|------------------------------------------------------------------|
| **ls -la**                 | Listed file and directory permissions in the project directory.   |
| **chmod**                  | Modified file and directory permissions to meet security requirements. |

---

This hands-on project allowed me to gain valuable experience in managing file permissions and maintaining system security in a Linux environment. It reinforced the importance of proper access controls in ensuring the confidentiality and integrity of sensitive information.
