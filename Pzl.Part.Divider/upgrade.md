# Upgrade project C:\repos\pzl\spfx-solutions\Pzl.Part.Divider to v1.7.1

Date: 2019-1-15

## Findings

Following is the list of steps required to upgrade your project to SharePoint Framework version 1.7.1. [Summary](#Summary) of the modifications is included at the end of the report.

### FN001001 @microsoft/sp-core-library | Required

Upgrade SharePoint Framework dependency package @microsoft/sp-core-library

Execute the following command:

```sh
npm i @microsoft/sp-core-library@1.7.1 -SE
```

File: [./package.json](./package.json)

### FN001002 @microsoft/sp-lodash-subset | Required

Upgrade SharePoint Framework dependency package @microsoft/sp-lodash-subset

Execute the following command:

```sh
npm i @microsoft/sp-lodash-subset@1.7.1 -SE
```

File: [./package.json](./package.json)

### FN001004 @microsoft/sp-webpart-base | Required

Upgrade SharePoint Framework dependency package @microsoft/sp-webpart-base

Execute the following command:

```sh
npm i @microsoft/sp-webpart-base@1.7.1 -SE
```

File: [./package.json](./package.json)

### FN002001 @microsoft/sp-build-web | Required

Upgrade SharePoint Framework dev dependency package @microsoft/sp-build-web

Execute the following command:

```sh
npm i @microsoft/sp-build-web@1.7.1 -DE
```

File: [./package.json](./package.json)

### FN002002 @microsoft/sp-module-interfaces | Required

Upgrade SharePoint Framework dev dependency package @microsoft/sp-module-interfaces

Execute the following command:

```sh
npm i @microsoft/sp-module-interfaces@1.7.1 -DE
```

File: [./package.json](./package.json)

### FN002003 @microsoft/sp-webpart-workbench | Required

Upgrade SharePoint Framework dev dependency package @microsoft/sp-webpart-workbench

Execute the following command:

```sh
npm i @microsoft/sp-webpart-workbench@1.7.1 -DE
```

File: [./package.json](./package.json)

### FN010001 .yo-rc.json version | Recommended

Update version in .yo-rc.json

In file [./.yo-rc.json](./.yo-rc.json) update the code as follows:

```json
{
  "@microsoft/generator-sharepoint": {
    "version": "1.7.1"
  }
}
```

File: [./.yo-rc.json](./.yo-rc.json)

### FN014006 sourceMapPathOverrides in .vscode/launch.json | Recommended

In the .vscode/launch.json file, for each configuration, in the sourceMapPathOverrides property, add "webpack:///.././src/*": "${webRoot}/src/*"

In file [.vscode\launch.json](.vscode\launch.json) update the code as follows:

```json
{
  "configurations": [
    {
      "sourceMapPathOverrides": {
        "webpack:///.././src/*": "${webRoot}/src/*"
      }
    }
  ]
}
```

File: [.vscode\launch.json](.vscode\launch.json)

### FN014006 sourceMapPathOverrides in .vscode/launch.json | Recommended

In the .vscode/launch.json file, for each configuration, in the sourceMapPathOverrides property, add "webpack:///.././src/*": "${webRoot}/src/*"

In file [.vscode\launch.json](.vscode\launch.json) update the code as follows:

```json
{
  "configurations": [
    {
      "sourceMapPathOverrides": {
        "webpack:///.././src/*": "${webRoot}/src/*"
      }
    }
  ]
}
```

File: [.vscode\launch.json](.vscode\launch.json)

### FN006003 package-solution.json isDomainIsolated | Required

Update package-solution.json isDomainIsolated

In file [./config/package-solution.json](./config/package-solution.json) update the code as follows:

```json
{
  "solution": {
    "isDomainIsolated": false
  }
}
```

File: [./config/package-solution.json](./config/package-solution.json)

### FN010007 .yo-rc.json isDomainIsolated | Recommended

Update isDomainIsolated in .yo-rc.json

In file [./.yo-rc.json](./.yo-rc.json) update the code as follows:

```json
{
  "@microsoft/generator-sharepoint": {
    "isDomainIsolated": false
  }
}
```

File: [./.yo-rc.json](./.yo-rc.json)

### FN018001 Web part Microsoft Teams tab resources folder | Optional

Create folder for Microsoft Teams tab resources

Execute the following command:

```sh
mkdir C:\repos\pzl\spfx-solutions\Pzl.Part.Divider\teams_divider
```

File: [teams_divider](teams_divider)

### FN018002 Web part Microsoft Teams tab manifest | Optional

Create Microsoft Teams tab manifest for the web part

Execute the following command:

```sh
cat > C:\repos\pzl\spfx-solutions\Pzl.Part.Divider\teams_divider\manifest.json << EOF
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.2/MicrosoftTeams.schema.json",
  "manifestVersion": "1.2",
  "packageName": "Divider (flexible)",
  "id": "6a1a8d9e-13f0-43ac-8663-7f6278d1669e",
  "version": "0.1",
  "developer": {
    "name": "SPFx + Teams Dev",
    "websiteUrl": "https://products.office.com/en-us/sharepoint/collaboration",
    "privacyUrl": "https://privacy.microsoft.com/en-us/privacystatement",
    "termsOfUseUrl": "https://www.microsoft.com/en-us/servicesagreement"
  },
  "name": {
    "short": "Divider (flexible)"
  },
  "description": {
    "short": "Add a line to help divide areas on your page",
    "full": "Add a line to help divide areas on your page"
  },
  "icons": {
    "outline": "tab20x20.png",
    "color": "tab96x96.png"
  },
  "accentColor": "#004578",
  "configurableTabs": [
    {
      "configurationUrl": "https://{teamSiteDomain}{teamSitePath}/_layouts/15/TeamsLogon.aspx?SPFX=true&dest={teamSitePath}/_layouts/15/teamshostedapp.aspx%3FopenPropertyPane=true%26teams%26componentId=6a1a8d9e-13f0-43ac-8663-7f6278d1669e",
      "canUpdateConfiguration": true,
      "scopes": [
        "team"
      ]
    }
  ],
  "validDomains": [
    "*.login.microsoftonline.com",
    "*.sharepoint.com",
    "*.sharepoint-df.com",
    "spoppe-a.akamaihd.net",
    "spoprod-a.akamaihd.net",
    "resourceseng.blob.core.windows.net",
    "msft.spoppe.com"
  ],
  "webApplicationInfo": {
    "resource": "https://{teamSiteDomain}",
    "id": "00000003-0000-0ff1-ce00-000000000000"
  }
}
EOF
```

File: [teams_divider\manifest.json](teams_divider\manifest.json)

### FN018003 Web part Microsoft Teams tab small icon | Optional

Create Microsoft Teams tab small icon for the web part

Execute the following command:

```sh
cp C:\Users\miksv\AppData\Roaming\npm\node_modules\@pnp\office365-cli\dist\o365\spfx\commands\project\project-upgrade\assets\tab20x20.png C:\repos\pzl\spfx-solutions\Pzl.Part.Divider\teams_divider\tab20x20.png
```

File: [teams_divider\tab20x20.png](teams_divider\tab20x20.png)

### FN018004 Web part Microsoft Teams tab large icon | Optional

Create Microsoft Teams tab large icon for the web part

Execute the following command:

```sh
cp C:\Users\miksv\AppData\Roaming\npm\node_modules\@pnp\office365-cli\dist\o365\spfx\commands\project\project-upgrade\assets\tab96x96.png C:\repos\pzl\spfx-solutions\Pzl.Part.Divider\teams_divider\tab96x96.png
```

File: [teams_divider\tab96x96.png](teams_divider\tab96x96.png)

### FN002008 tslint-microsoft-contrib | Required

Install SharePoint Framework dev dependency package tslint-microsoft-contrib

Execute the following command:

```sh
npm i tslint-microsoft-contrib@5.0.0 -DE
```

File: [./package.json](./package.json)

### FN012011 tsconfig.json compiler options outDir | Required

Update tsconfig.json outDir value

In file [./tsconfig.json](./tsconfig.json) update the code as follows:

```json
{
  "compilerOptions": {
    "outDir": "lib"
  }
}
```

File: [./tsconfig.json](./tsconfig.json)

### FN012012 tsconfig.json include property | Required

Update tsconfig.json include property

In file [./tsconfig.json](./tsconfig.json) update the code as follows:

```json
{
  "include": [
    "src/**/*.ts"
  ]
}
```

File: [./tsconfig.json](./tsconfig.json)

### FN012013 tsconfig.json exclude property | Required

Update tsconfig.json exclude property

In file [./tsconfig.json](./tsconfig.json) update the code as follows:

```json
{
  "exclude": [
    "node_modules",
    "lib"
  ]
}
```

File: [./tsconfig.json](./tsconfig.json)

### FN015003 ./tslint.json | Required

Add file ./tslint.json

Execute the following command:

```sh
cat > ./tslint.json << EOF
{
  "rulesDirectory": [
    "tslint-microsoft-contrib"
  ],
  "rules": {
    "class-name": false,
    "export-name": false,
    "forin": false,
    "label-position": false,
    "member-access": true,
    "no-arg": false,
    "no-console": false,
    "no-construct": false,
    "no-duplicate-variable": true,
    "no-eval": false,
    "no-function-expression": true,
    "no-internal-module": true,
    "no-shadowed-variable": true,
    "no-switch-case-fall-through": true,
    "no-unnecessary-semicolons": true,
    "no-unused-expression": true,
    "no-use-before-declare": true,
    "no-with-statement": true,
    "semicolon": true,
    "trailing-comma": false,
    "typedef": false,
    "typedef-whitespace": false,
    "use-named-parameter": true,
    "variable-name": false,
    "whitespace": false
  }
}
EOF
```

File: [./tslint.json](./tslint.json)

### FN015004 ./config/tslint.json | Required

Remove file ./config/tslint.json

Execute the following command:

```sh
rm ./config/tslint.json
```

File: [./config/tslint.json](./config/tslint.json)

### FN015005 ./src/index.ts | Required

Add file ./src/index.ts

Execute the following command:

```sh
cat > ./src/index.ts << EOF
// A file is required to be in the root of the /src directory by the TypeScript compiler

EOF
```

File: [./src/index.ts](./src/index.ts)

### FN017001 Run npm dedupe | Optional

If, after upgrading npm packages, when building the project you have errors similar to: "error TS2345: Argument of type 'SPHttpClientConfiguration' is not assignable to parameter of type 'SPHttpClientConfiguration'", try running 'npm dedupe' to cleanup npm packages.

Execute the following command:

```sh
npm dedupe
```

File: [./package.json](./package.json)

## Summary

### Execute script

```sh
npm i @microsoft/sp-core-library@1.7.1 @microsoft/sp-lodash-subset@1.7.1 @microsoft/sp-webpart-base@1.7.1 -SE
npm i @microsoft/sp-build-web@1.7.1 @microsoft/sp-module-interfaces@1.7.1 @microsoft/sp-webpart-workbench@1.7.1 tslint-microsoft-contrib@5.0.0 -DE
mkdir C:\repos\pzl\spfx-solutions\Pzl.Part.Divider\teams_divider
cat > C:\repos\pzl\spfx-solutions\Pzl.Part.Divider\teams_divider\manifest.json << EOF
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.2/MicrosoftTeams.schema.json",
  "manifestVersion": "1.2",
  "packageName": "Divider (flexible)",
  "id": "6a1a8d9e-13f0-43ac-8663-7f6278d1669e",
  "version": "0.1",
  "developer": {
    "name": "SPFx + Teams Dev",
    "websiteUrl": "https://products.office.com/en-us/sharepoint/collaboration",
    "privacyUrl": "https://privacy.microsoft.com/en-us/privacystatement",
    "termsOfUseUrl": "https://www.microsoft.com/en-us/servicesagreement"
  },
  "name": {
    "short": "Divider (flexible)"
  },
  "description": {
    "short": "Add a line to help divide areas on your page",
    "full": "Add a line to help divide areas on your page"
  },
  "icons": {
    "outline": "tab20x20.png",
    "color": "tab96x96.png"
  },
  "accentColor": "#004578",
  "configurableTabs": [
    {
      "configurationUrl": "https://{teamSiteDomain}{teamSitePath}/_layouts/15/TeamsLogon.aspx?SPFX=true&dest={teamSitePath}/_layouts/15/teamshostedapp.aspx%3FopenPropertyPane=true%26teams%26componentId=6a1a8d9e-13f0-43ac-8663-7f6278d1669e",
      "canUpdateConfiguration": true,
      "scopes": [
        "team"
      ]
    }
  ],
  "validDomains": [
    "*.login.microsoftonline.com",
    "*.sharepoint.com",
    "*.sharepoint-df.com",
    "spoppe-a.akamaihd.net",
    "spoprod-a.akamaihd.net",
    "resourceseng.blob.core.windows.net",
    "msft.spoppe.com"
  ],
  "webApplicationInfo": {
    "resource": "https://{teamSiteDomain}",
    "id": "00000003-0000-0ff1-ce00-000000000000"
  }
}
EOF
cp C:\Users\miksv\AppData\Roaming\npm\node_modules\@pnp\office365-cli\dist\o365\spfx\commands\project\project-upgrade\assets\tab20x20.png C:\repos\pzl\spfx-solutions\Pzl.Part.Divider\teams_divider\tab20x20.png
cp C:\Users\miksv\AppData\Roaming\npm\node_modules\@pnp\office365-cli\dist\o365\spfx\commands\project\project-upgrade\assets\tab96x96.png C:\repos\pzl\spfx-solutions\Pzl.Part.Divider\teams_divider\tab96x96.png
cat > ./tslint.json << EOF
{
  "rulesDirectory": [
    "tslint-microsoft-contrib"
  ],
  "rules": {
    "class-name": false,
    "export-name": false,
    "forin": false,
    "label-position": false,
    "member-access": true,
    "no-arg": false,
    "no-console": false,
    "no-construct": false,
    "no-duplicate-variable": true,
    "no-eval": false,
    "no-function-expression": true,
    "no-internal-module": true,
    "no-shadowed-variable": true,
    "no-switch-case-fall-through": true,
    "no-unnecessary-semicolons": true,
    "no-unused-expression": true,
    "no-use-before-declare": true,
    "no-with-statement": true,
    "semicolon": true,
    "trailing-comma": false,
    "typedef": false,
    "typedef-whitespace": false,
    "use-named-parameter": true,
    "variable-name": false,
    "whitespace": false
  }
}
EOF
rm ./config/tslint.json
cat > ./src/index.ts << EOF
// A file is required to be in the root of the /src directory by the TypeScript compiler

EOF
npm dedupe
```

### Modify files

#### [./.yo-rc.json](./.yo-rc.json)

Update version in .yo-rc.json:

```json
{
  "@microsoft/generator-sharepoint": {
    "version": "1.7.1"
  }
}
```

Update isDomainIsolated in .yo-rc.json:

```json
{
  "@microsoft/generator-sharepoint": {
    "isDomainIsolated": false
  }
}
```

#### [.vscode\launch.json](.vscode\launch.json)

In the .vscode/launch.json file, for each configuration, in the sourceMapPathOverrides property, add "webpack:///.././src/*": "${webRoot}/src/*":

```json
{
  "configurations": [
    {
      "sourceMapPathOverrides": {
        "webpack:///.././src/*": "${webRoot}/src/*"
      }
    }
  ]
}
```

In the .vscode/launch.json file, for each configuration, in the sourceMapPathOverrides property, add "webpack:///.././src/*": "${webRoot}/src/*":

```json
{
  "configurations": [
    {
      "sourceMapPathOverrides": {
        "webpack:///.././src/*": "${webRoot}/src/*"
      }
    }
  ]
}
```

#### [./config/package-solution.json](./config/package-solution.json)

Update package-solution.json isDomainIsolated:

```json
{
  "solution": {
    "isDomainIsolated": false
  }
}
```

#### [./tsconfig.json](./tsconfig.json)

Update tsconfig.json outDir value:

```json
{
  "compilerOptions": {
    "outDir": "lib"
  }
}
```

Update tsconfig.json include property:

```json
{
  "include": [
    "src/**/*.ts"
  ]
}
```

Update tsconfig.json exclude property:

```json
{
  "exclude": [
    "node_modules",
    "lib"
  ]
}
```
