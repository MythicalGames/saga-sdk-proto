# saga-sdk-proto

Project Saga SDK protobuf/gRPC files

## Building the saga-sdk-proto maven artifact

This project has only the protocol definitions for the SDK for inclusion as a submodule regardless of the language. The saga-sdk-proto maven
artifact in the mytical central maven repository is built as part of the saga-sdk-java Java SDK client library. The maven artifact is used in
conjuction with the Java SDK client library, but can also be used independently to provide the generated protocol buffer code for both Java
and Kotlin. 

### Updating the saga-sdk-proto maven artifact
1. Clone or pull the saga-sdk-java repository.
2. Do git submodule update if not already done with the --recursive flag when cloning
3. Create feature branch
4. Update the saga-proto submodule to the desired commit (most likely HEAD of develop)
5. Update the Java SDK client so that the project can build successfully (proto changes will almost always require updates to the Java client)
6. Bump the version for project_version variable in the root build.gradle
7. When the changes are merged, the CI build will update the mythical central repo with the updated artifact

### Releasing the saga-sdk-proto maven artifact
This should eventually be performed by Github Actions, but is currently a manual process. This process will also be a bit different when
the Java SDK client is ready for public release and release versions are uploaded to maven central rather than mythical central.

1. Clone or pull the saga-sdk-java repository.
2. Do git submodule update if not already done with the --recursive flag when cloning
3. Checkout master
4. Create feature branch
5. Merge develop into feature branch
6. Remove -SNAPSHOT from project_version variable in the root build.gradle
7. Create a PR to merge into master
8. When the changes are merged, the CI build will update the mythical central repo with the release artifact
9. Checkout develop
10. Create feature branch
11. Bump the version for project_version variable in the root build.gradle
12. Create a PR to merge into develop


