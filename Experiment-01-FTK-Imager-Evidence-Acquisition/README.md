# Experiment 01: Evidence Acquisition Using AccessData FTK Imager

**Date:** 

---

## Description

**Forensic Toolkit (FTK)** is a computer forensics software product developed by AccessData. It is a Windows-based commercial product. For forensic investigations, the development team has created a free version of the commercial product with fewer functionalities, known as **FTK Imager**. This tool is capable of both acquiring and analyzing computer forensic evidence.

The evidence that FTK Imager can acquire is split into two main categories:
1. **Volatile Memory (RAM):** Data that is lost when the computer powers down.
2. **Non-Volatile Memory (Hard Disk):** Persistent data stored on storage media.

There are two primary deployment methods for FTK Imager in forensic acquisitions:
* **Portable Version:** Run directly from a USB pen drive or external HDD on the target machine. This is most frequently used in live data acquisition where the evidence machine is powered on.
* **Installed Version:** Installed on the investigator's machine. In this scenario, the source disk is connected to the investigator's laptop via a **Write Blocker**. The write blocker prevents data modification on the source media while providing read-only access, maintaining the integrity of the evidence.

---

## Part A: Acquiring Volatile Memory (RAM)

FTK Imager enables investigators to capture the complete volatile memory (RAM) of a computer.

### Step-by-Step Procedure
1. Open **FTK Imager**.
2. Navigate to the top toolbar and click the volatile memory icon (**Capture Memory**).
3. Specify the destination path and options in the dialog.
4. Click **Capture Memory** to begin the acquisition.

> [!NOTE]
> Once the acquisition is complete, the destination folder will contain the acquired memory dump with a `.mem` file extension.

### Memory Capture Options

* **Include Pagefile:** The pagefile (`pagefile.sys`) is used by Windows as an extension of physical RAM when memory capacity is exceeded. It is located under the `C:` partition. Because it contains page-outs of memory, it can store valuable forensic artifacts. Capturing the pagefile alongside RAM is highly recommended.
* **Create AD1 File:** AD1 is an AccessData proprietary logical evidence file format. Investigators can choose to package the captured memory inside an AD1 container for consolidated storage and metadata retention.

---

## Part B: Acquiring Non-Volatile Memory (Disk Image)

FTK Imager is also used to acquire exact bit-stream copies of physical or logical drives.

### Step-by-Step Procedure
1. Open **FTK Imager** and navigate to **File** ➔ **Create Disk Image**.
2. Choose the source type to acquire:
   * **Physical Drive:** The entire hardware drive.
   * **Logical Drive:** Specific partitions/volumes.
   * **Image File:** Converting or cloning an existing image.
   * **Contents of a folder:** Logical file acquisition.
   * **CDs/DVDs:** Optical media.
3. Select the source drive/media and click **Finish**.
4. Enter the **Case Details** (Case Number, Evidence Number, Unique Description, Examiner, Notes).
5. Add an **Image Destination**:
   * Choose the destination folder and name the image file.
   * Specify the **Image Fragment Size (MB)**. If you want a single file instead of multiple split images, set this value to `0`.
   * Check **Verify images after they are created**.
6. Click **Start** to begin the process.

---

## Supported Forensic Image Formats

| Format | Name | Details & Forensic Characteristics |
| :--- | :--- | :--- |
| **RAW** | Raw (dd) | Bit-stream image copy without metadata, headers, or magic values. Spatial integrity is maintained by padding unreadable ranges (e.g., bad sectors). |
| **SMART** | SMART | Designed for Linux file systems. Consists of a standard 13-byte header followed by sections with size, offsets, CRC, and optional compression. |
| **E01** | EnCase | Proprietary format by Guidance Software. Compresses data and embeds case details (examiner name, date, description) and an MD5 hash of the bit-stream. |
| **AFF** | Advanced Forensic Format | Open-source format (typically AFF4) designed to prevent vendor lock-in. Supports metadata, compression, and signing. |

---

## Image Verification

* **Verify images after they are created:** Checking this option computes cryptographic hashes (MD5 and SHA-1) of the destination image and compares them to the source hashes. 
* A successful match guarantees that the forensic image is a perfect, unaltered copy of the original media.
* FTK Imager generates a summary text report (`.txt`) at the end of the acquisition containing execution logs and verified hash values.

---

## Conclusion
Through this experiment, we successfully acquired both volatile memory (RAM) and a non-volatile disk image using AccessData FTK Imager. Integrity was verified using MD5 and SHA-1 hashing, ensuring the authenticity of the evidence for judicial presentation.
