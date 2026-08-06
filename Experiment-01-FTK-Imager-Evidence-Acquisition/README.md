# Experiment 01 – Evidence Acquisition Using FTK Imager

## Aim

To acquire volatile memory (RAM) and non-volatile memory (disk image) using AccessData FTK Imager while maintaining the integrity of digital evidence through hash verification.

---

## Objective

- Learn the fundamentals of digital evidence acquisition.
- Capture volatile memory (RAM) from a live system.
- Create a forensic disk image.
- Verify evidence integrity using cryptographic hash values.
- Understand the role of FTK Imager in digital forensic investigations.

---

## Software Requirements

- AccessData FTK Imager
- Windows 10/11
- Storage device (USB or External HDD)
- Write Blocker (Recommended)

---

## Theory

FTK Imager is a digital forensic acquisition tool developed by AccessData. It allows investigators to create exact forensic copies of storage devices and capture volatile memory without altering the original evidence.

FTK Imager supports the acquisition of:

- Physical Drives
- Logical Drives
- Image Files
- Folder Contents
- CDs/DVDs
- Volatile Memory (RAM)

The acquired evidence can later be analyzed using forensic tools such as FTK, Autopsy, EnCase, or Volatility.

---

## Types of Evidence

### Volatile Evidence

Volatile evidence exists only while a system is powered on.

Examples:

- RAM
- Running Processes
- Network Connections
- Clipboard Data
- Encryption Keys

The captured memory is saved as a `.mem` file.

### Non-Volatile Evidence

Non-volatile evidence remains even after the system is powered off.

Examples:

- Hard Disk Drives (HDD)
- Solid State Drives (SSD)
- USB Flash Drives
- Memory Cards

---

## Supported Image Formats

| Format | Description |
|--------|-------------|
| RAW (.dd) | Standard forensic image format |
| E01 | EnCase compressed forensic image |
| SMART | Linux forensic image format |
| AFF | Advanced Forensic Format |

---

# Procedure

## Part A – Volatile Memory Acquisition

### Step 1

Open **FTK Imager**.

### Step 2

Click **Capture Memory**.

### Step 3

Choose the destination folder.

Optional:

- Include Pagefile
- Include AD1 File

### Step 4

Click **Capture Memory**.

FTK Imager creates a memory image with the `.mem` extension.

---

## Part B – Disk Imaging

### Step 1

Select:

```
File → Create Disk Image
```

### Step 2

Choose the source type.

Example:

- Physical Drive
- Logical Drive

### Step 3

Select the drive to acquire.

### Step 4

Enter Case Information.

- Case Number
- Evidence Number
- Examiner Name
- Notes

### Step 5

Choose the image destination.

Specify:

- Image File Name
- Destination Folder
- Fragment Size

Set **Fragment Size = 0** to create a single image file.

### Step 6

Enable:

```
Verify images after they are created
```

### Step 7

Click **Start** to begin acquisition.

### Step 8

After completion, FTK Imager generates:

- Image File
- Acquisition Log
- MD5/SHA1 Hash Values

---

## Result

Successfully acquired both volatile memory and a forensic disk image using FTK Imager. The generated hash values matched during verification, confirming the integrity and authenticity of the acquired evidence.

---

## Advantages

- Free forensic acquisition tool
- Easy to use
- Supports multiple image formats
- Generates cryptographic hash values
- Preserves evidence integrity

---

## Applications

- Digital Forensics
- Incident Response
- Malware Analysis
- Cyber Crime Investigation
- Corporate Security Investigations

---

## Precautions

- Use a write blocker whenever possible.
- Never analyze the original evidence directly.
- Verify hash values after acquisition.
- Store acquired evidence securely.
- Record case details accurately.

---

## Conclusion

This experiment demonstrated how FTK Imager is used to acquire both volatile and non-volatile digital evidence while preserving forensic integrity. Hash verification confirmed that the acquired image was an exact copy of the original source, making it suitable for further forensic analysis.

---

## References

1. AccessData FTK Imager Documentation
2. NIST Guidelines on Digital Forensics
3. Carrier, B. *File System Forensic Analysis*
