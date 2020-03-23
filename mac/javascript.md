---
title: JavaScript a TypeScript
description: Informace o podpoře JavaScriptu ve Visual Studiu pro Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: d2ce3b3cdbf1a4cf1f19956a7327d73c0bb34b62
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72807145"
---
# <a name="javascript-and-typescript-support"></a>Podpora javascriptu a jazyka TypeScript

Visual Studio for Mac poskytuje podporu pro JavaScript a TypeScript prostřednictvím zvýraznění syntaxe, formátování kódu a Technologie IntelliSense.

![podpora editoru typescript](media/tsjseditor-2019.gif)

Další informace o psaní JavaScriptu najdete v [příručkách Psaní kódu javascriptu.](/scripting/javascript/writing-javascript-code)

## <a name="adding-a-javascript-file"></a>Přidání souboru JavaScriptu

Soubory JavaScriptu se nejčastěji přidávají do ASP.NET základních projektů prostřednictvím dialogového okna **Nový soubor.** Chcete-li přidat soubor javascriptu, klikněte pravým tlačítkem myši na projekt a přejděte na **Přidat > nový soubor**:

![přidání nových souborů do projektu](media/javascript-image1.png)

V dialogovém okně **Nový soubor** vyberte možnost Web > Prázdný **soubor JS** nebo **Soubor Jazyka Www >**. Dejte mu jméno a pak zvolte **Nový**:

![vytvoření nového souboru psacího stroje ze šablony](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio for Mac používá [jazykovou službu JavaScript](/visualstudio/ide/javascript-intellisense) k poskytování technologie IntelliSense, což umožňuje inteligentní dokončování kódu, informace o parametrech a seznamy členů při psaní kódu.

JavaScript IntelliSense v Visual Studiu pro Mac může být založen na odvození typu, JSDoc nebo TypeScript ových deklaracích.

- **Odvození typu** – typ objektu je vyřešován kontextem okolního kódu. Další informace naleznete v části Visual Studio na [IntelliSense na základě odvození typu](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc** – Jsou chvíle, kdy odvození typu neposkytuje správné informace o typu. V těchto případech mohou být informace o typu poskytnuty explicitně poznámky [JSDoc.](https://jsdoc.app/about-getting-started.html) Další informace naleznete v části Visual Studio na [IntelliSense založené na JSDoc](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **Soubory deklarací typescriptu** – `.d.ts` soubory se používají k poskytování hodnot pro JavaScript IntelliSense. Typy deklarované v tomto souboru lze použít jako typy v komentářích JSDoc. Další informace naleznete v části Visual Studio na [IntelliSense na základě souborů deklarací TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)

    ![přidání definičního souboru psacího stroje](media/javascript-type-intellisense-2019.gif)

## <a name="see-also"></a>Viz také

- [JavaScript IntelliSense (Visual Studio ve Windows)](/visualstudio/ide/javascript-intellisense)
