---
title: Možnosti, textový editor, C#, upřesnit
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7cfbc6d57e5bfd3c6a8f317967448039a9b3f5e4
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670712"
---
# <a name="options-text-editor-c-advanced"></a>Možnosti, textový editor, C#, upřesnit

Použití **Upřesnit** stránka Možnosti, chcete-li změnit nastavení editoru formátování, refaktoringu kódu a komentáře dokumentace XML pro jazyk C#. Chcete-li získat přístup k této stránce Možnosti, zvolte **nástroje** > **možnosti**a klikněte na tlačítko **textový Editor** > **jazyka C#**  >  **Advanced**.

> [!NOTE]
> Ne všechny možnosti mohou být uvedeny zde.

## <a name="analysis"></a>Analýza

- Povolení úplné analýzy řešení

   Umožňuje analýzu kódu u všech souborů v řešení, ne jenom otevřít soubory kódu. Další informace najdete v tématu [úplné analýzy řešení](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Direktivy using

- Umístit nejdřív direktivy "System", při řazení direktiv Using

   Pokud je vybráno, **odebrat a seřadit direktivy using** příkaz v nabídce seřadí klikněte pravým tlačítkem `using` direktivy a místa obory názvů "Systém" v horní části seznamu.

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
   
- Oddělovat skupiny direktiv using

   Pokud je vybráno, **odebrat a seřadit direktivy using** odděluje příkazu v místní nabídce `using` direktivy vložením prázdný řádek mezi skupinami direktivy, které mají stejný obor názvů root.

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
   
- Navrhnout použití typů v sestaveních reference 
- Navrhnout použití typů v balíčcích NuGet 

   Když tyto možnosti jsou vybrané, [rychlá akce](../quick-actions.md) je k dispozici pro instalaci balíčku NuGet a přidejte `using` směrnice pro neodkazovaný typy.

   ![Rychlé akce pro instalaci balíčku NuGet v sadě Visual Studio](media/nuget-lightbulb.png)
  
## <a name="highlighting"></a>Zvýraznění

- Zvýrazňovat odkazy na _symbol pod kurzorem

   Když se kurzor uvnitř symbol, nebo když kliknete na symbol, jsou zvýrazněny všechny instance tohoto symbolu v souboru kódu.

## <a name="outlining"></a>Sbalování

- Po otevření souborů vstoupit do režimu sbalování

   Pokud je vybráno, automaticky popisuje, jak soubor kódu, který vytvoří sbalitelnou bloky kódu. Při prvním otevření souboru #regions bloky a bloky neaktivního kódu sbalte.

- Zobrazit oddělovače řádků procedury

   Textový editor označuje visual oboru postupy. Řádek je vykreslen v *.vb* zdrojové soubory vašeho projektu v umístěních uvedených v následující tabulce:

   |Umístění ve zdrojovém souboru .vb|Příklad umístění řádku|
   |---------------------------------|------------------------------|
   |Po uzavření bloku deklarace konstruktoru|– Na konci třída, struktura, modul, rozhraní nebo výčet<br />-After vlastnost, funkce nebo procedury sub<br />-Není mezi get a set klauzule ve vlastnosti|
   |Po sadu konstrukce jeden řádek|-After příkazy pro import, před definici typu v souboru třídy<br />-After proměnné deklarované ve třídě, před všechny postupy|
   |Po jeden řádek deklarací (deklarace mimo blok úrovně)|-Následující příkazy pro import, dědí příkazy deklarace proměnných, deklarace události, delegát deklarace a příkazy deklarovat knihovny DLL|

## <a name="editor-help"></a>Nápověda k editoru

- Generování komentářů k dokumentaci XML pro / / / / /

   Pokud je vybráno, vloží prvky XML pro dokumentační komentáře XML po zadání `///` Úvod komentář. Další informace o dokumentaci XML, naleznete v tématu [XML – dokumentační komentáře (C# Programming Guide)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Viz také:

- [Postupy: vložení komentáře XML pro generování dokumentace](../../ide/reference/generate-xml-documentation-comments.md)
- [XML – dokumentační komentáře (C# Programming Guide)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentaci kódu pomocí komentářů XML (Průvodce v C#)](/dotnet/csharp/codedoc)
- [Nastavení možností editoru pro konkrétní jazyk](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
