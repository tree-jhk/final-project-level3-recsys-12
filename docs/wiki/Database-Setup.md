# MySQL setup

Historical Windows 10/11, 64-bit setup:

1. Download the MySQL Community installer from [MySQL](https://dev.mysql.com/downloads/windows/installer/). The original version was `mysql-installer-community-8.0.31.0.msi`.
2. Install MySQL Workbench for easier administration, retain port **3306** unless there is a reason to change it, and store credentials securely.

![image](https://user-images.githubusercontent.com/90206705/217547369-71d8be1f-276e-49f1-8e1b-c38a504a4de3.png)

3. Open the local MySQL instance and authenticate.

**Security correction:** The original tutorial suggested a simple shared password for convenience. Do not use this advice for a network-accessible system; the team's later [security incident](Security-Incident.md) illustrates the risk. Use a strong, unique password and restrict access.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%84%A4%EC%A0%95)
