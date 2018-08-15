# mock-mesos-server

A golang test utility for mocking Mesos server requests. 

Copy (or better still, [drop](https://github.com/matryer/drop)) `mock_mesos_server.go` and `cmd/gen.go` into your
project, create fixtures as described below, and run `go generate`. 

Note you will need [mesos-go](https://github.com/mesos/mesos-go) on your GOPATH. 

## Test Fixtures

Each subdirectory in the testdata directory contains fixtures for a test case. For example, the 'empty' subdirectory 
contains a response which the Mesos agent operator API would yield if no tasks were running on the agent. 

As this plugin communicates with Mesos via protobuf, and the binary protobuf format is not human-readable nor human-
editable, each file is in JSON format. Running `go generate` from the root of the directory will compile these JSON
files to protobuf binary, which is then stored in a .bin file alongside the original. 

If you make changes to a JSON file you should run `go generate` and be sure to commit both the changed JSON file and 
the generated protobuf binary file. 

Adding a test case is as simple as creating a new directory with appropriately named JSON files and running `go
generate`. 



