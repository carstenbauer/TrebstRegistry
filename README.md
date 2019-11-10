## Using the registry
To install this registry (next to the [General](https://github.com/JuliaRegistries/General) registry) execute
```
] registry add http://github.com/crstnbr/TrebstRegistry
```

To test that things are set up correctly, try fake adding the `TestPackage`.
```
] preview add TestPackage
```
(You can drop `preview` to actually add the package.)

## Register a package (version)
Currently, there are two ways to register a new package or to release a new version of an already existing package:

* Using [this fork of Registrator.jl](http://github.com/crstnbr/Registrator.jl) to make the changes locally and filing a PR (recommended)
* Manually creating a PR that introduces the necessary changes.

If none of those work for you, contact [me](http://github.com/crstnbr).

### Registering a package using `crstnbr/Registrator.jl`

First, `] add https://github.com/crstnbr/Registrator.jl`, fork the `TrebstRegistry` repository, and `git clone` it to some local directory `<reg_path>`. The workflow is then simple:

```julia
using Registrator
using MyPackage
Registrator.register(MyPackage, "<reg_path>")
```

This will register the package in your local version of the registry. After `git push`ing the changes in `<reg_path>` to your github fork you can create a PR here (in the actual registry).

That's it! After one of the maintainers has reviewed and merged the PR your new package (version) is registered.

## Example package

An example package with [Code Integration (CI)](https://github.com/crstnbr/TestPackage2.jl/tree/master/.github/workflows/CompatHelper.yml), [CompatHelper.jl](https://github.com/crstnbr/TestPackage2.jl/tree/master/.github/workflows/CI.yaml), and [TagBot](https://github.com/crstnbr/TestPackage2.jl/tree/master/.github/workflows/TagBot.yml) set up to work with this custom registry can be found [here](http://github.com/crstnbr/TestPackage2.jl).
