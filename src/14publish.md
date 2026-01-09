# Private and Published Modules

Node Modules can be constructed to be publisable or private. Published modules are modules that will appear on **npm package repository**, these will be accessible for all to use.

Private modules are typically ones in which exist outside of the npm repository system. Either local ones or ones that are sourced from a git repository. However, there are private modules within the npm repository syestem. This can be declared within `package.json` as `private: true`.


## Private Modules

Within `package.json`, it allows the user to specify a git repository associated with a package (and the branch). This is assumed to be associated with a repository that is private but you as a developer have access to it.

Within `package.json`, we are able to specify under the `dependencies` key an entry of this format: `"package_name: git://repository-url"`.




## Publishing Modules

Publishing a module is fairly striaght forward, however it does require the following an account on `npm`. Afterwards, you are then able to do the following.

* Login using `npm`.
* Check to see if the package name you have by using `npm search <package name>`.
* Publish your package using `npm publish`.
