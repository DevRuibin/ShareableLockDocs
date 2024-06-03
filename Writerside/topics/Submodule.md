# how to use the submodule

This is a submodule of the project of [Shareable lock backend](https://github.com/DevRuibin/SharableLockBackend).
Here is some instructions on how to use the submodule.

## Working with the submodule

```bash
cd  SharableLockDocs
git add .
git commit -m "commit message"
git push origin main
```


## Updating the submodule in the main project

```bash
cd SharableLockDocs
git pull origin main
cd ..
git add SharableLockDocs
git commit -m "update the submodule"
git push origin main
```