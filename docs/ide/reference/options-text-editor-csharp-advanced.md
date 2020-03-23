---
title: Možnosti, textový editor, C#, upřesnit
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d0e04a011612cdebebd244fc061981b713b858a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431485"
---
# <a name="options-text-editor-c-advanced"></a>Možnosti, textový editor, C#, upřesnit

Stránka **Upřesnit** možnosti slouží k úpravě nastavení pro formátování editoru, refaktoring kódu a komentáře k dokumentaci XML pro jazyk C#. Chcete-li získat přístup k této stránce možností, zvolte**Možnosti** **nástrojů** > a pak zvolte **Textový editor** > **C#** > **Upřesnit**.

> [!NOTE]
> Zde mohou být uvedeny všechny možnosti.

## <a name="analysis"></a>Analýza

- Analýza živého kódu nebo obor analýzy pozadí

   Nakonfigurujte obor analýzy pozadí pro spravovaný kód. Další informace naleznete v [tématu Postup: Konfigurace oboru analýzy živého kódu pro spravovaný kód](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Používání směrnic

- Při řazení pomocí direktiv y nejprve umístěte direktivy "Systém"

   Když je tato volba vybraná, příkaz **Odebrat a seřadit usings** v nabídce po kliknutí pravým tlačítkem myši seřadí `using` direktivy a umístí obory názvů Systém na začátek seznamu.

   Před řazením:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Po seřazení:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- Samostatné pomocí skupin direktiv

   Když je tato volba vybraná, příkaz **Odebrat a seřadit usings** v nabídce po kliknutí pravým tlačítkem myši oddělí direktivy `using` vložením prázdného řádku mezi skupinami direktiv, které mají stejný kořenový obor názvů.

   Před řazením:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Po seřazení:

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

- Navrhnout použití pro typy v sestaveních rozhraní .NET Framework
- Navrhnout použití pro typy v balíčcích NuGet

   Pokud jsou vybrány tyto možnosti, [rychlá akce](../quick-actions.md) je k `using` dispozici k instalaci balíčku NuGet a přidat direktivu pro neodkazované typy.

   ![Rychlá akce pro instalaci balíčku NuGet v sadě Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Zvýraznění

- Zvýraznění odkazů na symbol pod kurzorem

   Když je kurzor umístěn uvnitř symbolu nebo když klepnete na symbol, zvýrazní se všechny instance tohoto symbolu v souboru kódu.

## <a name="outlining"></a>Sbalování

- Zadání režimu osnovy při otevření souborů

   Když je tato volba vybraná, automaticky načrtne soubor kódu, který vytvoří sbalitelné bloky kódu. Při prvním otevření souboru #regions bloky a bloky neaktivní kód sbalí.

- Zobrazit oddělovače čar procedury

   Textový editor označuje vizuální rozsah procedur. Čára je nakreslena ve zdrojových souborech *CS* projektu v umístěních uvedených v následující tabulce:

   |Umístění ve zdrojovém souboru .cs|Příklad umístění linky|
   |---------------------------------|------------------------------|
   |Po uzavření konstrukce deklarace bloku|- Na konci třídy, struktury, modulu, rozhraní nebo výčtu<br />- Po vlastnosti, funkce nebo sub<br />- Ne mezi get a set klauzule v nemovitosti|
   |Po sadě jednořádkových konstrukcí|- Po příkazech importu před definicí typu v souboru třídy<br />- Po proměnných deklarovaných ve třídě, před všemi postupy|
   |Po deklaracích jednoho řádku (deklarace neblokové úrovně)|- Následující příkazy importu dědí příkazy, deklarace proměnných, deklarace událostí, deklarace delegátů a deklarované příkazy dll.|

## <a name="block-structure-guides"></a>Vodítka blokové struktury

Zaškrtnutím těchto políček zobrazíte tečkované svislé čáry mezi složenými závorkami (**{}**) v kódu. Potom můžete snadno zobrazit jednotlivé bloky kódu pro úroveň deklarace a konstrukce úrovně kódu.

## <a name="editor-help"></a>Nápověda k editoru

- Generovat komentáře dokumentace XML pro ///

   Když je tato volba vybraná, vloží elementy `///` XML pro komentáře dokumentace XML po zadání úvodu komentáře. Další informace o dokumentaci XML naleznete v [tématu Komentáře k dokumentaci XML (C# Programming Guide)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Viz také

- [Postup: Vložení komentářů XML pro generování dokumentace](../../ide/reference/generate-xml-documentation-comments.md)
- [Dokumentační komentáře XML (Průvodce programováním v C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentujte kód pomocí komentářů XML (Průvodce C#)](/dotnet/csharp/codedoc)
- [Nastavení možností editoru specifického pro jazyk](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
