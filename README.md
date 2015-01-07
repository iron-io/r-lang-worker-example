# r-lang-worker-example
Hello world for R on IronWorker

## Getting Started

Run locally first:

```sh
docker run -ti --rm -v "$(pwd)":/home/docker -w /home/docker -u docker r-base Rscript hello.R
```

Then upload to IronWorker:

```
zip -r helloR.zip *
ironcli upload helloR.zip Rscript hello.R
```

Then queue it:

``` 
ironcli queue helloR
```
