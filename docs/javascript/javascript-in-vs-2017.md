---
title: JavaScript
description: Při psaní javascriptového kódu v integrovaném vývojovém prostředí (IDE Visual Studio) se dozvíte, že můžete použít většinu nebo všechny standardní pomůcky pro úpravy (fragmenty kódu, IntelliSense atd.).
ms.custom: SEO-VS-2020
ms.date: 01/15/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 79c7c13ea80e32e80d32c04052269cb814072aeb
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232905"
---
# <a name="javascript-in-visual-studio-2017"></a>JavaScript v sadě Visual Studio 2017

JavaScript je prvotřídní jazyk v Visual Studio. Při psaní kódu v jazyce JavaScript v sadě Visual Studio IDE můžete použít téměř všechny standardní editační pomůcky (fragmenty kódu, funkci IntelliSense atd.). Můžete psát javascriptový kód pro mnoho typů aplikací a služeb.

> [!NOTE]
> Připojili jsme se k celé [](https://developer.mozilla.org/en-US/) komunitě a přesměrují jsme všechny (více než 500 stránek) referenčních informací k rozhraní JavaScript API společnosti Microsoft z docs.microsoft.com na jejich protějšky MDN. Podrobnosti najdete v tomto [oznámení.](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/)

## <a name="support-for-ecmascript-2015-es6-and-beyond"></a><a name="ES6"></a> Podpora pro ECMAScript 2015 (ES6) a další

Visual Studio teď podporuje syntaxi pro aktualizace jazyka ECMAScript, například ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>Co je ECMAScript 2015?

JavaScript se stále vyvíjí jako programovací jazyk a [TC39](https://www.ecma-international.org/memento/tc39-m.htm) zodpovídá za provádění aktualizací.
ECMAScript 2015 je aktualizace jazyka JavaScript, která přináší užitečnou novou syntaxi a funkce. Další informace o funkcích ES6 najdete na [tomto referenčním](http://es6-features.org/#Constants) webu.

Kromě podpory PRO ECMAScript 2015 Visual Studio podporuje také ECMAScript 2016 a bude mít podporu pro budoucí verze ECMAScriptu, jakmile budou vydány. Pokud chcete držet postup s TC39 a nejnovějšími změnami v ECMAScriptu, postupujte podle [jejich GitHub](https://github.com/tc39).

### <a name="transpile-javascript"></a>Transpilace JavaScriptu

Běžným problémem JavaScriptu je, že chcete používat nejnovější jazykové funkce ES6+, protože vám pomůžou být produktivnější, ale vaše běhová prostředí (často prohlížeče) tyto nové funkce ještě nepodporují. To znamená, že buď musíte sledovat, které prohlížeče podporují jaké funkce (což může být zdlouhavé), nebo potřebujete způsob, jak převést kód ES6+ na verzi, které rozumí cílové moduly runtime (obvykle ES5). Převod kódu na verzi, které modul runtime rozumí, se běžně označuje jako "transpilace".

Jednou z klíčových funkcí TypeScriptu je možnost transpilovat kód ES6+ do ES5 nebo ES3, abyste mohli napsat kód, který vám zajistí nejproduktivnější práci, ale přesto váš kód spustíte na libovolné platformě. Vzhledem k tomu, že JavaScript v systému používá stejnou jazykovou službu jako TypeScript, může také využít výhod [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] transpilace ES6+ na ES5.

Před nastavením transpilace je potřeba porozumět možnostem konfigurace.
TypeScript se konfiguruje prostřednictvím `tsconfig.json` souboru.
Pokud takový soubor chybí, používají se některé výchozí hodnoty.
Z důvodů kompatibility se tato výchozí nastavení liší v kontextu, ve kterém jsou k dispozici pouze javascriptové soubory (a `.d.ts` volitelně soubory).
Ke kompilaci javascriptových souborů je nutné přidat soubor a některé z těchto možností je nutné `tsconfig.json` nastavit explicitně.

Požadovaná nastavení pro soubor tsconfig jsou následující:

- `allowJs`: Tato hodnota musí být nastavená na `true` , aby se soubory JavaScriptu rozpoznané. Výchozí hodnota je , protože TypeScript se kompiluje do JavaScriptu a kompilátor by neměl obsahovat `false` soubory, které právě zkompiloval.
- `outDir`: Tato hodnota by měla být nastavená na umístění, které není zahrnuto v projektu, aby se vygenerované soubory JavaScriptu nezjedu a pak byly zahrnuty do projektu (viz `exclude` ).
- `module`: Pokud používáte moduly, toto nastavení říká kompilátoru, který formát modulu by měl vygenerovaný kód použít (například pro `commonjs` Node nebo bundlery, jako je Browserify).
- `exclude`: Toto nastavení uvádí, které složky se nemají zahrnout do projektu.
Do tohoto nastavení by se mělo přidat výstupní umístění i složky mimo projekt, jako je `node_modules` `temp` nebo .
- `enableAutoDiscovery`: Toto nastavení umožňuje automatické zjišťování a stahování definičních souborů, jak je uvedeno výše.
- `compileOnSave`: Toto nastavení říká kompilátoru, jestli by měl znovu zkompilovat kdykoli je zdrojový soubor uložen Visual Studio.
- `typeAcquisition`: Tato sada nastavení řídí chování automatického získání typu (další vysvětlení v [této části).](../ide/javascript-intellisense.md#Auto)

Pokud chcete převést soubory JavaScriptu na moduly CommonJS a umístit je do složky, můžete `./out` použít následující `tsconfig.json` soubor:

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

Pokud zdrojový soubor ( ) existoval a obsahoval několik funkcí jazyka `./app.js` ECMAScript 2015, je po nastavení k dispozici takto:

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

Pak se vysílá soubor, který cílí na `./out/app.js` ECMAScript 5 (výchozí nastavení), který vypadá nějak takto:

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

## <a name="better-intellisense"></a>Lepší IntelliSense

JavaScript IntelliSense [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] v systému teď zobrazí mnohem více informací o parametrech a seznamech členů. Tyto nové informace poskytuje služba jazyka TypeScript, která používá statickou analýzu na pozadí k lepšímu pochopení vašeho kódu. Další informace o novém prostředí IntelliSense a o tom, jak funguje, najdete [tady.](../ide/javascript-intellisense.md)

## <a name="jsx-syntax-support"></a><a name="JSX"></a> Podpora syntaxe JSX

JavaScript v [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] systému nabízí bohatou podporu syntaxe JSX. JSX je sada syntaxe, která umožňuje značky HTML v souborech JavaScriptu.

Následující obrázek znázorňuje komponentu React definovanou v souboru TypeScript a potom tuto komponentu, která se používá ze souboru, doplněná o IntelliSense pro dokončování a dokumentaci v rámci `comps.tsx` `app.jsx` výrazů JSX.
TypeScript tady nepotřebujete, ale tento konkrétní příklad obsahuje jenom nějaký kód TypeScriptu.

![Syntaxe JSX](../javascript/media/js-react.png)

> [!NOTE]
> Pokud chcete převést syntaxi JSX React volání, musí být nastavení v souboru `"jsx": "react"` `compilerOptions` přidáno do `tsconfig.json` .

Soubor JavaScriptu vytvořený v ./out/app.js buildu by obsahoval kód:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Konfigurace projektu JavaScriptu

Služba jazyka využívá statickou analýzu, což znamená, že analyzuje váš zdrojový kód, aniž by ho skutečně spravovala, aby vrátila výsledky IntelliSense a poskytovala další funkce pro úpravy.
Proto čím větší je množství a velikost souborů, které jsou zahrnuté v kontextu projektu, tím více paměti a procesoru se použije během analýzy.
Z tohoto důvodu existuje několik výchozích předpokladů, které se vztahují k tvaru projektu:

- `package.json` a seznam závislostí používaných projektem a ve výchozím nastavení jsou `bower.json` zahrnuty v ata (Automatic Type Acquisition)
- Složka nejvyšší úrovně obsahuje zdrojový kód knihovny a její obsah je ve výchozím nastavení `node_modules` vyloučený z kontextu projektu.
- Každý jiný soubor , , a je pravděpodobně jedním z vašich vlastních zdrojových souborů a `.js` `.jsx` musí být `.ts` `.tsx` zahrnutý v kontextu projektu. 

Ve většině případů budete moct jednoduše otevřít projekt a mít skvělé prostředí s použitím výchozí konfigurace projektu. V projektech, které jsou velké nebo mají různé struktury složek, ale může být žádoucí službu jazyka nakonfigurovat tak, aby se lépe soustředily pouze na vaše vlastní zdrojové soubory.

### <a name="override-defaults"></a>Přepsání výchozích hodnot

Výchozí konfiguraci můžete přepsat přidáním `tsconfig.json` souboru do kořenového adresáře projektu.
Objekt `tsconfig.json` má několik různých možností, které mohou manipulovat s kontextem projektu.
Několik z nich je uvedeno níže, ale úplnou sadu všech dostupných možností najdete [v tématu úložiště schémat.](http://json.schemastore.org/tsconfig)

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

Projekt s následujícím nastavením:

- Zdrojové soubory projektu jsou ve `wwwroot/js`
- Soubory knihovny projektu jsou v `wwwroot/lib`
- `bootstrap`, `jquery` `jquery-validation` , a jsou uvedené `jquery-validation-unobtrusive` v `bower.json`
- `kendo-ui` byla ručně přidána do složky lib.

![Struktura složek](../javascript/media/js-folderstructure.png)

Pomocí následujícího příkladu můžete zajistit, aby služba jazyka analyzovala pouze zdrojové soubory ve složce, ale přesto načítá a používá soubory pro knihovny `tsconfig.json` `js` ve `.d.ts` `lib` složce.

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

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Řešení potíží se službou jazyka JavaScript byla zakázána pro následující projekty
Když otevřete projekt JavaScriptu s velkým množstvím obsahu, může se zobrazit zpráva s textem "Služba jazyka JavaScript byla pro následující projekty zakázaná". Nejčastější příčinou velkého množství zdrojů JavaScriptu je zahrnutí knihoven se zdrojovým kódem, které překračují limit 20 MB projektu.

Jednoduchým způsobem, jak optimalizovat projekt, je přidat soubor do kořenového adresáře projektu, aby služba jazyka věděla, které soubory lze bezpečně `tsconfig.json` ignorovat. Pomocí následující ukázky vylučte nejběžnější adresáře, ve kterých jsou uložené knihovny:

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

Podle velikosti přidejte další adresáře. Mezi další příklady patří adresáře "vendor" nebo "wwwroot/lib".

> [!NOTE]
> Vlastnost `disableSizeLimit` kompilátoru lze také použít k zakázání limitu kontroly 20 MB. Při použití této vlastnosti zvláštní opatření, protože zakázání limitu může ukončovat jazykovou službu.

## <a name="notable-changes-from-visual-studio-2015"></a>Notable Changes from Visual Studio 2015

Jako funkce zcela nové jazykové služby existuje několik chování, která se budou lišit nebo [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] chybět v předchozím prostředí.
Nejdůležitějšími změnami je nahrazení VSDoc za JSDoc, odebrání vlastních rozšíření a omezená `.intellisense.js` technologie IntelliSense pro konkrétní vzory kódu.

### <a name="no-more-references-or-_referencesjs"></a>Žádné další `///<references/>` nebo `_references.js`

Dříve bylo poměrně složité v libovolném okamžiku pochopit, které soubory byly v oboru IntelliSense. Někdy bylo žádoucí mít všechny soubory v oboru a jindy to nebylo, což vedlo ke složitým konfiguracím, které zahrnují ruční správu odkazů. Do budoucna už nemusíte přemýšlet o správě odkazů, takže nepotřebujete komentáře nebo soubory s trojitou `_references.js` lomítkem.

Další informace o tom, jak IntelliSense funguje, najdete na stránce [JavaScript IntelliSense.](../ide/javascript-intellisense.md)

### <a name="vsdoc"></a>VSDoc

Komentáře dokumentace XML, někdy označované jako VSDocs, by se dříve mohly použít k dekorování zdrojového kódu dalšími daty, která by se použila k shromažďování výsledků IntelliSense.
VSDoc se už nepodporuje ve prospěch [JSDoc,](https://jsdoc.app/about-getting-started.html) který se snadněji píše, a přijatý standard pro JavaScript.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` Rozšíření

Dříve jste mohli vytvářet rozšíření [IntelliSense,](/previous-versions/visualstudio/visual-studio-2015/ide/extending-javascript-intellisense) která by vám umožnila přidat vlastní výsledky dokončování pro knihovny třetích stran.
Zápis a instalace těchto rozšíření a jejich instalace a odkazování na ně byly poměrně obtížné, takže do budoucna nebude nová jazyková služba tyto soubory podporovat.
Jednodušší alternativou je napsat definiční soubor TypeScriptu, který bude poskytovat stejné výhody IntelliSense jako původní `.intellisense.js` rozšíření.
Další informace o vytváření souborů deklarací ( `.d.ts` ) najdete [tady.](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)

### <a name="unsupported-patterns"></a>Nepodporované vzory

Vzhledem k tomu, že je nová jazyková služba poháněna statickou analýzou, nikoli prováděcím modulem ( [Tento problém](https://github.com/Microsoft/TypeScript/issues/4789) si přečtěte z informací o rozdílech), existuje několik vzorů JavaScriptu, které už se nedají detekovat.
Nejběžnějším vzorem je vzor "expando".
V současné době služba jazyka nemůže poskytnout IntelliSense pro objekty, které mají vlastnosti po deklaraci.
Příklad:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

To lze obejít deklarováním vlastností během vytváření objektu:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Komentář JSDoc můžete také přidat následujícím způsobem:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
