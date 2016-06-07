# Build

## build backend

```
docker build -t twasr-frontend -f docker/frontend/Dockerfile .
```

## build frontend

```
docker build -t twasr-backend -f docker/backend/Dockerfile .
```

## run backend

```
docker run -d -p 8580:80 -v /Users/dtong/code/data/kaldi_models:/opt/models twasr-backend
```

## run frontend

```
docker run -d -p 8480:443 twasr-frontend
```
