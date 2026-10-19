# Cloud Computing Lab 05: S3 Static Website Hosting (Portfolio - Zayan)

## 1. Architecture Overview
* **Architecture Flow:** Website files (`index.html`, `about.html`, `projects.html`, `style.css`, and images) $\rightarrow$ S3 bucket $\rightarrow$ S3 website endpoint $\rightarrow$ Browser[cite: 1].
* **Core Concepts:** Utilized Amazon S3 as an object storage container where objects are identified by unique object keys and organized using prefixes that mimic folders[cite: 1]. The architecture serves static content without executing server-side code[cite: 1].

## 2. Deployment Steps
1. Signed into the AWS console using an approved IAM identity and navigated to Amazon S3[cite: 1, 2].
2. Created a unique bucket named `cs471-zayan-portfolio-2026` in the designated region with ACL-disabled settings[cite: 1, 2].
3. Prepared and uploaded the local folder structure containing `index.html`, `about.html`, `projects.html`, `style.css`, and the `images/` directory, preserving paths and prefixes[cite: 2, 4].
4. Configured **Static Website Hosting** under bucket properties, setting `index.html` as the index document[cite: 2].
5. Adjusted public access settings and applied an approved resource-based bucket policy granting public read access (`s3:GetObject`)[cite: 2, 3].
6. Performed a live update by modifying `index.html` locally, re-uploading the file, and refreshing the browser endpoint to verify real-time deployment[cite: 3, 4].

## 3. Security & Cost Notes
* **Security Measures:** Ensured the bucket policy was narrowly scoped to grant `s3:GetObject` exclusively, preventing public write, delete, or administrative operations[cite: 3]. Blocked sensitive data upload and verified that no private keys, passwords, or access credentials were exposed[cite: 4].
* **Cost Considerations:** Evaluated S3 Standard storage classes for frequently accessed website files and recognized that enabling versioning introduces additional storage costs over time due to preserved object versions[cite: 1, 3, 4].

## 4. Troubleshooting Log
* **Problem Encountered:** Opening the S3 static website endpoint resulted in an `AccessDenied` error[cite: 2, 3].
* **Diagnosis:** Checked the bucket policy resource ARN, verified object existence, and reviewed public-access safeguards[cite: 3]. S3 object keys and bucket policies are strictly case-sensitive[cite: 3].
* **Fix:** Corrected the resource ARN within the JSON bucket policy to precisely match the bucket name (`arn:aws:s3:::cs471-zayan-portfolio-2026/*`) and confirmed that public read access was successfully enabled[cite: 3].
