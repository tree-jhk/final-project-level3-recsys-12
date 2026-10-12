# Database security incident during development

## What happened

The team had deployed MySQL through GCP Cloud SQL. During development, the database stopped working as expected. Inspecting its tables revealed a ransom message.

<img src="https://user-images.githubusercontent.com/67851701/217970899-9e308722-fa64-48dd-8dd3-8d916e232003.JPG" width="800">

<img src="https://user-images.githubusercontent.com/67851701/217971080-c7f3e5fe-5d60-4311-a2f2-5721c1cfc3ef.JPG" width="800">

<img src="https://user-images.githubusercontent.com/67851701/217971139-a5b80924-6126-4c16-8a2b-b58a247ec875.JPG" width="800">

The attacker demanded **0.25 BTC**, reported at the time as approximately KRW 7–8 million. Backups existed and the team reported that no personal data was stored at that stage. It deleted the affected database and investigated before recreating it.

## Identified weaknesses

The team studied secure coding, including a [Python secure-coding guide](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/files/10702722/Python_._.pdf).

### Unrestricted network access

To accommodate remote teammates working from different places, the database had been made accessible from all IP addresses. This also exposed it to attackers.

<img src="https://user-images.githubusercontent.com/67851701/217992803-681f6288-ea2c-41d5-b15b-97ae36968300.png" width="400">

**Warning translation:** Adding `0.0.0.0/0` permits every IPv4 client—including unintended clients—to pass the network firewall and attempt an instance login, although valid credentials are still required. The form shows a network named 'ALL'; it documents the insecure historical configuration, not a recommended setup.

### Weak password

The team had reused a trivial local-development password for a remotely accessible database.

<img src="https://user-images.githubusercontent.com/67851701/217993196-4df2f6b1-bba0-4a03-bb79-e09706d39543.png" width="">

**Form labels:** 'Instance information', 'Instance ID', 'Password', and 'Set the root user's password.' The screenshot illustrates the weak historical password choice described above; it is not a current credential or a recommended configuration.

## Response

Restrict database access to the deployment server's IP and replace the weak password with a securely generated password. The original note reported stable operation afterward, while recognizing that other vulnerabilities still needed attention.

## SQL injection precautions

The early login flow accepted email input, creating another potential attack surface. The team added email-format checking:

<img src="https://user-images.githubusercontent.com/67851701/217995409-2e11877f-071b-4154-8646-90dfccf340dd.png" width="800">

The original note also discussed protecting raw SQL queries. The retained screenshot, however, shows Python string interpolation before execution, not safe parameter binding:

<img src="https://user-images.githubusercontent.com/67851701/217996270-30555823-bda8-4980-857d-1584d2a3b5c8.png" width="800">

**Clarification:** Input-format validation is not a substitute for parameterized queries. ORM use is not an unconditional guarantee against injection; safe query construction still matters. The original authors themselves noted that the workaround deserved a safer follow-up.

## Lessons and planned prevention

Inspecting each attack surface manually does not scale. The team explored automated static/security checks during CI and proposed a Jenkins-based redesign; this was **future work**, not a completed pipeline. Secure coding and access control remained essential.

The original page contains seven figures; all are retained. Monetary conversions and operation claims describe the historical incident, not the present service.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/%EA%B0%9C%EB%B0%9C-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EA%B0%80-%ED%95%B4%ED%82%B9%EB%8B%B9%ED%96%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
