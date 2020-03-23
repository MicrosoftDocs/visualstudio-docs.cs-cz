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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593717"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

Visual Studio poskytuje výkonné prostředí pro úpravy javascriptu ihned po vybalení. Visual Studio využívá jazykovou službu založenou na typescriptu a poskytuje bohatší technologii IntelliSense, podporu moderních funkcí JavaScriptu a vylepšené funkce produktivity, jako je Přejít na definici, refaktoring a další.

> [!NOTE]
> Počínaje Visual Studio 2017, javascriptová jazyková služba používá nový modul pro jazykovou službu (tzv. Salsa"). Podrobnosti jsou zahrnuty v tomto článku, a můžete si také přečíst tento [blog post](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/). Nové prostředí pro úpravy se také většinou vztahuje na kód sady Visual Studio. Další informace najdete v [dokumentech v kódu VS.](https://code.visualstudio.com/docs/languages/javascript)

Další informace o obecných funkcích technologie IntelliSense sady Visual Studio naleznete [v tématu Using IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Co je nového ve službě jazyka JavaScript ve Visual Studiu 2017

Počínaje Visual Studio 2017, JavaScript IntelliSense zobrazí mnohem více informací o parametrech a seznamech členů. Tyto nové informace poskytuje služba jazyka TypeScript, která používá statickou analýzu na pozadí, aby lépe porozuměla vašemu kódu.

TypeScript používá k vytvoření těchto informací několik zdrojů:

- [Technologie IntelliSense založená na odvození typu](#TypeInference)
- [Technologie IntelliSense založená na jsdoc](#JsDoc)
- [Technologie IntelliSense založená na souborech deklarací jazyka TypeScript](#TsDeclFiles)
- [Automatické pořízení definic typů](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>Technologie IntelliSense založená na odvození typu

V Jazyce JavaScript, většinu času není k dispozici žádné explicitní informace o typu. Naštěstí je obvykle poměrně snadné zjistit typ vzhledem k kontextu okolníkód.
Tento proces se nazývá odvození typu.

Pro proměnnou nebo vlastnost je typ obvykle typem hodnoty použité k inicializaci nebo nejnovějšího přiřazení hodnoty.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Pro funkci návratový typ lze odvodit z návratové příkazy.

Pro parametry funkce, je v současné době žádný závěr, ale existují způsoby, jak obejít pomocí JSDoc nebo TypeScript *.d.ts* soubory (viz další oddíly).

Kromě toho je zvláštní závěr pro následující:

- "ES3-style" třídy, určené pomocí funkce konstruktoru a přiřazení k vlastnosti prototypu.
- Vzory modulu ve stylu CommonJS, určené `exports` jako přiřazení vlastností `module.exports` na objektu nebo přiřazení k vlastnosti.

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

### <a name="intellisense-based-on-jsdoc"></a>Technologie IntelliSense založená na jsdoc

Pokud odvození typu neposkytuje informace o požadovaném typu (nebo pro podpůrnou dokumentaci), mohou být informace o typu poskytnuty explicitně prostřednictvím anotací JSDoc.  Chcete-li například poskytnout částečně deklarovanému `@type` objektu určitý typ, můžete použít značku, jak je znázorněno níže:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Jak již bylo zmíněno, parametry funkce nejsou nikdy odvodit. Pomocí značky JSDoc `@param` však můžete přidat i typy parametrů funkce.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Viz [Podpora JSDoc v JavaScriptu](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) pro aktuálně podporované poznámky JsDoc.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>Technologie IntelliSense založená na souborech deklarací jazyka TypeScript

Vzhledem k tomu, že JavaScript a TypeScript jsou nyní založeny na stejné jazykové službě, mohou pracovat bohatším způsobem. Například JavaScript IntelliSense může být poskytnutpro hodnoty deklarované v souboru *.d.ts* (viz [Dokumentace k písmu](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)) a typy, jako jsou rozhraní a třídy deklarované v TypeScriptu, jsou k dispozici pro použití jako typy v komentářích JsDoc.

Níže uvádíme jednoduchý příklad definičního souboru TypeScript, který poskytuje informace o typu (přes `JsDoc` rozhraní) do souboru JavaScript u stejného projektu (pomocí značky).

![Soubor definice jazyka TypeScript](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Automatické pořízení definic typů

Ve světě TypeScript, nejoblíbenější javascriptové knihovny mají své API popsané *soubory .d.ts* a nejběžnější úložiště pro tyto definice je na [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Ve výchozím nastavení se jazyková služba Salsa pokusí zjistit, které knihovny JavaScriptu se používají, a automaticky stáhne a naodkazuje na odpovídající soubor *.d.ts,* který popisuje knihovnu, aby poskytl bohatší technologie IntelliSense. Soubory jsou staženy do mezipaměti umístěné pod uživatelskou složkou na adrese *%LOCALAPPDATA%\Microsoft\TypeScript*.

> [!NOTE]
> Tato funkce je ve výchozím nastavení **zakázána,** pokud používáte konfigurační soubor *tsconfig.json,* ale může být nastavena na povolenou, jak je uvedeno dále níže.

V současné době auto-detekce funguje pro závislosti stažené z npm (čtením *package.json* soubor), Bower (čtením *bower.json* soubor), a pro volné soubory ve vašem projektu, které odpovídají seznamu zhruba top 400 nejpopulárnějších javascriptových knihoven. Pokud máte například v projektu *jquery-1.10.min.js,* soubor *jquery.d.ts* bude načten a načten, aby bylo možné lépe upravovat. Tento soubor *.d.ts* nebude mít žádný vliv na váš projekt.

Pokud nechcete používat automatické pořizování, zakažte jej přidáním konfiguračního souboru, jak je uvedeno níže. Stále můžete umístit definiční soubory pro použití přímo v rámci projektu ručně.

## <a name="see-also"></a>Viz také

- [Používání atributu IntelliSense](../ide/using-intellisense.md)
- [Podpora JavaScriptu (Visual Studio pro Mac)](/visualstudio/mac/javascript)
