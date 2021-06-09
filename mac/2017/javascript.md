---
title: JavaScript a TypeScript
description: Informace o podpoře JavaScriptu v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 5f1a400506f7766ba22ffbc1debde687b1709a21
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760923"
---
# <a name="javascript-and-typescript-support"></a>Podpora JavaScriptu a TypeScriptu

Visual Studio pro Mac poskytuje podporu pro JavaScript a TypeScript prostřednictvím zvýrazňování syntaxe, formátování kódu a IntelliSense.

![Podpora editoru TypeScript](/visualstudio/mac/media/tsjseditor-2019.gif)

Další informace o psaní JavaScriptu naleznete v tématu vytváření průvodců [kódem JavaScriptu](/scripting/javascript/writing-javascript-code) .

## <a name="adding-a-javascript-file"></a>Přidání souboru JavaScriptu

Soubory JavaScriptu se nejčastěji přidávají do ASP.NET Core projektů prostřednictvím dialogu **nový soubor** . Chcete-li přidat soubor JavaScriptu, klikněte pravým tlačítkem na projekt a přejděte na **přidat > nový soubor**:

![do projektu se přidávají nové soubory.](media/javascript-image1.png)

V dialogovém okně **nový soubor** vyberte možnost **webový > prázdný soubor JS** nebo **webový > TypeScript**. Zadejte název a pak zvolte **Nový**:

![Vytvoření nového souboru TypeScript ze šablony](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio pro Mac používá [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) k poskytnutí IntelliSense, což umožňuje inteligentní dokončování kódu, informace o parametrech a seznamy členů při psaní kódu.

Technologie IntelliSense jazyka JavaScript v Visual Studio pro Mac může být založena na odvození typu, JSDoc nebo deklaraci TypeScript.

- **Odvození typu** – typ objektu je znázorněný okolním kontextem kódu. Další informace naleznete v části sady Visual Studio na [technologii IntelliSense na základě odvození typu](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc** – při odvození typu neposkytují správné informace o typu. V těchto případech mohou být informace o typu poskytnuty explicitně [JSDoc](https://jsdoc.app/about-getting-started.html) poznámkami. Další informace naleznete v části sady Visual Studio na [technologii IntelliSense na základě JSDoc](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **Soubory deklarací TypeScript** – `.d.ts` soubory se používají k poskytnutí hodnot pro JavaScript IntelliSense. Typy deklarované v tomto souboru lze použít jako typy pro komentáře JSDoc. Další informace naleznete v části sady Visual Studio na [technologii IntelliSense na základě souborů deklarací TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) .

    ![Přidání definičního souboru TypeScript](media/javascript-image3.png)

## <a name="see-also"></a>Viz také

- [JavaScript IntelliSense (Visual Studio ve Windows)](/visualstudio/ide/javascript-intellisense)
