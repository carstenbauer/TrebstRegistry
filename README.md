To install this registry (next to the [General](https://github.com/JuliaRegistries/General) registry) execute
```
] registry add http://github.com/crstnbr/TrebstRegistry
```

To test that things are set up correctly, try fake adding the `TestPackage`.
```
] preview add TestPackage
```
You can drop the `preview` to actually add the package.
