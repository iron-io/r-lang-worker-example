# r-lang-worker-example

Hello world for R on IronWorker using the r-base Docker image.

## Getting Started

Run locally first:

```sh
docker run -ti --rm -v "$(pwd)":/home/docker -w /home/docker -u docker r-base Rscript hello.R
```

Then upload to IronWorker:

```
zip -r helloR.zip *
iron worker upload helloR.zip Rscript hello.R
```

Then queue it:

```
iron worker queue helloR
```

## Using R Packages

To install and use an R package in your worker, create a directory called Rpackages:

```sh
mkdir Rpackages
```

Fire up the interactive shell:

```sh
docker run -ti --rm  -v "$(pwd)":/home/docker -w /home/docker -u docker r-base
```

Then run:

```sh
install.packages("car", lib="./Rpackages")
```

Then in your script, you'd use (see pkgtest.R):

```r
library(car, lib.loc="./Rpackages")
```

Then upload/queue as above with hello.R.
