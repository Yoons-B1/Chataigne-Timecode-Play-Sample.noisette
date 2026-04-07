# Chataigne - Timecode Play - MMC Command - Sample.noisette
> Timecode cue playback sample using DOREMiDi MTC-30 with Chataigne

---

## Overview

This is a sample `.noisette` file for implementing Timecode cue playback using the DOREMiDi MTC-30 in Chataigne.

---

## 1. Why This Was Created

* The MTC-30 supports multiple timecode formats such as:

  * LTC
  * MTC
  * RTP-MIDI / USB-MIDI
  * Art-Timecode

* It also supports **Video Frame Sync (Genlock)**, making it suitable for video playback systems.

* Although it claims to support **MMC (MIDI Machine Control) Standard Commands** for remote control:

  * It is not easy to implement in practice
  * The official MMC Tool works correctly, but is not suitable for cue-based playback

* When testing MMC control in Chataigne:

  * Using **MIDI Module → Templates → MMC Command**
    → Works briefly, then disconnects
  * Using **SysEx Messages only**
    → Causes random connection failures or missed triggers

---

## 2. Solution

* Add an **MMC Command before every trigger**
* Then send the **SysEx Message immediately after**

### Result:

* MMC Command → Restores/maintains connection
* SysEx Message → Executes the actual command

This combination resolves both:

* Connection drop issues
* Missed trigger problems

<img width="2482" height="1541" alt="mtc01" src="https://github.com/user-attachments/assets/b3642634-5ccc-429c-82a6-3dc380619018" />
<img width="2482" height="1541" alt="mtc02" src="https://github.com/user-attachments/assets/66a3568d-8aa2-42ca-8ed9-1c0cdaaffa77" />

---

## 3. How to Use

* All actual commands are implemented via **SysEx Messages**
* Refer to:

  * Message descriptions
  * Attached sample `.noisette` file

---

## 4. MTC-30 Driver & Tool

* https://www.doremidi.cn/h-pd-106.html
  
<img width="332" height="274" alt="mtc0001" src="https://github.com/user-attachments/assets/7f8ce078-c3ec-40cd-8080-537eee214b2f" />

---

## Notes

* This is a practical workaround for stable MMC-based control
* Recommended for systems requiring reliable timecode triggering

---

