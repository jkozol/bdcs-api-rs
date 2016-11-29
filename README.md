# Composer BDCS API Library, Server, and Web Interface

This codebase is the BDCS API server, including a version of the composer-UI
web interface.

It depends on the BDCS metadata store generated by the [bdcs import
service](https://github.com/wiggum/bdcs), and can be run directly via `cargo
run` if the system has Rust installed, or via Docker.


## Running the API Server in Docker

Build the docker image by running:

`sudo docker build -t bcl/bdcs-api .`

To run the API it requires access to a copy of the metadata.db created by the
[bdcs import service[(https://github.com/wiggum/bdcs) and to a directory of
recipes. The recipes directory can be empty initially, or you can copy
`examples/recipe-example.toml` to `example`.

You can then run the API server and composer-UI code like this:

`docker run -it --rm -v ~/tmp/bdcs-db/:/bdcs-db/:Z -v ~/tmp/recipes/:/bdcs-recipes/:Z -p 8000:80 bcl/bdcs-api`

You can then access the UI on the `http://localhost:8000`