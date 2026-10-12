# Cross-Origin Resource Sharing (CORS)

The frontend and backend served different origins. Browser requests failed until cross-origin access was configured.

<img src="https://user-images.githubusercontent.com/90206705/217190275-9e39161c-7a78-468d-9e4e-454b0c962ba2.png">

## Same-origin policy

An origin is determined by protocol, host and port. The same-origin policy restricts interactions with resources loaded from a different origin; CORS headers allow a server to authorize selected cross-origin access.

![CORS 정책](https://user-images.githubusercontent.com/90206705/217184193-414b605b-fae5-49a4-8e79-5e08ca89a550.jpeg)

## FastAPI configuration

1. Import `CORSMiddleware`.

```python
from fastapi.middleware.cors import CORSMiddleware
```

2. List allowed origins; the original local example used port 8080.

```python
origins = [
    "http://localhost:8080",
]
```

3. Register the middleware with origin, credential, method and header settings.

```python
app.add_middleware(
    CORSMiddleware,
    allow_origins=origins,
    allow_credentials=True,  # cross-origin request에서 cookie를 포함할 것인지 (default=False)
    allow_methods=["*"],     # cross-origin request에서 허용할 method들을 나타냄. (default=['GET']
    allow_headers=["*"],     # cross-origin request에서 허용할 HTTP Header 목록
)
```

The snippet is retained as the original example. Configure actual origins narrowly for deployed services; CORS is not authentication and does not by itself make an API secure.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/CORS-%EC%9D%B4%EC%8A%88)
