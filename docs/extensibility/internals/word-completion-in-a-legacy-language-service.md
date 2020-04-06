---
title: Dokončení aplikace Word ve službě staršího jazyka | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703165"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Dokončování slov ve službě starší verze jazyka
Dokončení aplikace Word vyplní chybějící znaky částečně napsaného slova. Pokud existuje pouze jedno možné dokončení, slovo je dokončeno při zadání znaku dokončení. Pokud částečné slovo odpovídá více než jedné možnosti, zobrazí se seznam možných dokončení. Znak dokončení může být libovolný znak, který se nepoužívá pro identifikátory.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace naleznete v [tématu Rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="implementation-steps"></a>Prováděcí kroky

1. Když uživatel vybere **možnost Dokončit aplikaci Word** z nabídky **IntelliSense,** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> bude příkaz odeslán do jazykové služby.

2. Třída <xref:Microsoft.VisualStudio.Package.ViewFilter> zachytí příkaz a <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> volá metodu s <xref:Microsoft.VisualStudio.Package.ParseReason>důvodem analýzy .

3. Třída <xref:Microsoft.VisualStudio.Package.Source> pak volá <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu získat seznam možných dokončení slova a potom zobrazí slova <xref:Microsoft.VisualStudio.Package.CompletionSet> v seznamu tip nástroje pomocí třídy.

    Pokud existuje pouze jedno odpovídající <xref:Microsoft.VisualStudio.Package.Source> slovo, třída dokončí slovo.

   Případně pokud skener vrátí hodnotu <xref:Microsoft.VisualStudio.Package.TokenTriggers> aktivační události při zadání prvního <xref:Microsoft.VisualStudio.Package.Source> znaku identifikátoru, <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> třída to zjistí a <xref:Microsoft.VisualStudio.Package.ParseReason>zavolá metodu s důvodem analýzy . V tomto případě musí analyzátor zjistit přítomnost znaku výběru člena a poskytnout seznam členů.

## <a name="enabling-support-for-the-complete-word"></a>Povolení podpory pro úplné slovo
 Chcete-li povolit podporu `CodeSense` pro dokončování slov nastavit pojmenovaný parametr předán <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atribut uživatele přidružené k balíčku jazyka. Tím nastaví <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences> na třídu.

 Analyzátor musí vrátit seznam deklarací v reakci na hodnotu <xref:Microsoft.VisualStudio.Package.ParseReason>důvodu analýzy , pro dokončení slova pracovat.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementace úplného wordu v metodě ParseSource
 Pro dokončení slova <xref:Microsoft.VisualStudio.Package.Source> třída <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> volá metodu ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídě získat seznam možných shody slov. Je nutné implementovat seznam ve třídě, <xref:Microsoft.VisualStudio.Package.Declarations> která je odvozena z třídy. Podrobnosti <xref:Microsoft.VisualStudio.Package.Declarations> o metodách, které je nutné implementovat, naleznete ve třídě.

 Pokud seznam obsahuje pouze jedno slovo, <xref:Microsoft.VisualStudio.Package.Source> třída toto slovo automaticky vloží místo částečného slova. Pokud seznam obsahuje více než <xref:Microsoft.VisualStudio.Package.Source> jedno slovo, třída zobrazí seznam tipů nástrojů, ze kterého může uživatel vybrat příslušnou volbu.

 Podívejte se také na <xref:Microsoft.VisualStudio.Package.Declarations> příklad implementace třídy v [dokončení člena ve službě starší jazyk](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
