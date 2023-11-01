<link rel="stylesheet" type="text/css" href="auto-number-title.css" />
<img src="media/MT_logo.png" align="left" style="zoom:20%;"/>

<br/> 
<br/> 
<br/> 
<br/> 

<font size="7"> **<center>Ping Hu</center>**</font>

<font size="6"> **<center>MP(USC) MOV Design Specification</center>**</font>
<font size="5"> **<center>Revision: 1.5</center>**</font>
<font size="5"> **<center>11/2023</center>**</font>
<br/> 
<br/> 
<font size="3"> **<center>Confidential and for internal use only</center>**</font>
<br/> 
<br/> 
<br/> 
<br/> 
<br/> 
<br/>

<br/> 
<br/> 

<div STYLE="page-break-after: always;"></div>

**Revision History**

| **Date** | **Revision** | **Author** | **Description** |
| -------- | ------------ | ---------- | --------------- |
| 09/2023  | 1.5          | Weikai Jia | First Draft     |
| 11/2023  | 1.6          | Weikai Jia | PH1 edition.    |
|          |              |            |                 |
|          |              |            |                 |
|          |              |            |                 |
|          |              |            |                 |



**Terminology**

| **No.** | **Term** | **Full Name**                   | **Description**                                              |
| ------- | -------- | ------------------------------- | ------------------------------------------------------------ |
| **1**   | DWORD    | double words                    | 32-bit binary data unit.                                     |
| 2       | US       | Unified Store                   | Unified data storage.                                        |
| 3       | FC(CFQ)  | Fence Queue(Common Fence Queue) | FQ in the MPE will send instructions to MOV via the MEBI.    |
| 4       | ICTRL    | Instruction Control             | ICTRL sends ready instructions to FC, FC then send them to MOV. |
| 5       | SHS      | Shared store                    |                                                              |
| 6       | SLS(SR)  | slog registers store            |                                                              |
| 7       | SCHED_TS | scheduler task store            |                                                              |
| 8       | CEU      | Conditional Execution Unit      |                                                              |
| 9       | FC       | Fence Counter                   |                                                              |
| 10      | CFS      | Coefficient Store               |                                                              |
| 11      | PRED     | Predicate Store                 |                                                              |
| 12      | REG      | Register Bank                   |                                                              |