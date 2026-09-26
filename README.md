# angular_modernization_source — AngularJS 1.5 application (source)

The source side of an AngularJS → Angular modernization: the **ThingsBoard 2.5
web UI**, a real, production AngularJS application, unchanged.

- **Upstream:** [thingsboard/thingsboard](https://github.com/thingsboard/thingsboard),
  branch `release-2.5`, folder `ui/`, commit `11d263b05e61f43966032c3963828cd17fb65cac` (2021-01-25).
- **License:** Apache License 2.0 (see `LICENSE`). Copyright © 2016-2020 The ThingsBoard Authors.
  The files are as upstream wrote them; only this README was added.

**Target:** the same application rewritten as an Angular 22 app is [`angular_modernization_target`](https://github.com/cognidevwb/angular_modernization_target).

## What it is

| | |
|---|---|
| Framework | AngularJS 1.5.8, ui-router 0.3.2, Angular Material 1.1 |
| Build | webpack (`npm run build`), ES2015 modules, templates imported as `*.tpl.html` |
| AngularJS modules | 124 (`thingsboard`, `thingsboard.admin`, `thingsboard.api.*`, …) |
| Registrations | 255: 112 directives, 74 controllers, 36 factories, 17 config blocks, 9 filters, 3 providers, 2 constants, 1 run block, 1 value |
| Routes | 36 ui-router states |

These numbers come from CogniDev Understand run on this repository.

## Why it is a good modernization source

- ES2015 modules: each directive or controller is an exported function,
  registered in the folder's `index.js`.
- Templates are imported (`import tpl from './x.tpl.html'`) and read through
  `$templateCache`, not `templateUrl`.
- Directives compile markup at run time (`$compile`, `element.html(...)`),
  and `scope.$watch` is used throughout.
- ui-router 0.3 states with nested views.
