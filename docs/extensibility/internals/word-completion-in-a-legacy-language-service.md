---
title: Dokončování slov ve službě starší verze jazyka | Microsoft Docs
description: V sadě Visual Studio SDK může být podpora dokončování slov podporována pro službu starší verze jazyka. Přečtěte si, jak jsou ve VSPackage implementovány starší jazykové služby.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 489b43c825e3512e1bd33bc732833de84aed54c3
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616272"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Dokončování slov ve službě starší verze jazyka
Doplňování slov chybějících znaků u částečně zadaného slova. Pokud je k dispozici jenom jedno možné dokončení, slovo se po zadání znaku dokončení dokončí. Pokud se v částečném slově shoduje více než jedna možnost, zobrazí se seznam možných dokončení. Znak dokončení může být libovolný znak, který se nepoužívá pro identifikátory.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace najdete v tématu [rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="implementation-steps"></a>Postup implementace

1. Když uživatel vybere z nabídky **technologie IntelliSense** **kompletní slovo** , <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> příkaz se odešle do služby jazyka.

2. <xref:Microsoft.VisualStudio.Package.ViewFilter>Třída zachytí příkaz a volá <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodu s důvodem analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> .

3. <xref:Microsoft.VisualStudio.Package.Source>Třída pak zavolá <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu, aby získala seznam možných dokončování slov a potom zobrazí slova v seznamu popisů použití <xref:Microsoft.VisualStudio.Package.CompletionSet> třídy.

    Pokud je k dispozici pouze jedno vyhovující slovo, <xref:Microsoft.VisualStudio.Package.Source> Třída dokončí slovo.

   Případně, pokud skener vrátí hodnotu triggeru <xref:Microsoft.VisualStudio.Package.TokenTriggers> při zadání prvního znaku identifikátoru, <xref:Microsoft.VisualStudio.Package.Source> Třída ji detekuje a zavolá <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodu s důvodem analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> . V takovém případě analyzátor musí detekovat přítomnost znaku výběru členů a poskytnout seznam členů.

## <a name="enabling-support-for-the-complete-word"></a>Povolení podpory pro celé slovo
 Chcete-li povolit podporu pro dokončení aplikace Word, `CodeSense` pojmenovaný parametr předaný do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributu uživatele přidruženého k jazykovému balíčku. Tím se nastaví <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy.

 Váš analyzátor musí vrátit seznam deklarací v reakci na hodnotu důvod analýzy <xref:Microsoft.VisualStudio.Package.ParseReason> , aby se dokončilo fungování Wordu.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementace kompletního slova v metodě ParseSource
 V případě dokončování slov <xref:Microsoft.VisualStudio.Package.Source> třída volá <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodu <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy, aby získala seznam možných shod slov. Je nutné implementovat seznam ve třídě, která je odvozena od <xref:Microsoft.VisualStudio.Package.Declarations> třídy. <xref:Microsoft.VisualStudio.Package.Declarations>Podrobnosti o metodách, které je nutné implementovat, naleznete v třídě.

 Pokud seznam obsahuje pouze jedno slovo, <xref:Microsoft.VisualStudio.Package.Source> třída automaticky vloží toto slovo místo částečného slova. Pokud seznam obsahuje více než jedno slovo, <xref:Microsoft.VisualStudio.Package.Source> Třída prezentuje seznam tipů, ze kterého může uživatel vybrat vhodnou volbu.

 Podívejte se také na příklad <xref:Microsoft.VisualStudio.Package.Declarations> implementace třídy při [dokončování členů ve službě starší verze jazyka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
