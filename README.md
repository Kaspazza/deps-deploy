[![Clojars Project](https://img.shields.io/clojars/v/deps-deploy.svg)](https://clojars.org/deps-deploy)
# deps-deploy

A Clojure library to deploy your stuff to clojars with `clj` or `clojure`. It's a very thin wrapper around
Chaz Emericks [pommegranate](https://github.com/cemerick/pomegranate) library.

## Usage

To deploy to Clojars, simply merge 

```clojure
{:deploy {:extra-deps {deps-deploy {:mvn/version "RELEASE"}
          :main-opts ["-m" "deps-deploy.deps-deploy" "deploy" 
                      "{:artifact,\"YOUR_JAR.jar\",:name,YOUR_ARTIFACT_NAME,:version,\"0.0.1\"}"]}}
```

have a `pom.xml` handy (you can generate one with `clj -Spom` and `deps-deploy` with 

```sh
$ env CLOJARS_USER=username CLOJARS_PASSWORD=password clj -a:deploy
```

to deploy to Clojars


`deps-deploy` also supports installing to your local `.m2` repo, by invoking `install` instead of `deploy`:
```clojure
{:install {:extra-deps {deps-deploy {:mvn/version "RELEASE"}
           :main-opts ["-m" "deps-deploy.deps-deploy" "install"
           "{:artifact,\"YOUR_JAR.jar\",:name,YOUR_ARTIFACT_NAME,:version,\"0.0.1\"}"]}}
```



## License

Copyright © 2018 Erik Assum

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
