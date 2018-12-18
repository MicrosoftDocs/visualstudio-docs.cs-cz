---
title: Word dokončení ve službě starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55fbe636c77d77b3b4f61f9f56a4fa91fe49a090
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879074"
---
# <a name="word-completion-in-a-legacy-language-service"></a>Dokončování slov ve službě starší verze jazyka
Dokončování slov vyplní chybějící znaky na částečně napsaného slova. Pokud existuje jenom jeden možných dokončení, slovo dokončení po zadání znaku dokončení. Pokud částečné slovo odpovídá více než jednu možnost, zobrazí se seznam možných dokončení. Dokončení znak může být libovolný znak, který se nepoužívá pro identifikátory.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace najdete v tématu [rozšíření pro Editor a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
## <a name="implementation-steps"></a>Postup implementace  
  
1. Když uživatel vybere **dokončit slovo** z **IntelliSense** nabídce <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> příkazu se odesílají službě jazyka.  
  
2. <xref:Microsoft.VisualStudio.Package.ViewFilter> Zachytí třídy příkazu a volání <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodu parse důvod <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3. <xref:Microsoft.VisualStudio.Package.Source> Třídy volání a pak <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodu k získání seznamu dokončování slov je to možné a pak zobrazí seznam slov v popisu tlačítka pomocí <xref:Microsoft.VisualStudio.Package.CompletionSet> třídy.  
  
    Pokud existuje pouze jeden odpovídající aplikace <xref:Microsoft.VisualStudio.Package.Source> třídy dokončí slovo.  
  
   Případně Pokud skener vrací hodnotu aktivační událost <xref:Microsoft.VisualStudio.Package.TokenTriggers> při první znak identifikátoru se <xref:Microsoft.VisualStudio.Package.Source> třídy to zjistí a volá <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodu parse důvod <xref:Microsoft.VisualStudio.Package.ParseReason>. V tomto případě musíte analyzátor zjištění přítomnosti tohoto znaku výběru člena a poskytnout seznam členů.  
  
## <a name="enabling-support-for-the-complete-word"></a>Povolení podpory pro dokončit slovo  
 Povolení podpory pro sadu dokončování slov `CodeSense` s názvem parametr předaný <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atribut uživatele přidružené k balíčku jazyka. Tím se nastaví <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy.  
  
 Analyzátor jazyka musí vrátit seznam deklarací v reakci na hodnotu parse důvod <xref:Microsoft.VisualStudio.Package.ParseReason>, pro dokončování slov fungovat.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>Implementace dokončit slovo v ParseSource – metoda  
 Pro dokončení slova <xref:Microsoft.VisualStudio.Package.Source> třídy volání <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodu na <xref:Microsoft.VisualStudio.Package.AuthoringScope> třídy získat seznam možných slovo shody. V seznamu musí implementovat do třídy, která je odvozena od <xref:Microsoft.VisualStudio.Package.Declarations> třídy. Zobrazit <xref:Microsoft.VisualStudio.Package.Declarations> třídy podrobnosti pro metody, je nutné implementovat.  
  
 Pokud seznam obsahuje pouze jediné slovo, pak bude <xref:Microsoft.VisualStudio.Package.Source> třídy automaticky vloží toto slovo místo částečného slova. Pokud seznam obsahuje více než jedno slovo a <xref:Microsoft.VisualStudio.Package.Source> třída představuje seznam nástroj tip, ze kterého může uživatel vybrat vhodnou volbou.  
  
 V příkladu se také podívat <xref:Microsoft.VisualStudio.Package.Declarations> implementace třídy v [dokončování členů ve službě starší verze jazyka](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).