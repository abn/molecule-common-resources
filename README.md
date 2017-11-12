# Molecule: Common Resources for Scenarios

This repository provides commonly used resources for molecule test scenarios. Initial development was based on work done for the [test suite](https://github.com/metacloud/molecule/tree/master/test/resources) used by the [Molecule Project](https://molecule.readthedocs.io/en/latest/) itself.

## Usage Examples
### Git Submodule
#### Initialisation
Resources can be consumed as a [submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules) within your project's molecule directory. This can be done as shown below.

```sh
# assuming you are currently within your project directory
git submodule add https://github.com/abn/molecule-common-resources.git ./molecule/resources
git commit -m "git: add molecule-common-resources submodule"
```

Once this is done you can, within a scenario's `molecule.yml` file refer to a resource.
```yaml
provisioner:
  name: ansible
  playbooks:
    create: ../resources/playbooks/docker/create.yml
    prepare: prepare.yml
    destroy: ../resources/playbooks/docker/destroy.yml
  lint:
    name: ansible-lint
```

#### Update
In order to consume an updated version of the resources in your project, you will have to update the submodule commit. You can do this using the `update` sub-command.

```sh
git submodule update --remote
git add ./molecule/resources
git commit -m "update common resources"
```
