<a href="https://onyxia-t.intern.statistik.at/launcher/ide/rstudio?name=hello-world-r-shiny&version=2.3.10&init.personalInit=«https%3A%2F%2Fraw.githubusercontent.com%2Fgarronej%2Fhello-world-shiny%2Frefs%2Fheads%2Fmain%2Fonyxia-init.sh»&git.repository=«https%3A%2F%2Fgithub.com%2Fgarronej%2Fhello-world-shiny»&autoLaunch=true">
    <img height=20 src="https://user-images.githubusercontent.com/6702424/173724486-30b6232a-c5d2-40da-a0cc-4d4a11824135.png">
</a>

# `hello-world-shiny`

## Goals

Install deps, run shiny app, via shiny server, behind nginx and with certbot/letsencrypt


Deps install shiny from a Ubuntu/Debian package:
```
sudo apt install r-cran-shiny
```

or install from source for advanced users (R and gcc is installed from OS package):
```
Rscript -e 'install.packages("shiny", repos="https://cran.rstudio.com/")'
```
> Notes: 1GB ram is not enough if installing from source!

Run to test
```
Rscript -e "shiny::runApp('./src/', port=8080, host='0.0.0.0')"
```

## From 0 to hero:

1) Byu VPS with latest ubuntu
2) Buy domain name
3) `apt install nginx certbot-nginx`
4) `apt install r-cran-shiny`
5) https://github.com/rstudio/shiny-server#installing
6) upload your app in `/srv/shiny-server/hello-world-shiny`
7) setup shiny server for single app https://docs.rstudio.com/shiny-server/#host-a-single-application
8) nginx `proxy_pass http://127.0.0.1:8080;`
8) nginx + certbot -d …your-domain…


## Docker

```
docker build -t hello-world-shiny .
docker run -p 8080:8080 -it hello-world-shiny
```

### Advanced:
- multiple shiny servers for concurency
- nginx cacheing https://www.nginx.com/blog/nginx-caching-guide/
- maybe https://www.shinyproxy.io/deployment/
