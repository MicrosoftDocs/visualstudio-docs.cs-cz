---
title: Starší verze rozhraní v editoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45c3de943a1716877fcf33af4d16fd163721d04b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737507"
---
# <a name="legacy-interfaces-in-the-editor"></a>Starší verze rozhraní v editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor sady Visual Studio můžete přistupovat ze starší verze rozhraní. Visual Studio SDK zahrnuje adaptérů, označované jako *překrytí*, která umožňují tato rozhraní pro interakci s nového editoru. Doporučujeme však, že aktualizujete starší kód Refaktorovat pro použití nového editoru rozhraní API. Váš kód budou líp fungovat a využívat nové technologie, jako je Windows Presentation Foundation (WPF) a Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Přizpůsobení zastaralého kódu editoru](../extensibility/adapting-legacy-code-to-the-editor.md)|Vysvětluje, jak přizpůsobit kód do nového editoru.|  
|[Nové nebo změněné chování adaptérů editoru](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Vysvětluje, jak se liší od starších verzí editoru chování editoru adaptéry.|  
|[Práce v základní editoru](../extensibility/inside-the-core-editor.md)|Popisuje různé součásti dřívějších verzích editoru.|  
|[Vytvoření instance základního editoru pomocí zastaralého rozhraní API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Vysvětluje způsob používání starší verze rozhraní API k vytvoření instance základní editor.|  
|[Objekty pro vytváření editoru](../extensibility/editor-factories.md)|Vysvětluje, jak používat objekty pro vytváření editoru pomocí starší verze rozhraní API.|  
|[Postupy: Registrace typů souborů editoru](../extensibility/how-to-register-editor-file-types.md)|Vysvětluje, jak propojit příponu názvu souboru do editoru.|  
|[Návod: Vytvoření základního editoru a registrace typu souboru editoru](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Vysvětluje, jak vytvořit základní editor a odkaz na něj příponu názvu souboru.|  
|[Postupy: Poskytnutí kontextu pro editory](../extensibility/how-to-provide-context-for-editors.md)|Vysvětluje, jak poskytnout kontext pro editor.|  
|[Jazykové služby a základní editor](../extensibility/language-services-and-the-core-editor.md)|Vysvětluje interakce mezi služba jazyka a editoru.|  
|[Přístup k vyrovnávací paměti textu pomocí zastaralého rozhraní API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Vysvětluje, jak získat přístup k vyrovnávací paměti textu pomocí starší verze rozhraní API.|  
|[Přístup k textovému zobrazení pomocí zastaralého rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Vysvětluje, jak získat přístup k zobrazení textu pomocí starší verze rozhraní API.|  
|[Přizpůsobení oken s kódem pomocí zastaralého rozhraní API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Vysvětluje, jak přizpůsobit kód windows pomocí starší verze rozhraní API.|  
|[Přístup k textovým vrstvám pomocí zastaralého rozhraní API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Vysvětluje, jak získat přístup k jiné vrstvy textu pomocí starší verze rozhraní API.|  
|[Použití textových značek pomocí zastaralého rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)|Vysvětluje, jak přidat text značky pomocí starší verze rozhraní API.|  
|[Přizpůsobení ovládacích prvků a nabídek editoru pomocí zastaralého rozhraní API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Vysvětluje, jak přizpůsobit ovládací prvky editoru pomocí starší verze rozhraní API.|  
|[Správa příkazů Zpět a Znovu pomocí zastaralého rozhraní API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Vysvětluje, jak spravovat vrácení zpět a znovu pomocí starší verze rozhraní API.|  
|[Postupy: Implementace mechanismu Najít a nahradit](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Vysvětluje, jak spravovat najít a nahradit pomocí starší verze rozhraní API.|  
|[Postupy: Potlačení oznámení o změně souboru](../extensibility/how-to-suppress-file-change-notifications.md)|Vysvětluje, jak můžete potlačit oznámení o změně souborů pomocí starší verze rozhraní API.|  
|[Vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md)|Vysvětluje vytváření vlastních editorů a návrhářů.|  
|[Vývoj služby starší verze jazyka](../extensibility/internals/developing-a-legacy-language-service.md)|Obsahuje odkazy na dokumenty o funkcích, které umožňují přizpůsobení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základním editoru tak, že přidáte podporu pro jazykové služby.|  
|[Použití písem a barev](../extensibility/using-fonts-and-colors.md)|Vysvětluje, jak pomocí starší verze rozhraní písma a barvy.|

