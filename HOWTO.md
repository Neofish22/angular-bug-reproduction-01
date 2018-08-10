Bug reproduction for bug found in @fortawesome/angular-fontawesome.

Bug
===
See https://github.com/FortAwesome/angular-fontawesome/issues/78

How I created repo
===
1
---
`ng new AngularBugReproduction01`
`ng update @angular/cli`

Test 1
---
`ng serve --watch`
(Page loads. App compiles OK on file changes.)

2
---
`npm install --save @fortawesome/angular-fontawesome @fortawesome/fontawesome-svg-core`
Add to `app.module.ts` as shown in https://fontawesome.com/how-to-use/on-the-web/using-with/angular

Test 2
---
`ng serve --watch`
(First compile works. Subsequent don't. I didn't stop the watch command from the last test and the first compile worked then. Commenting out module in app.module.ts allows it to compile again.)

3 (Optional step to show it's not other modules)
---
`npm install --save @ctrl/ngx-codemirror`
Add to `app.module.ts`:
  `import { CodemirrorModule } from '@ctrl/ngx-codemirror';`
  `CodeMirrorModule` in imports.

Test 3
---
`ng serve --watch`
(Page loads. App compiles OK on file changes.)

Problem
---
The above is what happened as I did it, but now the compiler only produces errors for ngx-codemirror, and works fine with just FontAwesome. This leads me to believe there may be a compatibility issue, or something wrong with Angular, rather than FontAwesome.
