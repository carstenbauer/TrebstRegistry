# Creating the registry
```julia
using Pkg
Pkg.add(Pkg.PackageSpec(url="https://github.com/crstnbr/Registrator.jl"))
using Registrator
regsdir = joinpath(homedir(), "julia-registries")
!isfile(regsdir) && mkdir(regsdir)
cd(regsdir)

regname = "TrebstRegistry"
regurl = "http://github.com/crstnbr/$regname"
regpath = joinpath(regsdir, regname)

Registrator.create_registry(regname, regurl)
```

Create the registry repository on GitHub and push the local registry.

# Installing the registry locally
```julia
Pkg.Registry.add(Pkg.RegistrySpec(url=regurl))
```
or
```julia
] registry add http://github.com/crstnbr/TrebstRegistry
```
# Adding a package

You must have the package repository somewhere locally. Activate the pkg repo (or do whatever necessary) to be able to `using TestPackage`. Then, do the
following:

```julia
regsdir = joinpath(homedir(), "julia-registries")
regname = "TrebstRegistry"
regpath = joinpath(regsdir, regname)
using Registrator
Registrator.register(TestPackage, regpath)
```

Afterwards, go to the registry directory and push the changes (which should have been committed) to GitHub. You're done! The package should now be `] add`able. (It might be necessary to `] registry up TrebstRegistry` first.)


## Resources
Based on https://lhendricks.org/julia_notes.pdf and https://github.com/GunnarFarneback/Registrator.jl. More manual instructions: https://discourse.julialang.org/t/creating-a-registry/12094
