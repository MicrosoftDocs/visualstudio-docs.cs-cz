---
title: JavaScript v sadě Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/10/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: bowdenk7
ms.author: wilkelly
manager: ghogen
ms.openlocfilehash: 75c234b2a3b16d3bcbe05da9f0818c73be0412db
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880771"
---
# <a name="javascript-in-visual-studio-2017"></a>JavaScript v sadě Visual Studio 2017

JavaScript je prvotřídní jazyk v sadě Visual Studio. Při psaní kódu v jazyce JavaScript v sadě Visual Studio IDE můžete použít téměř všechny standardní editační pomůcky (fragmenty kódu, funkci IntelliSense atd.). Můžete napsat kód jazyka JavaScript pro mnoho typů aplikací a služeb.

> [!NOTE]
> Jsme se připojili k celé komunitě úsilí, aby [MDN web dokumentace](https://developer.mozilla.org/en-US/) komplexní, vedoucí vývoje prostředků na webu, přesměrováním všechny (víc než 500 stránky) reference k rozhraní API jazyka JavaScript společnosti Microsoft z webu docs.microsoft.com pro své zprávy MDN. protějšky. Podrobnosti najdete v tomto [oznámení](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/).

## <a name="ES6"></a> Podporu pro ECMAScript 2015 (ES6) a další

Visual Studio teď podporuje syntaxi pro aktualizace jazyka ECMAScript například ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>Co je ECMAScript 2015?

JavaScript se dál vyvíjejí jako programovací jazyk a [TC39](http://www.ecma-international.org/memento/TC39.htm) zodpovídá výbor pro provedení aktualizací.
ECMAScript 2015 je aktualizace, která přináší užitečné novou syntaxi a funkce jazyka JavaScript. Podrobné informace o funkcích ES6, projděte si [to](http://es6-features.org) referenční webový server.

Kromě podporu pro ECMAScript 2015 Visual Studio také podporuje ECMAScript 2016 a bude zahrnovat podporu pro budoucí verze ECMAScript při jejich vydání. Jak držet krok s TC39 a nejnovější změny v ECMAScript, sledujte práci na [githubu](https://github.com/tc39).

### <a name="transpile-javascript"></a>Transpiluje JavaScript

Běžný problém s použitím jazyka JavaScript je, že chcete používat nejnovější funkce jazyků ES6 + vzhledem k tomu, že vám pomohly zvýšit produktivitu, ale prostředí modulu runtime (často prohlížeče) zatím nepodporují tyto nové funkce. To znamená, že buď muset udržovat přehled o které prohlížeče podporujete funkcích (která může být pracná), nebo pokud potřebujete způsob, jak převést váš kód ES6 + na verzi, že vaše cílové prostředí runtime pochopit (obvykle ES5). Převod vašeho kódu na verzi, která modul runtime, rozumí se obvykle označuje jako "transpiling".

Jednou z klíčových funkcí TypeScript je možnost transpiluje ES6 + kódu ES5 nebo ES3, takže můžete napsat kód, který vám umožňuje být nejproduktivnější, ale stále svůj kód spustit na libovolné platformě. Protože jazyk JavaScript v [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] používá stejný jazyk služby jako TypeScript, příliš může trvat výhod ES6 + ES5 transpilation.

Než transpilation můžete nastavit, vyžaduje se některé pochopení možností konfigurace.
TypeScript je nakonfigurovaný přes `tsconfig.json` souboru.
Chybí tento soubor se používají výchozí hodnoty.
Z důvodu kompatibility se liší v kontextu tam, kde je to jenom tyto výchozí hodnoty soubory jazyka JavaScript (a volitelně `.d.ts` soubory) jsou k dispozici.
Pro kompilaci souborů JavaScript `tsconfig.json` soubor musí být přidán, a některé z těchto možností musí být explicitně nastaveno.

Požadovaná nastavení pro souboru tsconfig jsou následující:

 - `allowJs`: Tato hodnota musí být nastavená na `true` pro soubory jazyka JavaScript, chcete-li rozpoznán. Výchozí hodnota je `false`, protože zkompiluje TypeScript pro JavaScript a kompilátor by neměl obsahovat soubory, které je zkompilován.
 - `outDir`: Tato hodnota měla nastavit na umístění není zahrnutý v projektu, aby emitovaný souborů JavaScriptu nejsou zjištěny a pak zahrnutý v projektu (viz `exclude`).
 - `module`: Pokud používáte moduly, toto nastavení instruuje kompilátor, který formát modulu emitovaný kód by měl používat (třeba `commonjs` pro uzel nebo to software instalující například Browserify).
 - `exclude`: Toto nastavení stavy které složky nechcete zahrnout do projektu.
 Umístění výstupu, jakož i mimo projekt složky jako `node_modules` nebo `temp`, by se měl přidat k tomuto nastavení.
 - `enableAutoDiscovery`: Toto nastavení umožňuje automatické zjišťování a stahování souborů definice, jak je uvedeno dříve.
 - `compileOnSave`: Toto nastavení instruuje kompilátor, pokud by měl znovu zkompilovat pokaždé, když zdrojový soubor je uložen v sadě Visual Studio.
 - `typeAcquisition`: Tato sada nastavení řídí chování získání automatické typu (dále vysvětlili v [v této části](/visualstudio/ide/javascript-intellisense#Auto))

Aby bylo možné převést soubory jazyka JavaScript na moduly CommonJS a umístit je do `./out` složky, můžete použít následující `tsconfig.json` souboru:

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

S nastavením na místě, pokud zdrojový soubor (`./app.js`) existovala a obsahovala několik funkcí jazyka ECMAScript 2015 následujícím způsobem:

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

Pak soubor by měl vyzařovaného k `./out/app.js` cílení na ECMAScript 5 (výchozí), která vypadá nějak takto:

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

## <a name="better-intellisense"></a>Vylepšení IntelliSense

Technologie IntelliSense jazyka JavaScript v [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] bude nyní zobrazit mnohem víc o parametry a seznamech členů. Služba jazyka TypeScript, který používá statickou analýzu na pozadí pro lepší pochopení kódu poskytuje tyto nové informace. Můžete si přečíst další informace o nové prostředí IntelliSense a jak to funguje [tady](/visualstudio/ide/javascript-intellisense/).

## <a name="JSX"></a> Podpora syntaxi JSX

JavaScript v [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] má bohatou podporu pro syntaxi JSX. JSX je sada syntaxe, která umožňuje značek HTML v rámci soubory jazyka JavaScript.

Následující obrázek znázorňuje React komponentu podle `comps.tsx` soubor TypeScript a potom tuto součást je používán z `app.jsx` souboru, bylo dokončeno s podporou technologie IntelliSense pro dokončování a dokumentace v rámci výrazy JSX.
Není nutné TypeScript tady, v tomto konkrétním příkladu prostě se to děje tak, aby obsahovala kód TypeScript.

<img src="./media/react.png" height="500" width="640"/>

> [!NOTE]
> K převodu syntaxi JSX React volání, nastavení `"jsx": "react"` musí být přidané do `compilerOptions` v `tsconfig.json` souboru.

Soubor JavaScript vytvořeno v ". / out/app.js při sestavení by obsahovat kód:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Konfigurace projektu JavaScript

Služba jazyka používá statickou analýzu, což znamená, že analyzuje zdrojový kód bez ve skutečnosti provádí ho, aby bylo možné vrátit výsledky technologie IntelliSense a poskytují další funkce pro úpravu.
Proto větší množství a velikosti souborů, které jsou zahrnuty kontext projektu, víc paměti a procesoru se použije během analýzy.
Z tohoto důvodu jsou několik výchozí předpoklady, které jsou provedeny o obrazec projektu:

- `package.json` a `bower.json` seznam závislostí ve vašem projektu a ve výchozím nastavení jsou zahrnuty v automatické získání typu (ATA)
- Nejvyšší úrovně `node_modules` složka obsahuje zdrojový kód knihovny a jeho obsah jsou vyloučené z kontext projektu ve výchozím nastavení
- Každých dalších `.js`, `.jsx`, `.ts`, a `.tsx` soubor je pravděpodobně jednou z *vlastní* zdrojové soubory a musí být zahrnuty v kontextu projektu

Ve většině případů bude moct stačí otevřít vašeho projektu a mají skvělé zkušenosti s používáním výchozí konfigurace projektu. Nicméně v projektech, které je velký nebo mají jinou složku struktury, může být žádoucí dále konfigurovat službu jazyk lépe zaměřit jenom na zdrojové soubory.

### <a name="override-defaults"></a>Přepsat výchozí hodnoty

Výchozí konfigurace můžete přepsat tak, že přidáte `tsconfig.json` soubor do kořenového adresáře projektu.
A `tsconfig.json` obsahuje celou řadu různých možností, které můžete pracovat s kontext projektu.
Několik z nich jsou uvedeny níže, ale pro úplnou sadu všechny možnosti, které jsou k dispozici, [zobrazit schéma, ukládání](http://json.schemastore.org/tsconfig).

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

Zadaný projekt s následujícím nastavením:

- zdrojové soubory projektu jsou v `wwwroot/js`
- soubory projektu knihovny lib `wwwroot/lib`
- `bootstrap`, `jquery`, `jquery-validation`, a `jquery-validation-unobtrusive` jsou uvedeny v `bower.json`
- `kendo-ui` byl ručně přidán do složky lib

![struktura složek](./media/folderStructure.png)

Můžete použít následující `tsconfig.json` k Ujistěte se, že jazyk služby pouze analyzuje vaše zdrojové soubory v `js` složku, ale stále načítá a používá `.d.ts` souborů knihoven v vaše `lib` složky.

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
# <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Řešení potíží s JavaScript language service je zakázané pro následující projekty
Když otevřete projekt jazyka JavaScript, která má velmi velké množství obsahu, může se zobrazit zpráva "služba jazyka JavaScript je zakázané pro následující projekty". Nejčastější příčinou nutnosti velmi velký objem zdrojového jazyka JavaScript je z důvodu včetně knihovny se zmírněními hrozeb zdrojový kód, který překračuje limit projektu 20 MB.

Jednoduchý způsob, jak optimalizovat váš projekt je přidat `tsconfig.json` soubor v kořenovém adresáři projektu, aby služba jazyka zjistit, které soubory jsou bezpečně ignorovat. Podle následující ukázky vyloučit nejběžnější adresáře, kde jsou uloženy knihovny:

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

Přidáte další adresáře podle svých potřeb. Příklady zahrnují "dodavatele" nebo "wwwroot/lib" adresáře. 

> [!NOTE]
> Vlastnost kompilátoru `disableSizeLimit` lze také zakázat kontrolu limit 20 MB. Opatření speciální při použití této vlastnosti, protože limit zakázat, mohou selhat, služba jazyka.

## <a name="notable-changes-from-visual-studio-2015"></a>Upozorňují na důležité změny ze sady Visual Studio 2015

Jako [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] funkce zcela nová jazyková služba, existuje pár chování, které se bude lišit nebo zcela chybět z předchozí zkušenosti.
Nejdůležitější změny jsou nahrazení VSDoc s JSDoc, odebrání vlastní `.intellisense.js` rozšíření a omezené IntelliSense pro konkrétní kódech vzorků.

### <a name="no-more-references-or-referencesjs"></a>Žádné další `///<references/>` nebo `_references.js`

Dříve bylo poměrně složité porozumět v kterémkoli daném okamžiku, které soubory byly ve vašem oboru technologie IntelliSense. Byl někdy žádoucí, aby všechny soubory v oboru a jindy nebylo, a to vedlo k komplexní konfigurace týkajících se správy ruční odkaz. Do budoucna, už nemusíte uvažovat o odkaz na správu a nepotřebujete tedy Trojitá lomítko odkazuje na komentáře nebo `_references.js` soubory.

Zobrazit [technologie IntelliSense jazyka JavaScript](/visualstudio/ide/javascript-intellisense/) stránky pro další informace o tom, jak funguje technologie IntelliSense.

### <a name="vsdoc"></a>VSDoc

Dokumentační komentáře XML, který se někdy označuje jako VSDocs, může použít dříve k vyplnění zdrojového kódu s další data, která se použije k buff výsledky technologie IntelliSense.
VSDoc se už nepodporuje nahrazený [JSDoc](http://usejsdoc.org/about-getting-started.html) tedy usnadňují zápis a přijaté standard pro jazyk JavaScript.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` Rozšíření

Dříve, můžete třeba vytvořit [rozšíření technologie IntelliSense](https://msdn.microsoft.com/library/hh874692.aspx) které by bylo možné přidat vlastní dokončení výsledky pro knihovny třetích stran.
Tato rozšíření se poměrně obtížně zápisu a instalaci a odkazy na ně byla náročnější, takže od této chvíle nová jazyková služba nebude podporovat tyto soubory.
Jako alternativu snadnější, můžete napsat definiční soubor TypeScript a poskytuje stejné výhody IntelliSense jako původní `.intellisense.js` rozšíření.
Další informace o deklaraci (`.d.ts`) vytváření souborů [tady](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Nepodporovaná vzory

Protože nová jazyková služba používá technologii statické analýzy spíše než prováděcího modulu (čtení [tento problém](https://github.com/Microsoft/TypeScript/issues/4789) informace rozdílů), existuje několik vzorových postupů jazyka JavaScript, které už můžete zjistit.
Nejběžnější vzor je vzor "expando".
Služba jazyka momentálně nemůže poskytnout technologii IntelliSense pro objekty, které mají skládaný po deklaraci vlastnosti.
Příklad:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Můžete obejít tím deklarováním vlastnosti při vytváření objektu:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Komentáře JSDoc můžete také přidat následovně:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
