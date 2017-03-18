# rocker-fun

A test repo for all my Docker+R (rocker) experimentation

---

This is meant to be a testbed for my working environment with R.
Ideally, it should get to the point where you clone this repo, fire up [Docker](https://www.docker.com/), and get [RStudio](https://www.rstudio.com/) running in your browser.
The objective of this workflow is to make my research analyses reproducible, with minimum (no?) hindrances.
The Docker image in question (`rocker/verse`, brought to you by the wonderful people behind [`rocker-org`](https://github.com/rocker-org)) should contain all the main dependencies needed to work with my code, and any additional packages needed will be installed automatically by `docker-compose` (am I allowed to do that?).

## Requirements

- Access to a \*NIX system (GNU/Linux or macOS) or knowledge of how to use CLI tools on Windows
- git
- Docker (and Docker Compose)
- Some basic knowledge of R and RStudio (although, most of the work should be entirely automated or self-explanatory or both)

## Workflow

Fire up a terminal, navigate to a directory where you would like to download this repository, and follow these instructions:

```bash
$ git clone https://path.to/repo.git # Clone this git repo to your machine
$ cd repo # Enter the git repository
$ git submodule init # Initialise the git submodules (see below)
$ git submodule update # Update the git submodules
$ docker-compose up -d # Launch the Docker container named amr_research
```

You then need to navigate you `localhost:8787` or `0.0.0.0:8787` in your browser, to see RStudio along with all the files from the repository.
To log in, use "`rstudio`" as both the username and password.

When you're done playing around with the RStudio, close your browser window, and run:

```bash
$ docker-compose down # Will stop and delete the container
# Optional! If you want to delete the Docker image just created,
# run the following command as well:
$ docker image rm raoofphysics/research
```

## Directory structure

- `/data`: all the datasets used in the analyses
- `/output`: R Markdown files used for producing a variety of content [N.B.: In the final version, these subdirectories will in fact "git submodules", meaning that their content will be stored in separate git repository. To make changes to these projects and send them to me, you will have to refer to their respective `README.md` files.]
    - `/notebooks`: R notebooks containing used both for exploration as well as generation of plots for posters etc.
    - `/papers`: journal papers and conference proceedings [directory names start with date (`YYYYMM`)]
    - `/presentations`: conference presentations and talks [directory names start with date (`YYYYMM`)]
    - `/thesis`: my doctoral thesis
- `/src`: code and scripts (mostly R); exploratory code is not stored here though -- you can find that under `/output/notebooks`

### Interesting documents to explore

- Blah blah blah: `path/to/directory`
    - ![type: presentation](https://img.shields.io/badge/type-presentation-blue.svg)
- More blah blah: `path/to/second/directory`
    - ![type: paper](https://img.shields.io/badge/type-paper-blue.svg)

## Contributing

I've created this repo to test out my understanding of reproducible workflows using some modern tools.
It may well be that either I've entirely missed the point and am abusing a tool badly or there are better tools/workflows out there.
In either case, please leave a comment in a GitHub issue.

## Licence

Code (in the form of R scripts or chunks) is licensed under GPLv3.
Content (text, images etc.) is licenced under CC BY-SA 4.0.
Copyleft FTW, yo.

## Acknowledgements

- Tibor Simko, for his help and advice regarding Docker
- Jacopo Notarstefano, for his help and advice concerning Docker
- Rik Smith-Unna, for his help and advice concerning R
