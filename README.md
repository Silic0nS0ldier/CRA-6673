This repo aims to reproduce the issues described at https://github.com/facebook/create-react-app/issues/6673

Stack traces and code that causes them extracted from within `webpack`.

## 1
```
{ SyntaxError: 'with' in strict mode (1:99)
    at _class.pp$4.raise (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2844:13)
    at _class.pp$1.parseWithStatement (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:1110:27)
    at _class.pp$1.parseStatement (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:850:33)
    at _class.parseStatement (C:\Users\jorda\Desktop\CRA-6673\node_modules\acorn-dynamic-import\lib\index.js:63:118)
    at _class.pp$1.parseBlock (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:1167:23)
    at _class.pp$3.parseFunctionBody (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2685:22)
    at _class.pp$1.parseFunction (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:1283:8)    at _class.pp$3.parseExprAtom (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2280:17)
    at _class.parseExprAtom (C:\Users\jorda\Desktop\CRA-6673\node_modules\acorn-dynamic-import\lib\index.js:75:117)
    at _class.pp$3.parseExprSubscripts (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2126:19)
    at _class.pp$3.parseMaybeUnary (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2103:17)
    at _class.pp$3.parseExprOps (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2045:19)
    at _class.pp$3.parseMaybeConditional (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2028:19)
    at _class.pp$3.parseMaybeAssign (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2003:19)
    at _class.pp$3.parseMaybeAssign (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2013:23)
    at _class.pp$3.parseExpression (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:1968:19) pos: 99, loc: Position { line: 1, column: 99 }, raisedAt: 103 }
```
```js
var _ = require("!!../node_modules/lodash/lodash.js");module.exports = function (templateParams) { with(templateParams) {return (function(data) {
var __t, __p = '';
__p += '<!DOCTYPE html>\n<html>\n  <body>\n    <div id="root"></div>\n  </body>\n</html>\n';
return __p
})();}}
```

## 2
```
{ SyntaxError: Unexpected token (1:6)
    at _class.pp$4.raise (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2844:13)
    at _class.pp.unexpected (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:690:8)
    at _class.pp.expect (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:684:26)
    at _class.pp$1.parseImportSpecifiers (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:1592:8)
    at _class.pp$1.parseImport (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:1561:28)
    at _class.pp$1.parseStatement (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:861:47)
    at _class.parseStatement (C:\Users\jorda\Desktop\CRA-6673\node_modules\acorn-dynamic-import\lib\index.js:63:118)
    at _class.pp$1.parseTopLevel (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:749:23)
    at _class.parse (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:552:15)
    at Function.parse (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:575:35)
    at Function.parse (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\lib\Parser.js:2234:22)
    at Parser.parse (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\lib\Parser.js:2102:17)
    at doBuild.err (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\lib\NormalModule.js:460:32)
    at runLoaders (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\lib\NormalModule.js:342:12)
    at C:\Users\jorda\Desktop\CRA-6673\node_modules\loader-runner\lib\LoaderRunner.js:373:3
    at iterateNormalLoaders (C:\Users\jorda\Desktop\CRA-6673\node_modules\loader-runner\lib\LoaderRunner.js:214:10) pos: 6, loc: Position { line: 1, column: 6 }, raisedAt: 7 }
```
```js
import('./dynamic-import');
```

## 3
```
{ SyntaxError: 'import' and 'export' may appear only with 'sourceType: module' (1:0)
    at _class.pp$4.raise (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:2844:13)
    at _class.pp$1.parseStatement (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:859:16)
    at _class.parseStatement (C:\Users\jorda\Desktop\CRA-6673\node_modules\acorn-dynamic-import\lib\index.js:63:118)
    at _class.pp$1.parseTopLevel (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:749:23)
    at _class.parse (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:552:15)
    at Function.parse (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\node_modules\acorn\dist\acorn.js:575:35)
    at Function.parse (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\lib\Parser.js:2246:23)
    at Parser.parse (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\lib\Parser.js:2102:17)
    at doBuild.err (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\lib\NormalModule.js:460:32)
    at runLoaders (C:\Users\jorda\Desktop\CRA-6673\node_modules\webpack\lib\NormalModule.js:342:12)
    at C:\Users\jorda\Desktop\CRA-6673\node_modules\loader-runner\lib\LoaderRunner.js:373:3
    at iterateNormalLoaders (C:\Users\jorda\Desktop\CRA-6673\node_modules\loader-runner\lib\LoaderRunner.js:214:10)
    at iterateNormalLoaders (C:\Users\jorda\Desktop\CRA-6673\node_modules\loader-runner\lib\LoaderRunner.js:221:10)
    at C:\Users\jorda\Desktop\CRA-6673\node_modules\loader-runner\lib\LoaderRunner.js:236:3
    at context.callback (C:\Users\jorda\Desktop\CRA-6673\node_modules\loader-runner\lib\LoaderRunner.js:111:13)
    at loader.call.then.args (C:\Users\jorda\Desktop\CRA-6673\node_modules\babel-loader\lib\index.js:51:71) pos: 0, loc: Position { line: 1, column: 0 }, raisedAt: 6 }
```
```js
import('./dynamic-import');
```