---
title: Možnosti, textový editor, C#, Upřesnit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f2d11e78c2402a6541bc87748ed6ba348ba80fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662323"
---
# <a name="options-text-editor-c-advanced"></a>Možnosti, textový editor, C#, upřesnit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto dialogové okno slouží k úpravě nastavení formátování editoru, refaktoringu kódu a dokumentačních komentářů XML pro jazyk Visual C#. Chcete-li získat přístup k tomuto dialogovému oknu, klikněte na tlačítko **Možnosti** v nabídce **nástroje** , rozbalte složku **textový editor** , rozbalte položku **C#** a poté klikněte na možnost **Upřesnit**.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="outlining"></a>Sbalování
 Přejít do režimu sbalení, když se otevřou soubory, když jsou vybrané, automaticky se vyberou do souboru kódu, který vytvoří sbalitelný blok kódu. Při prvním otevření souboru #regions bloky a neaktivní bloky kódu budou sbaleny.

## <a name="editor-help"></a>Pomocník s editorem
 Podtržené chyby v editoru identifikují chyby sestavení v kódu. Je-li vybrána tato možnost, jsou podtrženy vlnovkou v barvách, které mají zvláštní význam:

- Chyby analýzy jsou červené.

- Chyby sestavení jsou modré.

- Upozornění sestavení jsou zelená.

- Neplatné úpravy [úprav a pokračování](../../debugger/edit-and-continue.md) jsou fialové.

  Přesunutím ukazatele myši na podtržený segment kódu zobrazíte popis tlačítka s informacemi o chybě.

  Zobrazit sémantické chyby při kompilaci identifikují určité chyby kompilace bez explicitní kompilace, například deklarování a použití neznámého typu nebo odkazování na neznámou vlastnost.

  Zvýrazněte odkazy na symbol pod kurzorem, když je kurzor umístěn uvnitř symbolu, nebo když kliknete na symbol, všechny instance tohoto symbolu v souboru kódu jsou zvýrazněny.

## <a name="refactoring"></a>Refaktoring
 Při kontrole výsledků refaktoringu se zobrazí dialogové okno **výsledky ověření** při pokusu o refaktorování kódu, který obsahuje chyby sestavení, nebo když refaktoring způsobí, že se odkaz na kód sváže s jiným objektem, než má původní vazba.

 Upozornění na členy pomocí odkazů generovaných kompilátorem zobrazí dialogové okno s upozorněním, když se pokusíte Refaktorovat člen, který má stejný název jako odkaz generovaný kompilátorem.

## <a name="xml-documentation-comments"></a>Dokumentační komentáře XML
 Vygenerovat dokumentační komentáře XML pro///Pokud je tato možnost vybrána, vloží \<summary> počáteční a koncovou značku automaticky pro dokumentační komentáře XML po zadání komentáře pro Úvod do komentáře. Další informace o dokumentaci XML najdete v [dokumentaci k dokumentaci XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).

## <a name="implement-interface"></a>Implementovat rozhraní
 Obklopte vygenerovaný kód s #region vloží #region \<*interface name*> člena kolem metod při použití rozhraní nebo explicitního implementace rozhraní.

## <a name="organize-usings"></a>Uspořádat direktivy using
 Nejprve umístit direktivy System při řazení direktivy using, pokud je tato možnost vybrána, `System` jsou před jinými direktivami using zobrazeny direktivy using. Další informace najdete v tématu [řazení pomocí](../../misc/sort-usings.md).

## <a name="see-also"></a>Viz také
 [Dokumentace k dokumentaci XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [nastavení editoru specifického pro jazyk možnosti jazyka](../../ide/reference/setting-language-specific-editor-options.md) [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)
