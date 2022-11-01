# Loan_Risk_Assessment
**Predict whether the loan will be approved or rejected (Supervised ML)**

## Background
**Dataset Introduction & Problem Statement:** <br>
<div align='justify'>

[Dataset](https://www.kaggle.com/datasets/mirbektoktogaraev/should-this-loan-be-approved-or-denied) yang kami gunakan adalah dataset dari U.S. Small Business Administration (SBA).
SBA merupakan pihak ketiga yang berperan membantu pihak pengusaha kecil di pasar kredit AS melalui program pemberian jaminan yang dirancang agar pihak Bank dapat memberikan pinjaman 
kepada pengusaha kecil. SBA bertindak seperti penyedia asuransi untuk mengurangi risiko pihak Bank dengan menutupi beberapa kerugian melalui sebagian jaminan yang diberikan jika para pengusaha kecil gagal bayar.
Namun karena jaminan yang diberikan SBA hanya sebagian dari seluruh saldo pinjaman, Bank tetap mengalami kerugian jika pihak pengusaha kecil gagal dalam melunasi pinjaman. Oleh karena itu, Bank masih dihadapkan 
pada pilihan yang sulit apakah mereka harus memberikan pinjaman tersebut atau tidak karena harus mempertimbangkan risiko gagal bayar yang masih tinggi walaupun sebagian sudah dijamin oleh pihak SBA.

**Role:** <br>
Disini kami berperan sebagai Tim Data Scientist dari pihak Bank

**Goals:** <br>
Adapun goals yang ingin kami capai adalah meningkatkan efektivitas dalam melakukan review terhadap calon peminjam tanpa menambah cost untuk menambah karyawan, serta meminimalisir risiko adanya pengusaha kecil yang tidak mampu melunasi pinjaman.

**Business Matrics:** <br>
Business Matrics yang kami gunakan sebagai pengukur keberhasilan dari goals yang ingin kami capai adalah Default Rate (rasio gagal bayar dari total pinjaman yang diterima), yakni meminimalisir risiko adanya pengusaha kecil yang tidak mampu melunasi pinjaman.

**Objective:** <br>
Berdasarkan latar belakang yang ada kami bermaksud melakukan analisa pada data historis yang tersedia, untuk membuat Machine Laerning Model yang dapat memprediksi secara otomatis penilaian risiko pinjaman,
apakah pinjaman yang diajukan oleh pengusaha kecil layak untuk disetujui atau ditolak. Sehingga dengan adanya model ini, daily resolved application akan meningkat karena banyak pengajuan yang di-review secara otomatis oleh model, 
serta meminimalisir risiko gagal bayar dari pengusaha kecil sampai kurang dari 6%, perusahaan dikatakan sehat apabila tingkat Non-Performing Loannya kurang dari 6%.

## Data Dictionary
|Variable|Description|
|--|--|
|LoanNr_ChkDgt| Identifier Primary key|
|Name|Borrower name|
|City|Borrower city|
|State|Borrower state|
|Zip| Borrower zip code|
|Bank|Bank name|
|BankState|Bank state|
|NAICS|North American industry classification system code|
|ApprovalDate|Date SBA commitment issued|
|ApprovalFY|Fiscal year of commitment|
|Term|Loan term in months|
|NoEmp|Number of business employees|
|NewExist|1 = Existing business, 2 = New business|
|CreateJob|Number of jobs created|
|RetainedJob|Number of jobs retained|
|FranchiseCode|Franchise code, (00000 or 00001) = No franchise|
|UrbanRural|1 = Urban, 2 = rural, 0 = undefined|
|RevLineCr|Revolving line of credit: Y = Yes, N = No|
|LowDoc|LowDoc Loan Program: Y = Yes, N = No|
|ChgOffDate|The date when a loan is declared to be in default|
|DisbursementDate|Disbursement date|
|DisbursementGross|Amount disbursed|
|BalanceGross|Gross amount outstanding|
|MIS_Status|Loan status charged off = CHGOFF, Paid in full =PIF|
|ChgOffPrinGr|Charged-off amount|
|GrAppv|Gross amount of loan approved by bank|
|SBA_Appv|SBA’s guaranteed amoun bold text of approved loan bold text|



## Methods
Proses yang kami lakukan secara garis besar adalah:
### **1. EDA**
 - Descriptive Statistics
 - Univariate Analysis
 - Multivariate Analysis
### **2. Preprocessing**
 - Data Cleansing
 - Feature Engineering
 - Feature transformation: BoxCox
 - Handle Outliers: Z-Score
 - Standardization
 - Handle class imbalance: over sampling SMOTE
### **3. Modeling** 
Kami mencoba 4 jenis model classification untuk melihat mana yang paling baik dalam memprediksi targer yaitu:
 - Decission Tree
 - Random Forest
 - Adaboost
 - XGBoost

Project ini membutuhkan paket standar numpy, pandas, matplotlib, seaborn, sklearn, imblearn, xgboost. Jadi, Anda mungkin perlu menginstal paket ini jika ingin mengujinya.

## Result
Berikut ini adalah hasil perbandingan model yang kami gunakan:

![image](https://user-images.githubusercontent.com/113230789/199012570-25e5fcb3-504b-4a4a-b11a-3b83b435ca57.png)

Berdasarkan nilai AUCnya, model terbaik dalam memprediksi target adalah model XGBoost. 

Berikut adalah impact yang dihasilkan sebelum dan setelah menggunakan model :
- Sebelum menggunakan model, persentase charge off sebanyak 17% dari 64.484 debitur
- Setelah prediksi menggunakan model persentase charge off menjadi 4.6% dari 53.582 debitur

Sehingga kami berhasil mencapai target awal yakni nilai charge off kurang dari 6%
