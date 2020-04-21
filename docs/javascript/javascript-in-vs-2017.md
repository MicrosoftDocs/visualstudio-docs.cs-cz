---
title: JavaScript
ms.date: 01/15/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: bowdenk7
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9df1b66f1a2407d523e38cd71fc9ffa993cd2d92
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649633"
---
# <a name="javascript-in-visual-studio-2017"></a>JavaScript v sadě Visual Studio 2017

JavaScript je prvotřídní jazyk v sadě Visual Studio. Při psaní kódu v jazyce JavaScript v sadě Visual Studio IDE můžete použít téměř všechny standardní editační pomůcky (fragmenty kódu, funkci IntelliSense atd.). Můžete napsat kód JavaScript pro mnoho typů aplikací a služeb.

> [!NOTE]
> Připojili jsme se k komunitě-široký úsilí, aby se [MDN webové dokumenty](https://developer.mozilla.org/en-US/) na webu one-stop, premiéra vývoj ový zdroj, přesměrováním všech (500 + stránky) javascriptového api společnosti Microsoft odkaz z docs.microsoft.com na jejich protějšky MDN. Podrobnosti naleznete v tomto [oznámení](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/).

## <a name="support-for-ecmascript-2015-es6-and-beyond"></a><a name="ES6"></a>Podpora ecmascriptu 2015 (ES6) a dalších

Visual Studio teď podporuje syntaxi pro aktualizace jazyka ECMAScript, jako je ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>Co je ECMAScript 2015?

JavaScript se stále vyvíjí jako programovací jazyk a [TC39](https://www.ecma-international.org/memento/tc39-m.htm) je výbor odpovědný za provádění aktualizací.
ECMAScript 2015 je aktualizace jazyka JavaScript, která přináší užitečnou novou syntaxi a funkce. Podrobné informace o funkcích ES6 naleznete na [tomto](http://es6-features.org/#Constants) referenčním webu.

Kromě podpory ecmascriptu 2015 podporuje Visual Studio také ECMAScript 2016 a bude mít podporu pro budoucí verze ECMAScriptu po jejich vydání. Chcete-li držet krok s TC39 a nejnovější změny v ECMAScript, sledovat jejich práci na [github](https://github.com/tc39).

### <a name="transpile-javascript"></a>Transpile JavaScript

Běžným problémem JavaScriptu je, že chcete používat nejnovější funkce jazyka ES6+, protože vám pomohou být produktivnější, ale vaše runtime prostředí (často prohlížeče) tyto nové funkce ještě nepodporují. To znamená, že musíte buď sledovat, které prohlížeče podporují jaké funkce (což může být únavné), nebo potřebujete způsob, jak převést kód ES6 + na verzi, které vaše cílové běhové časy rozumí (obvykle ES5). Převod kódu na verzi, které běhový čas rozumí, se běžně označuje jako "transpilování".

Jednou z klíčových vlastností TypeScriptu je schopnost transpile ES6 + kód ES5 nebo ES3, takže můžete napsat kód, který vás činí nejproduktivnější, ale stále spustit kód na libovolné platformě. Vzhledem k [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] tomu, že JavaScript v používá stejnou jazykovou službu jako TypeScript, může také využít transpilaci ES6+ na ES5.

Před transpilací je nutné určitě porozumět možnostem konfigurace.
TypeScript je konfigurován `tsconfig.json` prostřednictvím souboru.
V případě, že takový soubor, některé výchozí hodnoty se používají.
Z důvodů kompatibility se tyto výchozí hodnoty liší v kontextu, `.d.ts` kde jsou k dispozici pouze soubory JavaScriptu (a volitelně soubory).
Chcete-li kompilovat `tsconfig.json` soubory JavaScript, musí být přidán soubor a některé z těchto možností musí být nastaveny explicitně.

Požadovaná nastavení pro soubor tsconfig jsou následující:

- `allowJs`: Tato hodnota musí `true` být nastavena na hodnotu, aby byly rozpoznány soubory JavaScriptu. Výchozí hodnota `false`je , protože TypeScript kompiluje do Jazyka JavaScript a kompilátor by neměl obsahovat soubory, které právě zkompiloval.
- `outDir`: Tato hodnota by měla být nastavena na umístění, které není zahrnuto v projektu, aby emitované soubory JavaScript nebyly detekovány a poté zahrnuty do projektu (viz). `exclude`
- `module`: Pokud používáte moduly, toto nastavení říká kompilátoru, `commonjs` který formát modulu emitovaný kód by měl používat (například pro Uzel, nebo bundlers jako Browserify).
- `exclude`: Toto nastavení uvádí, které složky nemají být zahrnuty do projektu.
Do tohoto nastavení by mělo být přidáno výstupní umístění, stejně jako složky, které nejsou projektové, například `node_modules` nebo `temp`, .
- `enableAutoDiscovery`: Toto nastavení umožňuje automatickou detekci a stahování definičních souborů, jak je uvedeno výše.
- `compileOnSave`: Toto nastavení informuje kompilátor, pokud by měl překompilovat kdykoli je zdrojový soubor uložen v sadě Visual Studio.
- `typeAcquisition`: Tato sada nastavení řídí chování automatického pořizování typů (dále [vysvětlete](../ide/javascript-intellisense.md#Auto)v této části)

Chcete-li převést soubory JavaScript u modulů CommonJS a umístit je do `./out` složky, můžete použít následující `tsconfig.json` soubor:

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typeAcquisition": {
    "enable": true
  }
}
```

S nastavením na místě, pokud`./app.js`zdrojový soubor ( ) existoval a obsahoval několik funkcí jazyka ECMAScript 2015 takto:

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
```

Pak soubor by být `./out/app.js` emitovány na cílení ECMAScript 5 (výchozí), který vypadá podobně jako následující:

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
```

## <a name="better-intellisense"></a>Lepší technologie IntelliSense

JavaScript IntelliSense [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] v nyní zobrazí mnohem více informací o parametrech a seznamech členů. Tyto nové informace poskytuje služba jazyka TypeScript, která používá statickou analýzu na pozadí, aby lépe porozuměla vašemu kódu. Další informace o novém prostředí Technologie IntelliSense a o tom, jak [funguje, naleznete zde](/visualstudio/ide/javascript-intellisense/).

## <a name="jsx-syntax-support"></a><a name="JSX"></a>Podpora syntaxe JSX

JavaScript [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] v má bohatou podporu pro syntaxi JSX. JSX je syntaktická sada, která umožňuje html tagy v javascriptových souborech.

Následující obrázek znázorňuje komponentu React definovanou `comps.tsx` v souboru `app.jsx` TypeScript a poté tuto komponentu používanou ze souboru, doplněnou o technologie IntelliSense pro dokončení a dokumentaci v rámci výrazů JSX.
Nepotřebujete TypeScript zde, tento konkrétní příklad jen náhodou obsahují některé Kód Jazyka.

![Syntaxe JSX](../javascript/media/js-react.png)

> [!NOTE]
> Chcete-li převést syntaxi JSX `"jsx": "react"` na volání `compilerOptions` React, `tsconfig.json` musí být nastavení přidáno do souboru.

Soubor JavaScript vytvořený na './out/app.js' na sestavení by obsahoval kód:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Konfigurace projektu JavaScriptu

Služba jazyka je poháněna statickou analýzou, což znamená, že analyzuje zdrojový kód, aniž by jej skutečně prováděla, aby vrátila výsledky Technologie IntelliSense a poskytla další funkce pro úpravy.
Proto větší množství a velikost souborů, které jsou zahrnuty kontext projektu, tím více paměti a procesoru budou použity během analýzy.
Z tohoto důvodu existuje několik výchozí předpoklady, které jsou provedeny o obrazec projektu:

- `package.json`a `bower.json` seznam závislostí používaných v projektu a ve výchozím nastavení jsou zahrnuty v automatické matné pořízení typu (ATA)
- Složka nejvyšší `node_modules` úrovně obsahuje zdrojový kód knihovny a její obsah je ve výchozím nastavení vyloučen z kontextu projektu.
- Každý `.js`druhý `.jsx` `.ts`soubor `.tsx` , , a soubor je pravděpodobně jedním z *vašich vlastních* zdrojových souborů a musí být zahrnut do kontextu projektu

Ve většině případů budete moci pouze otevřít projekt a mít velké zkušenosti s použitím výchozí konfigurace projektu. Však v projektech, které jsou velké nebo mají různé struktury složek, může být žádoucí dále nakonfigurovat službu jazyka lépe zaměřit pouze na vlastní zdrojové soubory.

### <a name="override-defaults"></a>Přepsat výchozí hodnoty

Výchozí konfiguraci můžete přepsat přidáním souboru `tsconfig.json` do kořenového adresáře projektu.
A `tsconfig.json` má několik různých možností, které mohou manipulovat s kontextem projektu.
Několik z nich jsou uvedeny níže, ale pro úplnou sadu všech dostupných možností, [viz úložiště schématu](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>Důležité `tsconfig.json` možnosti

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

### <a name="example-project-configuration"></a>Příklad konfigurace projektu

Daný projekt s následujícím nastavením:

- zdrojové soubory projektu jsou`wwwroot/js`
- soubory lib projektu jsou v`wwwroot/lib`
- `bootstrap`, `jquery` `jquery-validation`, `jquery-validation-unobtrusive` , a jsou uvedeny v seznamu`bower.json`
- `kendo-ui`byl ručně přidán do složky lib

![Struktura složek](../javascript/media/js-folderstructure.png)

Pomocí následujících `tsconfig.json` možností můžete zajistit, aby jazyková služba `js` analyzovala pouze zdrojové `.d.ts` soubory ve složce, `lib` ale přesto načítá a používá soubory pro knihovny ve složce.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "noEmit": true
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Poradce při potížích Jazyková služba JavaScript u následujících projektů byla zakázána.
Když otevřete projekt JavaScriptu, který má velmi velké množství obsahu, může se zobrazí zpráva "Jazyková služba JavaScript u následujících projektů byla zakázána". Nejčastějším důvodem pro velmi velké množství zdroje JavaScript je kvůli zahrnutí knihoven se zdrojovým kódem, který přesahuje limit projektu 20 MB.

Jednoduchý způsob, jak optimalizovat projekt `tsconfig.json` je přidat soubor v kořenovém adresáři projektu, aby jazyková služba vědět, které soubory jsou bezpečné ignorovat. Následující ukázka slouží k vyloučení nejběžnějších adresářů, ve kterých jsou uloženy knihovny:

```json
{
  "compilerOptions": {
    "allowJs": true,
    "allowSyntheticDefaultImports": true,
    "maxNodeModuleJsDepth": 2,
    "noEmit": true,
    "skipLibCheck": true
  },
  "exclude": [
    "**/bin",
    "**/bower_components",
    "**/jspm_packages",
    "**/node_modules",
    "**/obj",
    "**/platforms"
  ]
}
```

Přidejte další adresáře, jak uznáte za vhodné. Některé další příklady zahrnují adresáře "dodavatel" nebo "wwwroot/lib".

> [!NOTE]
> Kompilátor `disableSizeLimit` vlastnost lze také zakázat limit kontroly 20 MB. Při použití této vlastnosti provázte zvláštní opatření, protože zakázání limitu může dojít k selhání jazykové služby.

## <a name="notable-changes-from-visual-studio-2015"></a>Významné změny z Visual Studia 2015

Jako [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] funkce zcela nové jazykové služby, existuje několik chování, které se bude lišit nebo chybí z předchozízkušenosti.
Nejpozoruhodnější změny jsou nahrazení VSDoc s JSDoc, `.intellisense.js` odstranění vlastních rozšíření a omezené IntelliSense pro konkrétní vzory kódu.

### <a name="no-more-references-or-_referencesjs"></a>Žádné `///<references/>` další nebo`_references.js`

Dříve bylo poměrně složité pochopit v daném okamžiku, které soubory byly ve vašem oboru IntelliSense. Někdy bylo žádoucí mít všechny soubory v oboru a jindy to nebylo, což vedlo ke složitým konfiguracím zahrnujícím ruční správu odkazů. Do budoucna již nemusíte přemýšlet o správě odkazů, a proto nepotřebujete trojité lomítko odkazy komentáře nebo `_references.js` soubory.

Další informace o tom, jak technologie IntelliSense funguje, najdete na stránce [JavaScript IntelliSense.](/visualstudio/ide/javascript-intellisense/)

### <a name="vsdoc"></a>VSDoc

Komentáře k dokumentaci XML, někdy označované jako VSDocs, mohly být dříve použity k dekoraci zdrojového kódu dalšími daty, která by byla použita k vylepšování výsledků technologie IntelliSense.
VSDoc již není podporován ve prospěch [JSDoc,](https://jsdoc.app/about-getting-started.html) který je jednodušší psát a přijatý standard pro JavaScript.

### <a name="intellisensejs-extensions"></a>`.intellisense.js`Rozšíření

Dříve jste mohli vytvářet [rozšíření IntelliSense,](https://msdn.microsoft.com/library/hh874692.aspx) která by vám umožnila přidat vlastní výsledky dokončení pro knihovny třetích stran.
Tato rozšíření byla poměrně obtížné psát a instalace a odkazování na ně bylo těžkopádné, takže do budoucna nová jazyková služba nebude podporovat tyto soubory.
Jako jednodušší alternativu můžete napsat definiční soubor TypeScript, abyste poskytli `.intellisense.js` stejné výhody technologie IntelliSense jako stará rozšíření.
Další informace o vytváření`.d.ts`souborů deklarací [naleznete zde](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Nepodporované vzory

Vzhledem k tomu, že nová jazyková služba je poháněna statickou analýzou spíše než prováděcím strojem (přečtěte si [tento problém](https://github.com/Microsoft/TypeScript/issues/4789) pro informace o rozdílech), existuje několik vzorů JavaScriptu, které již nelze zjistit.
Nejběžnějším vzorem je vzor "expando".
V současné době služba jazyka nemůže poskytovat technologie IntelliSense u objektů, které mají vlastnosti připnuté po deklaraci.
Příklad:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Můžete obejít tím, že deklaruje vlastnosti během vytváření objektu:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Můžete také přidat komentář JSDoc takto:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
