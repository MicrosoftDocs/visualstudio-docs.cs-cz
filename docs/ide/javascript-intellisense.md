---
title: JavaScript IntelliSense
ms.date: 06/28/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 666ce7d65269992af486e59c6b5ce11e94da736b
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348113"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] poskytuje výkonné JavaScript předem připravené prostředí pro úpravy. Služba jazyka TypeScript, na základě, nabízí propracovanější IntelliSense, podpora pro moderní funkce JavaScript, sada Visual Studio a zvýšení produktivity, jako je přejít k definici, refaktoring, funkce a provádění dalších akcí.

> [!NOTE]
> Služba jazyka JavaScript v [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] používá nový modul pro službu jazyka (nazývané "Salsa"). Podrobnosti jsou uvedené v tomto tématu, a můžete si také přečíst to [blogový příspěvek](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/more-productive-javascript-in-visual-studio-2017-rc/). Nové možnosti úprav také většinou platí pro Visual Studio Code. Zobrazit [dokumentace VS Code](https://code.visualstudio.com/docs/languages/javascript) pro další informace.

Další informace o funkcích technologie IntelliSense, které obecné sady Visual Studio najdete v tématu [pomocí technologie IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Co je nového ve službě jazyka JavaScript v [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Počínaje [!include[vs_dev15](../misc/includes/vs_dev15_md.md)], technologie IntelliSense jazyka JavaScript zobrazí v seznamech parametrů a člen mnohem víc informací.
Služba jazyka TypeScript, který používá statickou analýzu na pozadí pro lepší pochopení kódu poskytuje tyto nové informace.
TypeScript používá několik zdrojů k vytvoření těchto informací:

- [Technologie IntelliSense podle odvození typu](#TypeInference)
- [Technologie IntelliSense podle JSDoc](#JsDoc)
- [Technologie IntelliSense na základě souborů deklarace TypeScript](#TsDeclFiles)
- [Automatické získání definic typů](#Auto)

<a name="TypeInference"></a>
### <a name="intellisense-based-on-type-inference"></a>Technologie IntelliSense podle odvození typu

V jazyce JavaScript ve většině případů není žádná explicitní typ informace k dispozici. Naštěstí se obvykle poměrně snadné zjistit, typu okolního kontext kódu.
Tento proces se nazývá odvození typu proměnné.

Pro proměnnou nebo vlastnost typ je obvykle typ hodnoty použité k inicializaci nebo poslední přiřazení hodnoty.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Funkce návratový typ lze odvodit z návratové příkazy.

Pro parametry funkce aktuálně nejsou k dispozici žádné odvození, ale existují způsoby, jak tento problém obejít použitím JSDoc nebo TypeScript *. d.ts* soubory (najdete v dalších částech).

Kromě toho je speciální odvození pro následující:

- Třídy "ES3 stylu" zadat pomocí funkce konstruktoru a přiřazení k vlastnosti prototypu.
- Vzory modul CommonJS – vizuální styl, zadaný jako vlastnost přiřazení na `exports` objektu nebo přiřazení `module.exports` vlastnost.

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
### <a name="intellisense-based-on-jsdoc"></a>Technologie IntelliSense podle JSDoc

Kde odvození typu neposkytuje informace požadovaného typu (nebo pro podporu dokumentace), informace o typu může být poskytnuta prostřednictvím poznámky JSDoc explicitně.  Pokud chcete dát částečně deklarovanému objektu určitého typu, například můžete použít `@type` označit, jak je znázorněno níže:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Jak už bylo zmíněno, jsou odvozeny nikdy parametry funkce. Avšak použití JSDoc `@param` značku, můžete přidat typy mají také parametry funkce.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Zobrazit [podpora formátu JSDoc v jazyce JavaScript](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) pro poznámky JsDoc v tuto chvíli nepodporuje.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>Technologie IntelliSense na základě souborů deklarace TypeScript

Protože jazyk JavaScript a TypeScript jsou nyní založené na stejnou službu jazyka, jsou komunikovat bohatší způsobem. Například je možné poskytnout technologii IntelliSense jazyka JavaScript pro hodnoty deklarované v *. d.ts* souboru (naleznete v tématu [TypeScript dokumentaci](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)), a jsou typy, jako jsou rozhraní a třídy deklarované v TypeScript k dispozici pro použití jako typy v komentářích JsDoc.

Níže uvádíme jednoduchý příklad TypeScript definičního souboru, který poskytuje tyto informace o typu (prostřednictvím rozhraní) do souboru jazyka JavaScript ve stejném projektu (pomocí `JsDoc` značky).

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640" alt="TypeScript definition file" />

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Automatické získání definic typů

Ve světě TypeScript Oblíbené knihovny jazyka JavaScript mají své rozhraní API popsal *. d.ts* soubory a nejběžnější úložiště pro tato definice je na [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Ve výchozím nastavení, se pokusí zjistit knihoven jazyka JavaScript se používá a automaticky stáhnout a odkaz na odpovídající službě Salsa jazyka *. d.ts* soubor, který popisuje knihovny cílem poskytnout bohatší Technologie IntelliSense. Soubory se stáhnou do mezipaměti, umístěný ve složce uživatele na *%LOCALAPPDATA%\Microsoft\TypeScript*.

> [!NOTE]
> Tato funkce je **zakázané** ve výchozím nastavení při použití *tsconfig.json* konfigurační soubor, ale může být nastaven na povoleno jak dále jsou uvedeny níže.

Automatické zjišťování v současné době používá pro závislosti stažené z npm (v článku *package.json* souboru), Bower (načtením *bower.json* souboru) a dojde ke ztrátě souborů ve vašem projektu, které odpovídají seznam z přibližně horní části 400 nejvíce Oblíbené knihovny jazyka JavaScript. Pokud máte například *jquery 1.10.min.js* ve vašem projektu, soubor *jquery.d.ts* bude načtena a načíst, aby bylo možné poskytovat lepší úprav. To *. d.ts* soubor nebude mít žádný vliv na váš projekt.

Pokud nechcete používat automatické získání, zakažte ho tak, že přidáte konfiguračního souboru, jak je uvedeno níže. Můžete stále provádět definičních souborů pro použití přímo v rámci svého projektu ručně.

## <a name="see-also"></a>Viz také:

- [Používání atributu IntelliSense](../ide/using-intellisense.md)
- [Podpora jazyka JavaScript (Visual Studio for Mac)](/visualstudio/mac/javascript)