---
title: JavaScript IntelliSense
ms.date: 06/28/2017
ms.topic: conceptual
ms.technology: vs-javascript
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d2459c9ab7b6dc6e49bbbe86729d25a2adb5bdb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593717"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

Visual Studio poskytuje výkonné prostředí pro úpravu JavaScriptu přímo ze seznamu. Služba Visual Studio využívá službu založenou na TypeScript, nabízí bohatou technologii IntelliSense, podporu moderních funkcí JavaScriptu a vylepšené funkce produktivity, jako je jít na definici, refaktoring a další.

> [!NOTE]
> Počínaje verzí Visual Studio 2017 používá služba jazyka JavaScript nový modul pro jazykovou službu (označovanou jako "Salsa"). Podrobnosti jsou uvedené v tomto článku a můžete si také přečíst tento [Blogový příspěvek](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/). Nové prostředí pro úpravy platí i pro Visual Studio Code. Další informace najdete v [dokumentaci vs Code](https://code.visualstudio.com/docs/languages/javascript) .

Další informace o obecných funkcích technologie IntelliSense v aplikaci Visual Studio naleznete v tématu [Using IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Co je nového ve službě jazyka JavaScript v aplikaci Visual Studio 2017

Počínaje verzí Visual Studio 2017 JavaScript IntelliSense zobrazí další informace o parametrech a seznamech členů. Tyto nové informace poskytuje služba jazyka TypeScript, která používá statickou analýzu na pozadí pro lepší pochopení kódu.

TypeScript používá několik zdrojů k sestavení těchto informací:

- [IntelliSense na základě odvození typu](#TypeInference)
- [IntelliSense na základě JSDoc](#JsDoc)
- [IntelliSense na základě souborů deklarací TypeScript](#TsDeclFiles)
- [Automatické získání definic typů](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>IntelliSense na základě odvození typu

Ve většině případů nejsou k dispozici žádné explicitní informace o typu v jazyce JavaScript. Donovanovo je obvykle poměrně snadné zjistit typ daného okolního kontextu kódu.
Tento proces se nazývá odvození typu.

Pro proměnnou nebo vlastnost je typ obvykle typ hodnoty používané k jeho inicializaci nebo poslední přiřazení hodnoty.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Pro funkci je možné návratový typ odvodit z příkazů Return.

Pro parametry funkce není aktuálně odvozen, ale existují způsoby, jak tento problém obejít pomocí souborů JSDoc nebo TypeScript *. d. TS* (viz pozdější části).

Kromě toho je k dispozici speciální odvození pro následující:

- Třídy "ES3-Style" zadané pomocí funkce konstruktoru a přiřazení k vlastnosti Prototype.
- Vzory modulu ve stylu CommonJS zadané jako přiřazení vlastností objektu `exports` nebo přiřazení vlastnosti `module.exports`.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

<a name="JsDoc"></a>

### <a name="intellisense-based-on-jsdoc"></a>IntelliSense na základě JSDoc

Tam, kde odvození typu neposkytuje požadované informace o typu (nebo podpora dokumentace), mohou být informace o typu poskytnuty explicitně prostřednictvím poznámek JSDoc.  Chcete-li například poskytnout částečně deklarovaný objekt konkrétnímu typu, můžete použít značku `@type`, jak je znázorněno níže:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Jak bylo zmíněno, parametry funkcí nejsou nikdy odvozeny. Nicméně pomocí značky `@param` JSDoc můžete také přidat typy do parametrů funkce.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

V této části se v [JavaScriptu podpora JSDoc](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) pro anotace JSDoc aktuálně podporuje.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>IntelliSense na základě souborů deklarací TypeScript

Vzhledem k tomu, že JavaScript a TypeScript jsou teď založené na stejné jazykové službě, můžou s nimi pracovat snadněji. Například JavaScript IntelliSense lze poskytnout pro hodnoty deklarované v souboru *. d. TS* (viz [dokumentace TypeScript](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)) a typy jako rozhraní a třídy deklarované v TypeScript jsou k dispozici pro použití jako typy v komentářích JSDoc.

Níže uvádíme jednoduchý příklad definičního souboru TypeScript, který poskytuje tyto informace o typu (přes rozhraní) do souboru JavaScriptu ve stejném projektu (pomocí značky `JsDoc`).

![Definiční soubor TypeScript](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Automatické získání definic typů

V TypeScript World má nejoblíbenější JavaScriptové knihovny svá rozhraní API popsaná v souborech *. d. TS* a nejběžnější úložiště pro tyto definice je na [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Ve výchozím nastavení se služba Salsa Language pokusí zjistit, které knihovny JavaScriptu se používají, a automaticky stáhne a odkazuje na odpovídající soubor *. d. TS* , který popisuje knihovnu, aby poskytovala bohatší IntelliSense. Soubory se stáhnou do mezipaměti, která se nachází ve složce uživatele na adrese *%localappdata%\Microsoft\TypeScript*.

> [!NOTE]
> Tato funkce je ve výchozím nastavení **zakázána** , je-li použit konfigurační soubor *tsconfig. JSON* , ale může být nastaven na hodnotu povoleno, jak je uvedeno dále níže.

V současné době automatické zjišťování funguje pro závislosti stažené z NPM (čtením souboru *Package. JSON* ), Bower (načtením souboru *Bower. JSON* ) a pro volné soubory v projektu, které odpovídají seznamu zhruba 400 nejoblíbenějších knihoven JavaScript. Například pokud máte ve svém projektu *jQuery 1.10. min. js* , soubor *jQuery. d. TS* se načte a načte, aby se zajistilo lepší prostředí pro úpravy. Tento soubor *. d. TS* nebude mít žádný vliv na váš projekt.

Pokud nechcete automatické získání použít, zakažte ho přidáním konfiguračního souboru, jak je uvedeno níže. Můžete přesto umístit definiční soubory pro použití přímo v projektu ručně.

## <a name="see-also"></a>Viz také:

- [Používání atributu IntelliSense](../ide/using-intellisense.md)
- [Podpora JavaScriptu (Visual Studio pro Mac)](/visualstudio/mac/javascript)
