This is an [MRE](https://en.wikipedia.org/wiki/Minimal_reproducible_example) for two caching-related bugs in nx.

### Bug 1 (https://github.com/nrwl/nx/issues/20942)

To reproduce:

1. Run `yarn nx run products:build`
2. Edit `apps/products/foo.txt`
3. Run `yarn nx run products:build` again

The `products` target will rebuild, even though `foo.txt` is marked as ignored by `apps/products/.gitignore`.

### Bug 2 (https://github.com/nrwl/nx/issues/20945)

To reproduce:

1. Run `yarn nx run cart:build`
2. Edit `apps/products/bar.txt`
3. Run `yarn nx run cart:build` again

The `cart` target will be rebuilt even though `bar.txt` is marked as ignored in the `.nxignore`.
