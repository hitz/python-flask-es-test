
# Python/Flask Testing prototype
A prototype web portal for genomic information

## Prerequisites

Python 2.7.8 or greater on Mac OSX.  Elasticsearch 2.4 

Ensure you've installed [pip][1], [virtualenv][2], [nodejs][3], [elasticsearch][4] (Note: This has all been done for you already if you are actually taking the test)

Detailed install instructions (MacOSX):
```
>/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
>brew install python@2
>brew install git
>pip install virtualenv
>brew cask install homebrew/cask-versions/java8
>brew install elasticsearch@2.4
>brew link elasticsearch@2.4
 ```

## Background
This application is designed to mimic a typical web programming environment in the Cherry Lab.
The stack uses Python (Flask) as a web framework and API, Javascript (ReactJS) for the web front end, and Elasticsearch as a ~static, searchable database.  The database is designed to connect the genomes (list of genes), the functional annotations ([GO][5] terms), and disease associations for each gene from [OMIM][6].   These data are loaded and indexed into elasticsearch and results provided by the api using /api/search/ endpoint.  The system is set up to load the data from the worm C. elegans.  During the test you will be asked to extend the functionality of the software.

## Organization of the software

### Root directory
Contains this README various python and node package requirements, and a Makefile

### scripts/elastic_search directory
Contains the code for loading the data and indexing it in Elasticsearch.  The data files are located in scripts/elastic_search/data.

### src directory 
Contains the python Flask code to handle routing, search, and API functions (and dev server).

#### src/js_src
ReactJS code for the front end

#### src/templates
A single boilerplate jinja file.

### src/build
Compile JS from node; recreated with make build.

#### src/public
Public libraries for Select CSS and Sigma plugin

## Getting started with the Application

Create a virtualenv for isolating the python dependencies:


## In one terminal, start elasticsearch
See: [Elasticsearch Docs][7] for more info
```bash
elasticsearch
```

## In a second terminal (the prototype currently requires Python2)
:
```bash
virtualenv -p python2 prototype
source prototype/bin/activate (csh)
OR
. prototype/bin/activate
```
## In the repository directory 
```bash
make build
make index
make run
```

To run tests

```bash
source prototype/bin/activate
make tests
```


## Development Environment Pro Tips
Assets are compiled using [webpack][8]. 
To enable [hot module replacement][9] in your development environment,
run `npm start` while the dev server is running and refresh the page.
Subsequent JavaScript changes will go to your browser as a "hot
update" without refreshing.

You can run JavaScript unit tests automatically on each file change by
running `npm run test:watch`.

JavaScript coding style is enforced with [ESLint][10].
The rules are configured in the .eslintrc file.

[1]: https://pip.pypa.io/en/stable/installing/
[2]: https://virtualenv.pypa.io/en/stable/installation/
[3]: https://docs.npmjs.com/getting-started/installing-node
[4]: https://gist.github.com/jpalala/ab3c33dd9ee5a6efbdae
[5]: http://www.geneontology.org/
[6]: https://www.omim.org/
[7]: https://www.elastic.co/guide/en/elasticsearch/reference/2.3/index.html
[8]: https://webpack.github.io/
[9]: https://webpack.github.io/docs/hot-module-replacement.html
[10]: http://eslint.org/

