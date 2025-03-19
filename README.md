# wutz-engel-deployment
resources and scripts to set up a custom Engelsystem for the Wutzrock festival

## General notes
Our fork, including internal isues is located at https://github.com/zeh-nagel/engelsystem

## Updating Our Engelsystem Instance
Before Deploying a new release, we need to re-insert some of our customizations.

TODO: do we want to do this on a dedicated branch and turn it into a release also?

### Syncing our `main` branch with new upstream release
TODO

### Updating the locale files
We're using customized locale (`.po`) files that exchanges the original "Engel"/"Angel" wording to terms that makes more sense for our audience (for details, see [#13](https://github.com/zeh-nagel/engelsystem/issues/13)).
If they have changed since our last deployment, these may need to be updated.
Proceed as follows:

1. Check whether the `*.po` files in the `resources/lang` folder have changed in the new release. To do this, check whether the last commit date [on github](https://github.com/engelsystem/engelsystem/tree/main/resources/lang) is older than the last commit to [these files **on our `wutzrock-locale-DONOTDELETE` branch**](https://github.com/zeh-nagel/engelsystem/tree/wutzrock-locale-DONOTDELETE/resources/lang). If our changes are newer, you can skip the rest of this section.

2. If there have been changes, you need to integrate these into our modified `.po` files.

First, check out out the `wutzrock-locale-DONOTDELETE` branch from our engelsystem fork:
(these instructions assume that this fork is called `origin` on your system)

```
$ # make sure you're in the Engelsystem folder
$ cd Engelsystem
$
$ git fetch origin
$ git checkout -b wutzrock-locale-DONOTDELETE origin/wutzrock-locale-DONOTDELETE
```
you are now on the `wutzrock-locale-DONOTDELETE` branch.

Then, open all `*.po` files in `resources/lang/de_DE`. Check if any of the following keywords have re-appeared and replace them with the listed replacements.

| term  | replace with |
| ------------- | ------------- |
| Himmel  | Knotenpunkt |
| Engel | Helfer*innen |
| Engeltyp | Team | 
| Engelsystem | Wutzrock Helfen |

Then, do the same thing with `resources/lang/en_US` and these replacements:

| term  | replace with |
| ------------- | ------------- |
| Heaven  | Knotenpunkt |
| Angel | Helpers|
| Angel Type | Team | 
| Engelsystem | Wutzrock Helfen |

If you've changed any files in this process, commit and push your changes:

```
$ git add resources/lang/de_DE
$ git add resources/lang/en_US
$ git commit -m "updated wording in .po files"
$ git push origin wutzrock-locale-DONOTDELETE
```

If you feel unsure about your changes, feel free to open a PR instead of directly pushing to `wutzrock-locale-DONOTDELETE` or ask a team member to review your changes.

TODO: I *think* ⬇️ this ⬇️ can be avoided if we construct our own release containing our custom *.po files etc

Now, copy your newly modified `.po` files back to this repo for easy access:

```
$ cp resources/lang/de_DE/*.po <path to this repository on your system>/resources/lang/de_DE
$ cp resources/lang/en_US/*.po <path to this repository on your system>/resources/lang/de_DE
```

## Deployment

### copy over our `.po` files
TODO: I *think* this can be avoided if we construct our own release containing our custom *.po files etc

```
$ # from the root folder of this repository
$ cp -r resources <path to Engelsystem to be deployed>
```
