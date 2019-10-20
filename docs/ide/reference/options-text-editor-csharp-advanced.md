---
title: Možnosti, textový editor, C#, upřesnit
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d1d540f3a49eda22973b25a6b9a91691907efe93
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666293"
---
# <a name="options-text-editor-c-advanced"></a>Možnosti, textový editor, C#, upřesnit

Stránka **Upřesnit** možnosti slouží k úpravě nastavení formátování editoru, refaktoringu kódu a dokumentačních komentářů XML pro C#. Chcete-li získat přístup k této stránce Možnosti, zvolte **nástroje**  > **Možnosti**a pak zvolte**C#** **textový editor**  >   > **Upřesnit**.

> [!NOTE]
> Ne všechny možnosti mohou být uvedeny zde.

## <a name="analysis"></a>Analýza

- Povolení úplné analýzy řešení

   Povolí analýzu kódu pro všechny soubory v řešení, nikoli pouze otevřené soubory kódu. Další informace najdete v tématu [Úplná analýza řešení](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Direktivy using

- Při řazení direktiv using umístit nejdřív direktivy System

   Pokud je tato možnost vybrána, příkazy **Remove a Sort using** v nabídce po kliknutí pravým tlačítkem myši seřadí direktivy `using` a umístí do horní části seznamu obory názvů System.

   Před řazením:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Po řazení:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- Samostatné použití skupin direktiv

   Pokud je tato možnost vybrána, příkaz **Odebrat a seřadit pomocí** v nabídce po kliknutí pravým tlačítkem myši oddělí `using` direktivy vložením prázdného řádku mezi skupiny směrnic, které mají stejný kořenový obor názvů.

   Před řazením:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Po řazení:

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

- Navrhnout použití typů v referenčních sestaveních
- Navrhnout použití typů v balíčcích NuGet

   Pokud jsou tyto možnosti vybrány, je k dispozici [rychlá akce](../quick-actions.md) pro instalaci balíčku NuGet a přidání direktivy `using` pro neodkazované typy.

   ![Rychlá akce pro instalaci balíčku NuGet v aplikaci Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Zvýrazňovač

- Zvýraznit odkazy na symbol pod kurzorem

   Když je kurzor umístěný uvnitř symbolu nebo když kliknete na symbol, zvýrazní se všechny instance daného symbolu v souboru kódu.

## <a name="outlining"></a>Sbalování

- Po otevření souborů přejít do režimu sbalení

   Když je tato možnost vybrána, automaticky popisuje soubor kódu, který vytvoří sbalitelný blok kódu. Při prvním otevření souboru #regions bloky a neaktivní bloky kódu budou sbaleny.

- Zobrazit oddělovače řádků procedury

   Textový editor označuje vizuální rozsah procedur. Řádek je vykreslen ve zdrojových souborech *. cs* projektu v umístěních uvedených v následující tabulce:

   |Umístění ve zdrojovém souboru. cs|Příklad umístění řádku|
   |---------------------------------|------------------------------|
   |Po ukončení konstrukce deklarace bloku|– Na konci třídy, struktury, modulu, rozhraní nebo výčtu<br />– Za vlastností, funkcí nebo sub<br />– Není mezi klauzulemi Get a set ve vlastnosti.|
   |Po sadě jednoduchých konstrukcí|-Po příkazech importu před definicí typu v souboru třídy<br />– Po proměnných deklarovaných ve třídě, před všemi postupy|
   |Po deklaracích s jedním řádkem (deklarace na úrovni bez blokování)|– Následující příkazy pro import dědí příkazy, deklarace proměnných, deklarace událostí, deklarace delegátů a příkazy DLL Declare.|

## <a name="block-structure-guides"></a>Vodítka struktury bloku

Zaškrtnutím těchto políček zobrazíte tečkované svislé čáry mezi složenými závorkami ( **{}** ) ve vašem kódu. Pak můžete snadno zobrazit jednotlivé bloky kódu pro vaši úroveň deklarace a konstrukce na úrovni kódu.

## <a name="editor-help"></a>Pomocník s editorem

- Generovat dokumentační komentáře XML pro///

   Když je tato možnost vybrána, vloží prvky XML pro dokumentační komentáře XML po zadání `///` Úvod do komentáře. Další informace o dokumentaci XML najdete v [dokumentaci k dokumentaci XML (C# Průvodce programováním)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Viz také:

- [Postupy: vložení komentářů XML pro generování dokumentace](../../ide/reference/generate-xml-documentation-comments.md)
- [Komentáře dokumentace XML (C# Průvodce programováním)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentování kódu pomocí komentářů XML (C# průvodce)](/dotnet/csharp/codedoc)
- [Nastavení možností editoru pro konkrétní jazyk](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
