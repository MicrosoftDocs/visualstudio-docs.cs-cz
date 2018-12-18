---
title: Jazykové služby a základní Editor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7f439cf1564e14857b3a609191cc0bea05e0e04
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636236"
---
# <a name="language-services-and-the-core-editor"></a>Jazykové služby a základní editor
Editory v sadě Visual Studio jsou často spojeny s služba jazyka. Mimo jiné poskytuje služba jazyka barevné zvýrazňování syntaxe, dokončování příkazů, technologie IntelliSense a formátování textu.  
  
## <a name="core-editors-and-document-data-objects"></a>Základní editory a datové objekty dokumentu  
 Při přístupu k základní editor nevytvoříte data dokumentu a objekty zobrazení dokumentu. Rozhraní IDE vytvoří a ovládací prvky tyto dva objekty, a získat obslužné rutiny na ně tím, že odpovídající volání v editoru implementace objektu factory.  
  
 Další informace najdete v tématu [určit, které editor otevře soubor v projektu](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Jazykové služby a základní editor  
 Implementací služba jazyka můžete řídit, jak se data zobrazí v zobrazení dokumentu. Služba jazyka poskytuje informace a chování, které jsou specifické pro daný jazyk, jako je například Visual C++. Při vytváření textové vyrovnávací paměti a určit název souboru rozšíření pro dokument, které otevíráte, textové vyrovnávací paměti určuje spojené s touto příponou názvu souboru z klíče registru, služba jazyka **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\Editors\\{YourLanguageService GUID} \Extensions**. Standardní VSPackage načítání postupu pak načte váš balíček VSPackage správy kódu a je vytvořena instance vaší služby jazyka.  
  
 Služba základní jazyk je zobrazena na následujícím obrázku.  
  
 ![Obrázek modelu služby jazyka](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Základní jazyk a editor objektů služby  
  
 Datový objekt dokumentu pro základní editor se nazývá textové vyrovnávací paměti a je reprezentována <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objektu. Objekt zobrazení dokumentu se nazývá zobrazení textu a je reprezentována <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objektu. Společně tyto dva objekty ve službě jazyka poskytnout jednotný pohled na základní editor. Informace z vyrovnávací paměti textu a zobrazení textu v okně dokumentu volat okně kódu. Okno dokumentu kódu se spravuje přes správce okno kódu.  
  
## <a name="see-also"></a>Viz také:  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Poskytuje kontext služby jazyka pomocí starší verze rozhraní API](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hostování technologie IntelliSense](../extensibility/intellisense-hosting.md)   
 [Omezením jazyky](../extensibility/contained-languages.md)   
 [Vývoj služby starší verze jazyka](../extensibility/internals/developing-a-legacy-language-service.md)