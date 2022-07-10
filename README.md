# Github Workflow Rust CLI

An official dev template that configures your cli's entire github workflow in rust

## How to use

After installing the [dt cli](https://dtemplate.org/docs/cli/install) enter the root folder of your cli, example:

```sh
cd projects/cli-example
```

Then use this template through the dt cli:

```sh
dt new -t github-workflow-rust-cli
```

## TODO

- Go to your repository configuration and create a [secret in actions](https://docs.github.com/en/actions/security-guides/encrypted-secrets) with the name `TOKEN_GITHUB`
- In .github/workflows/create_new_tag.yml replace the `- master` in line 5 column 7 by `- {your-default-branch-name}` (replace `your-default-branch-name` by your default branch name)

## Results

- Every time there is a new push in your default branch a new tag with a new version will be created, then shortly after that a pipeline called `Release` will be triggered, which will build your project, create a new release and add the file binary in zip there.
- Every time a pull request is opened, and the change files have `Cargo.toml`, `Cargo.lock`, `**.rs` a testing process will be run, this includes the commands: `cargo fmt -- --check`, `cargo check`, `cargo clippy`. you can also open the file `.github/workflows/ci.yml` in line 39 column 11 and add a new version of rust, and then it will run all that in all the versions that are there!

```sh
.
├── .github
│    └── workflows
│       ├── ci.yml
│       ├── create_new_tag.yml
│       └── release.yml
│ {the-rest-of-the-files-in-your-cli}...
```
