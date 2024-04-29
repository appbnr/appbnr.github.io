# Web App Package Format

In Appbnr, web application is packaged as a zip file, with following structure.

```
- package.yml
- app
  - index.html
  - ...
- locales
  - <locale>
```

# Package.yml
For this one, refer [package.yml](bundle-metadata-spec.md).

# app
Within this folder, all web application files, including .js, .css or any static assets are within this package.

`index.html` is normally under this folder. If user access your app like `https://<your-org-code>.appbnr.com/example/`,
then `index.html` will be served.

For example, in a typical Angular app, there will be:
```
- app
  - assets
  - index.html
```

# locales
If you want to support multiple languages, then multiple versions are stored under locales folders. Folder name will be locale id,
for example `zh_CN`. 

Structure of folder under locales are same as `app`.

# Build the package
Once all are in the same folder with above defined structure, just `zip` it into a file.

This can also be done with `abnr` command tool:
```bash
abnr bundle package <path to folder>
```

An example of how to automate Angular app, can be found here:
* [How to package Angular app](/how-to/how-to-package-angular-app.md)