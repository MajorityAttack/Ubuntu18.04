
## Delete submodules (protobuf and gRPC) from git project

```sh
git submodule deinit protobuf

git rm protobuf

git submodule deinit gRPC

git rm gRPC

git commit -m "Removed submodule"

git push
```
