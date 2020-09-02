---
title: Jazykové služby a základní editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180294"
---
# <a name="language-services-and-the-core-editor"></a>Jazykové služby a základní editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editory v aplikaci Visual Studio jsou často přidruženy ke službě jazyka. Služba jazyka mimo jiné poskytuje barevné zvýrazňování syntaxe, dokončování příkazů, IntelliSense a formátování textu.  
  
## <a name="core-editors-and-document-data-objects"></a>Základní editory a objekty dat dokumentu  
 Když přistupujete k základnímu editoru, nevytvářejte data dokumentů a objekty zobrazení dokumentu. Rozhraní IDE vytvoří a řídí tyto dva objekty a získáte k nim popisovače pomocí příslušných volání v implementaci vaší továrny editoru.  
  
 Další informace naleznete v tématu [určení, který Editor otevře soubor v projektu](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Jazykové služby a základní editor  
 Implementací jazykové služby můžete řídit, jak se data zobrazují v zobrazení dokumentu. Služba jazyka poskytuje informace a chování, které jsou specifické pro daný jazyk, například Visual C++. Když vytvoříte textovou vyrovnávací paměť a určíte příponu filename pro otevíraný dokument, vyrovnávací paměť textu určuje jazykovou službu přidruženou k této příponě názvu souboru z klíče registru HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Editors \\ {YOURLANGUAGESERVICE GUID} \Extensions. Standardní postup načítání VSPackage potom načte VSPackage a vytvoří instanci vaší jazykové služby.  
  
 Na následujícím obrázku je uvedena základní služba jazyka.  
  
 ![Obrázek modelu jazykové služby](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Základní editor a objekty jazykové služby  
  
 Datový objekt dokumentu pro základní editor se nazývá textová vyrovnávací paměť a je reprezentovaný <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objektem. Objekt zobrazení dokumentu se nazývá textové zobrazení a je reprezentován <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objektem. Tyto dva objekty vzájemně spolupracují prostřednictvím jazykové služby a poskytují jednotný přehled základního editoru. Informace z textové vyrovnávací paměti a zobrazení text se zobrazí v okně dokumentu s názvem okno kódu. Dokument okna Code je spravován správcem oken kódu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Poskytování kontextu jazykové služby pomocí starší verze rozhraní API](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hostování IntelliSense](../extensibility/intellisense-hosting.md)   
 [Obsažené jazyky](../extensibility/contained-languages.md)   
 [Vývoj služby starší verze jazyka](../extensibility/internals/developing-a-legacy-language-service.md)
