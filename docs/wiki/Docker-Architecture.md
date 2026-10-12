# Planned Docker-based architecture redesign

The original deployed architecture did **not** use Docker containers. The team built an image and planned a longer-term redesign around containerized deployment; the available image was not the latest application version.

<img src="https://user-images.githubusercontent.com/67851701/218299174-6afac629-0039-4bd0-8cd8-e5669cc93a4a.png" width="400">

Historical image download:

```bash
docker pull youngseoyoo/my-own-house
```

Historical local execution:

```bash
docker run -p 8000:8000 youngseoyoo/my-own-house
```

These commands are preserved as documentation, not a current deployment recommendation. Inspect and trust an image before running it. The redesign and image update were future work.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Docker%EC%99%80-%ED%95%A8%EA%BB%98-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%EC%9E%AC%EC%84%A4%EA%B3%84)
