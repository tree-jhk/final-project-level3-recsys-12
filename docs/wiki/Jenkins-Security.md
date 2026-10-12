# Planned security analysis with Jenkins

## Motivation

After the [security incident](Security-Incident.md), the team recognized that manually tracking every vulnerability would become difficult as the application grew. It explored checking code before integration and automating those checks.

The project **did not have a deployed CI/CD pipeline** at the time. GitHub Actions had been considered; Jenkins was investigated as an automation server for a future redesign.

## Jenkins

<img src="https://user-images.githubusercontent.com/67851701/218297097-bb10640b-55df-4079-9ba2-dbfff182477c.png" width="">

Jenkins supports integration/deployment automation and many plugins.

## PMD and SpotBugs

<img src="https://user-images.githubusercontent.com/67851701/218297515-a59ab5f5-1527-4fab-b431-d1eaf0c1a9e5.png" height="150">

<img src="https://user-images.githubusercontent.com/67851701/218297527-4e20f66d-667e-4a74-adfe-18b0c44dca41.png" height="150">

The team investigated PMD and SpotBugs for code-quality/security checks and severity-based findings. These primarily targeted Java, so a suitable Python approach was still needed.

## Python and next steps

<img src="https://user-images.githubusercontent.com/67851701/218298136-6c6b576b-2e03-40d5-90d4-90cb5833ff1a.png" width="400">

The original exploration mentioned **Pylint** and **RATS**. Their suitability and coverage would need evaluation; mentioning tools is not evidence that they detect all security weaknesses or were integrated into CI.

The takeaway was to choose tools for the actual language and purpose while keeping secure coding, maintainability and developer responsibility central.

[Original reference](https://www.itworld.co.kr/news/107527)


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Jenkins%EC%99%80-%ED%95%A8%EA%BB%98%ED%95%98%EB%8A%94-%EC%B7%A8%EC%95%BD%EC%A0%90-%EB%B6%84%EC%84%9D%EC%9D%84-%ED%86%B5%ED%95%9C-%EB%B3%B4%EC%95%88-%EA%B0%95%ED%99%94)
