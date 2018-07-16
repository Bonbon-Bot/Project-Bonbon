# Project-Bonbon## RESULT OBJECT

The objects that are returned by npm-package-arg contain the following
keys:

* `type` - One of the following strings:
  * `git` - A git repo
  * `tag` - A tagged version, like `"foo@latest"`
  * `version` - A specific version number, like `"foo@1.2.3"`
  * `range` - A version range, like `"foo@2.x"`
  * `file` - A local `.tar.gz`, `.tar` or `.tgz` file.
  * `directory` - A local directory.
  * `remote` - An http url (presumably to a tgz)
* `registry` - If true this specifier refers to a resource hosted on a
  registry.  This is true for `tag`, `version` and `range` types.
* `name` - If known, the `name` field expected in the resulting pkg.
* `scope` - If a name is something like `@org/module` then the `scope`
  field will be set to `@org`.  If it doesn't have a scoped name, then
  scope is `null`.
* `escapedName` - A version of `name` escaped to match the npm scoped packages
  specification. Mostly used when making requests against a registry. When
  `name` is `null`, `escapedName` will also be `null`.
* `rawSpec` - The specifier part that was parsed out in calls to `npa(arg)`,
  or the value of `spec` in calls to `npa.resolve(name, spec).
* `saveSpec` - The normalized specifier, for saving to package.json files.
  `null` for registry dependencies.
* `fetchSpec` - The version of the specifier to be used to fetch this
  resource.  `null` for shortcuts to hosted git dependencies as there isn't
  just one URL to try with them.
* `gitRange` - If set, this is a semver specifier to match against git tags with
* `gitCommittish` - If set, this is the specific committish to use with a git dependency.
* `hosted` - If `from === 'hosted'` then this will be a `hosted-git-info`
  object. This property is not included when serializing the object as
  JSON.
* `raw` - The original un-modified string that was provided.  If called as
  `npa.resolve(name, spec)` then this will be `name + '@' + spec`.

Working on bonbon-bot
