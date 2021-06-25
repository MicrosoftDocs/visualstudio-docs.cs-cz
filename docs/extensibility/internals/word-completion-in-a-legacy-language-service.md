---
title: Dokončování slov ve službě starší verze | Microsoft Docs
description: Dokončování slov může být podporováno pro službu starší verze jazyka v Visual Studio SDK. Zjistěte, jak jsou služby starší verze jazyka implementovány v balíčky VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea386aea3a17b0fb0d93ff9872f92e86a166be5c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902628"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Dokončování slov ve službě starší verze jazyka
Dokončování slov vyplní chybějící znaky u částečně typovaných slov. Pokud je k dispozici pouze jedno možné dokončení, slovo se dokončí při zadání znaku dokončení. Pokud částečné slovo odpovídá více než jedné možnosti, zobrazí se seznam možných dokončení. Znak dokončení může být libovolný znak, který se pro identifikátory nepouží.

 Služby starší verze jazyka jsou implementovány jako součást balíčku VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace najdete v tématu [Rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme, abyste nové rozhraní API editoru začali používat co nejdříve. Tím se zlepší výkon služby jazyka a umožní vám to využívat nové funkce editoru.

## <a name="implementation-steps"></a>Postup implementace

1. Když uživatel v nabídce **IntelliSense** vybere Complete **Word** (Dokončit word), <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> příkaz se odesílá do služby jazyka.

2. Třída <xref:Microsoft.VisualStudio.Package.ViewFilter> zachytí příkaz a <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> zavolá metodu s důvodem parsování <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. Třída pak zavolá metodu , aby získejte seznam možných dokončování slov, a pak pomocí třídy zobrazí slova v seznamu <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.CompletionSet> tipů.

    Pokud existuje pouze jedno odpovídající slovo, <xref:Microsoft.VisualStudio.Package.Source> třída toto slovo dokončí.

   Případně pokud skener vrátí hodnotu triggeru při zadání prvního znaku identifikátoru, třída to zjistí a zavolá metodu s důvodem <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> parsování <xref:Microsoft.VisualStudio.Package.ParseReason> . V takovém případě musí analyzátor rozpoznat přítomnost znaku výběru členu a poskytnout seznam členů.

## <a name="enabling-support-for-the-complete-word"></a>Povolení podpory pro úplné slovo
 Pokud chcete povolit podporu dokončování slov, nastavte pojmenovaný parametr předaný `CodeSense` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributu user přidruženému k jazykovému balíčku. Tím se <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> nastaví vlastnost třídy <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

 Analyzátor musí vrátit seznam deklarací v reakci na hodnotu důvodu parsování, aby bylo <xref:Microsoft.VisualStudio.Package.ParseReason> dokončování slov fungovat.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementace kompletního slova v metodě ParseSource
 Pro dokončování slov volá třída metodu ve třídě , aby <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> získala seznam možných shod slov. Seznam je nutné implementovat ve třídě, která je odvozena z <xref:Microsoft.VisualStudio.Package.Declarations> třídy. Podrobnosti o metodách, které je <xref:Microsoft.VisualStudio.Package.Declarations> nutné implementovat, najdete v třídě .

 Pokud seznam obsahuje pouze jedno slovo, třída toto slovo automaticky vloží <xref:Microsoft.VisualStudio.Package.Source> místo částečného slova. Pokud seznam obsahuje více než jedno slovo, třída zobrazí seznam popisů nástrojů, ze kterého může uživatel <xref:Microsoft.VisualStudio.Package.Source> vybrat vhodnou volbu.

 Podívejte se také na příklad implementace <xref:Microsoft.VisualStudio.Package.Declarations> třídy v dokončování [členů ve službě starší verze jazyka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
