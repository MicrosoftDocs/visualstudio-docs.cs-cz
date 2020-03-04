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
ms.author: wilkelly
manager: jillfra
ms.openlocfilehash: 2a0d3657843dcf282e5c9aab8609efe5f9611965
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78234953"
---
# <a name="javascript-in-visual-studio-2017"></a>JavaScript v sadě Visual Studio 2017

JavaScript je prvotřídní jazyk v sadě Visual Studio. Při psaní kódu v jazyce JavaScript v sadě Visual Studio IDE můžete použít téměř všechny standardní editační pomůcky (fragmenty kódu, funkci IntelliSense atd.). Můžete napsat kód jazyka JavaScript pro mnoho typů aplikací a služeb.

> [!NOTE]
> Spojili jsme se s úsilím na celou komunitu, aby [webové dokumenty MDN webovým](https://developer.mozilla.org/en-US/) a vývojovým prostředkem na jednom zastavení webu. tím, že přesměruje všechny (500 + stránky) referenčních rozhraní API Microsoftu pro JavaScript z docs.Microsoft.com na své MDN protějšky. Podrobnosti najdete v tomto [oznámení](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/).

## <a name="ES6"></a>Podpora pro ECMAScript 2015 (ES6) a novější

Visual Studio teď podporuje syntaxi pro aktualizace jazyka ECMAScript, jako je například ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>Co je ECMAScript 2015?

JavaScript se stále vyvíjí jako programovací jazyk a [TC39](https://www.ecma-international.org/memento/tc39-m.htm) je výbor zodpovědný za provádění aktualizací.
ECMAScript 2015 je aktualizace jazyka JavaScriptu, který přináší užitečnou novou syntaxi a funkčnost. Podrobné informace o funkcích ES6 najdete na [tomto](http://es6-features.org/#Constants) referenčním webu.

Kromě podpory pro ECMAScript 2015 podporuje Visual Studio také ECMAScript 2016 a bude mít podporu pro budoucí verze ECMAScript při jejich vydání. Pokud chcete zachovat TC39 a nejnovější změny v ECMAScriptu, postupujte podle svých prací na [GitHubu](https://github.com/tc39).

### <a name="transpile-javascript"></a>Převýšení JavaScriptu

Běžným problémem s JavaScriptem je, že chcete používat nejnovější funkce ES6 + Language, protože vám pomůžou zvýšit produktivitu, ale běhová prostředí (často prohlížeče) tyto nové funkce ještě nepodporují. To znamená, že musíte sledovat, které prohlížeče podporují funkce (které můžou být únavné), nebo potřebujete způsob, jak převést ES6 + kód na verzi, kterou vaše cílové moduly runtime chápou (obvykle ES5). Převod kódu na verzi, kterou modul runtime zná, se běžně označuje jako "transpiling".

Jedna z klíčových funkcí TypeScript je schopnost přeES6 + kód na ES5 nebo ES3, takže můžete napsat kód, který vám dává největší produktivitu, ale pořád spustit váš kód na libovolné platformě. Protože JavaScript v [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] používá stejnou jazykovou službu jako TypeScript, může také využít výhod ES6 + až ES5 transpilation.

Aby bylo možné nastavit transpilation, jsou vyžadovány některé možnosti konfigurace.
TypeScript je nakonfigurovaný pomocí souboru `tsconfig.json`.
V případě, že takový soubor není k dispozici, jsou použity některé výchozí hodnoty.
Z důvodu kompatibility se tyto výchozí hodnoty liší v kontextu, kde jsou přítomny pouze soubory JavaScriptu (a volitelně `.d.ts` soubory).
Aby bylo možné kompilovat soubory JavaScriptu, je nutné přidat `tsconfig.json` soubor a některé z těchto možností musí být nastaveny explicitně.

Požadovaná nastavení souboru tsconfig jsou následující:

- `allowJs`: Tato hodnota musí být nastavená na `true` pro rozpoznané soubory JavaScriptu. Výchozí hodnota je `false`, protože TypeScript kompiluje do JavaScriptu a kompilátor by neměl obsahovat soubory, které právě zkompiluje.
- `outDir`: Tato hodnota by měla být nastavená na umístění, které není zahrnuté v projektu, aby se nezjistily vygenerované soubory JavaScriptu a pak se do projektu zahrnuly (viz `exclude`).
- `module`: při použití modulů toto nastavení instruuje kompilátor, který formát modulu, který generovaný kód vygeneroval (například `commonjs` pro uzel nebo to software instalující, jako je například Browserify).
- `exclude`: Toto nastavení určuje, které složky nechcete do projektu zahrnout.
Do tohoto nastavení byste měli přidat umístění výstupu i neprojektové složky, například `node_modules` nebo `temp`.
- `enableAutoDiscovery`: Toto nastavení povoluje automatickou detekci a stahování definičních souborů, jak je uvedeno dříve.
- `compileOnSave`: Toto nastavení instruuje kompilátor, pokud by měl znovu kompilovat pokaždé, když je uložen zdrojový soubor v aplikaci Visual Studio.
- `typeAcquisition`: Tato sada nastavení řídí chování automatického pořízení typu (dále Vysvětlete v [této části](/visualstudio/ide/javascript-intellisense#Auto)).

Aby bylo možné převést soubory JavaScriptu na CommonJS moduly a umístit je do složky `./out`, můžete použít následující `tsconfig.json` soubor:

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

Pokud se jedná o nastavení, pokud zdrojový soubor (`./app.js`) existoval a obsahoval několik funkcí jazyka ECMAScript 2015, jak je znázorněno níže:

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

Pak se soubor vygeneruje, aby se `./out/app.js` cílení na ECMAScript 5 (výchozí), který vypadá nějak takto:

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

JavaScript IntelliSense v [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] nyní zobrazí další informace o parametrech a seznamech členů. Tyto nové informace poskytuje služba jazyka TypeScript, která používá statickou analýzu na pozadí pro lepší pochopení kódu. Můžete si přečíst další informace o novém prostředí IntelliSense a o [tom, jak to funguje.](/visualstudio/ide/javascript-intellisense/)

## <a name="JSX"></a>Podpora syntaxe JSX

JavaScript v [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] má bohatou podporu syntaxe JSX. JSX je sada syntaxe, která umožňuje značky HTML v souborech JavaScriptu.

Následující ilustrace znázorňuje komponentu reakce, která je definována v `comps.tsx` souboru TypeScript, a poté, co je tato součást používána ze souboru `app.jsx`, dokončete s IntelliSense pro dokončení a dokumentaci v rámci výrazů JSX.
V tuto chvíli nepotřebujete TypeScript, tento konkrétní příklad se může skládat i z nějakého kódu TypeScript.

![Syntaxe JSX](../javascript/media/js-react.png)

> [!NOTE]
> Chcete-li převést syntax JSX na reagující volání, musí být nastavení `"jsx": "react"` přidáno do `compilerOptions` v souboru `tsconfig.json`.

Soubor JavaScriptu vytvořený v './out/App.js ' při sestavení by měl obsahovat kód:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Konfigurace projektu JavaScriptu

Služba jazyka používá statickou analýzu, což znamená, že analyzuje váš zdrojový kód bez skutečného spuštění, aby se vracely výsledky IntelliSense a poskytovaly další funkce úprav.
Čím větší množství a velikost souborů, které jsou součástí vašeho kontextu projektu, tím více paměti a CPU budou použity při analýze.
Z tohoto důvodu je k dispozici několik výchozích předpokladů týkajících se vašeho obrazce projektu:

- `package.json` a `bower.json` seznam závislostí používaných vaším projektem a ve výchozím nastavení jsou zahrnuté do automatického pořízení typu (ATA).
- `node_modules` složka na nejvyšší úrovni obsahuje zdrojový kód knihovny a její obsah je ve výchozím nastavení vyloučený z kontextu projektu.
- Každé jiné `.js`, `.jsx`, `.ts`a soubor `.tsx` je pravděpodobně jeden z *vašich vlastních* zdrojových souborů a musí být zahrnut v kontextu projektu.

Ve většině případů budete moci otevřít projekt a mít skvělé zkušenosti s používáním výchozí konfigurace projektu. Nicméně v projektech, které jsou velké nebo mají jiné struktury složek, může být žádoucí, aby služba Language Service byla lépe nakonfigurovaná tak, aby se lépe zaostřely jenom na vaše vlastní zdrojové soubory.

### <a name="override-defaults"></a>Přepsat výchozí

Můžete přepsat výchozí konfiguraci přidáním souboru `tsconfig.json` do kořenového adresáře projektu.
`tsconfig.json` má několik různých možností, které mohou manipulovat s kontextem projektu.
Níže jsou uvedeny některé z nich, ale úplnou sadu dostupných možností najdete v části [úložiště schémat](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>Důležité možnosti `tsconfig.json`

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

S ohledem na projekt s následujícím nastavením:

- zdrojové soubory projektu jsou `wwwroot/js`
- soubory LIB projektu jsou v `wwwroot/lib`
- `bootstrap`, `jquery`, `jquery-validation`a `jquery-validation-unobtrusive` jsou uvedeny v `bower.json`
- `kendo-ui` bylo ručně přidáno do složky lib.

![Struktura složek](../javascript/media/js-folderstructure.png)

Následující `tsconfig.json` můžete použít k ujištění, že služba jazyka analyzuje zdrojové soubory pouze ve složce `js`, ale stále načítá a používá `.d.ts` soubory pro knihovny ve složce `lib`.

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

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Řešení potíží se službou jazyka JavaScript bylo zakázáno pro následující projekty.
Když otevřete projekt JavaScriptu, který má velmi velký objem obsahu, může se zobrazit zpráva "služba jazyka JavaScript je pro následující projekty zakázaná." Nejběžnějším důvodem pro velmi velký objem zdrojů JavaScriptu je zahrnutí knihoven se zdrojovým kódem, který překračuje limit projektu 20MB.

Jednoduchým způsobem, jak optimalizovat projekt, je přidat soubor `tsconfig.json` do kořenového adresáře projektu, aby služba jazyka mohla zjistit, které soubory jsou bezpečné pro ignorování. Pomocí níže uvedeného příkladu vylučte nejběžnější adresáře, ve kterých se ukládají knihovny:

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

Přidejte další adresáře podle potřeby. Mezi další příklady patří adresáře "dodavatel" nebo "wwwroot/lib".

> [!NOTE]
> Vlastnost kompilátoru `disableSizeLimit` lze použít také k zakázání limitu kontroly 20MB. Při použití této vlastnosti Vezměte v úvahu zvláštní opatření, protože zakázáním tohoto limitu by mohlo dojít k chybě služby jazyka.

## <a name="notable-changes-from-visual-studio-2015"></a>Významné změny ze sady Visual Studio 2015

Jelikož [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] nabízí zcela novou jazykovou službu, je k dispozici několik chování, která se liší nebo nevyskytují v předchozím prostředí.
Nejvýznamnější změny jsou nahrazení VSDoc pomocí JSDoc, odebrání vlastních rozšíření `.intellisense.js` a omezení technologie IntelliSense pro konkrétní vzory kódu.

### <a name="no-more-references-or-_referencesjs"></a>Žádné další `///<references/>` ani `_references.js`

Dřív bylo poměrně komplikované pochopit, že v daném okamžiku byly soubory v oboru IntelliSense. V některých případech je žádoucí mít všechny vaše soubory v rozsahu a dalších časech a to vedlo ke složitým konfiguracím, které zahrnují ruční správu odkazů. Už nebudete muset myslet na správu odkazů, takže nepotřebujete tři lomítka s odkazy na komentáře nebo `_references.js` soubory.

Další informace o tom, jak funguje technologie IntelliSense, najdete na stránce [JavaScript IntelliSense](/visualstudio/ide/javascript-intellisense/) .

### <a name="vsdoc"></a>VSDoc

Komentáře dokumentace XML, někdy označované jako VSDocs, mohou být použity k vyplnění zdrojového kódu dalšími daty, která by se použila k buffí výsledků technologie IntelliSense.
VSDoc už není podporovaný ve prospěch [JSDoc](https://jsdoc.app/about-getting-started.html) , který je snazší psát a přijatý standard pro JavaScript.

### <a name="intellisensejs-extensions"></a>rozšíření `.intellisense.js`

Dřív jste mohli vytvořit [rozšíření IntelliSense](https://msdn.microsoft.com/library/hh874692.aspx) , která vám umožní přidat vlastní výsledky dokončení pro knihovny třetích stran.
Tato rozšíření byla poměrně obtížná při zápisu a instalaci a odkazování na ně byla nenáročná, takže nová jazyková služba nebude podporovat tyto soubory.
Jednodušší Alternativně můžete napsat definiční soubor TypeScript, který poskytuje stejné výhody IntelliSense jako stará `.intellisense.js` rozšíření.
Další informace o vytváření souborů deklarace (`.d.ts`) najdete [tady](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

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
