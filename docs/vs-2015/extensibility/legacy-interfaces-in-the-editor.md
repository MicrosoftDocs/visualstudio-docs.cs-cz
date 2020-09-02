---
title: Starší rozhraní v editoru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8483068ae03c9a57fc67b528393e5d6830c3ec33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180281"
---
# <a name="legacy-interfaces-in-the-editor"></a>Zastaralá rozhraní v editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K editoru sady Visual Studio můžete přistupovat z starších rozhraní. Sada Visual Studio SDK obsahuje adaptéry označované jako *překrytí*, které umožňují těmto rozhraním pracovat s novým editorem. Nicméně doporučujeme, abyste aktualizovali starší kód, aby používal nové rozhraní API editoru. Váš kód bude lepší a můžete použít nové technologie, jako je Windows Presentation Foundation (WPF) a Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Přizpůsobení zastaralého kódu editoru](../extensibility/adapting-legacy-code-to-the-editor.md)|Vysvětluje, jak přizpůsobovat kód k novému editoru.|  
|[Nové nebo změněné chování adaptérů editoru](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Vysvětluje, jak se chování adaptérů editoru liší od předchozí verze editoru.|  
|[Práce v základní editoru](../extensibility/inside-the-core-editor.md)|Popisuje různé komponenty starších verzí editoru.|  
|[Vytvoření instance základního editoru pomocí zastaralého rozhraní API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Vysvětluje, jak používat starší rozhraní API k vytvoření instance základního editoru.|  
|[Objekty pro vytváření editoru](../extensibility/editor-factories.md)|Vysvětluje, jak používat objekty pro vytváření editorů se starší verzí rozhraní API.|  
|[Postupy: Registrace typů souborů editoru](../extensibility/how-to-register-editor-file-types.md)|Vysvětluje, jak propojit příponu názvu souboru s vaším editorem.|  
|[Návod: Vytvoření základního editoru a registrace typu souboru editoru](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Vysvětluje, jak vytvořit základní editor a propojit s ním příponu názvu souboru.|  
|[Postupy: Poskytnutí kontextu pro editory](../extensibility/how-to-provide-context-for-editors.md)|Vysvětluje, jak poskytnout kontext pro Editor.|  
|[Jazykové služby a základní editor](../extensibility/language-services-and-the-core-editor.md)|Vysvětluje interakce mezi službou jazyka a editorem.|  
|[Přístup k vyrovnávací paměti textu pomocí zastaralého rozhraní API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Vysvětluje, jak přistupovat k textové vyrovnávací paměti pomocí starší verze rozhraní API.|  
|[Přístup k textovému zobrazení pomocí zastaralého rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Vysvětluje, jak přistupovat k zobrazení textu pomocí starší verze rozhraní API.|  
|[Přizpůsobení oken s kódem pomocí zastaralého rozhraní API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Vysvětluje, jak přizpůsobit okna kódu pomocí starší verze rozhraní API.|  
|[Přístup k textovým vrstvám pomocí zastaralého rozhraní API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Vysvětluje, jak přistupovat k různým vrstvám textu pomocí starší verze rozhraní API.|  
|[Použití textových značek pomocí zastaralého rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)|Vysvětluje, jak přidat textové značky pomocí starší verze rozhraní API.|  
|[Přizpůsobení ovládacích prvků a nabídek editoru pomocí zastaralého rozhraní API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Vysvětluje, jak přizpůsobit ovládací prvky editoru pomocí starší verze rozhraní API.|  
|[Správa příkazů Zpět a Znovu pomocí zastaralého rozhraní API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Vysvětluje, jak spravovat akce zpět a znovu pomocí starší verze rozhraní API.|  
|[Postupy: Implementace mechanismu Najít a nahradit](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Vysvětluje, jak spravovat hledání a nahrazování pomocí starší verze rozhraní API.|  
|[Postupy: Potlačení oznámení o změně souboru](../extensibility/how-to-suppress-file-change-notifications.md)|Vysvětluje, jak potlačit oznámení o změnách souborů pomocí starší verze rozhraní API.|  
|[Vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md)|Vysvětluje, jak vytvořit vlastní editory a návrháře.|  
|[Vývoj služby starší verze jazyka](../extensibility/internals/developing-a-legacy-language-service.md)|Obsahuje odkazy na dokumenty o funkcích, které poskytují možnosti přizpůsobení pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základní editor přidáním podpory pro jazykovou službu.|  
|[Použití písem a barev](../extensibility/using-fonts-and-colors.md)|Vysvětluje, jak používat písma a barvy u starších rozhraní.|
