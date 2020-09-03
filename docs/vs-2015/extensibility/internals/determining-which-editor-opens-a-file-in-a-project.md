---
title: Určení editoru, který otevře soubor v projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c79860f770a6b04a17786cfb281fc3c0e4dffda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196759"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Určení editoru, který otevře soubor v projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Když uživatel otevře soubor v projektu, prostředí projde procesem cyklického dotazování a nakonec otevře příslušný editor nebo návrháře pro tento soubor. Počáteční postup používaný prostředím je stejný pro standardní i vlastní editory. Prostředí používá různá kritéria při cyklickém dotazování, který Editor použít k otevření souboru a VSPackage musí během tohoto procesu koordinovat prostředí.  
  
 Například když uživatel vybere příkaz **otevřít** v nabídce **soubor** a pak zvolí `filename` . RTF (nebo jakýkoli jiný soubor s příponou. RTF), prostředí zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementaci pro každý projekt a nakonec projde všechny instance projektu v řešení. Projekty vrací sadu příznaků, které identifikují deklarace identity v dokumentu podle priority. Při použití nejvyšší priority prostředí volá příslušnou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodu. Pro další informace o procesu cyklického dotazování [přidejte šablony projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Projekt různých souborů deklarace identity všechny soubory, které nejsou vyžádány jinými projekty. Tímto způsobem mohou vlastní editory otevřít dokumenty před tím, než je otevřou standardní editory. Pokud projekt různé soubory deklaruje soubor, prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodu pro otevření souboru pomocí standardního editoru. Prostředí zkontroluje svůj interní seznam registrovaných editorů pro jeden, který zpracovává soubory. RTF. Tento seznam najdete v registru v následujícím klíči:  
  
 [HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ < `version`> \Editors \\ {<`editor factory guid`>} \Extensions]  
  
 Prostředí také kontroluje identifikátory třídy v klíči HKEY_CLASSES_ROOT \CLSID pro všechny objekty, které mají DocObject podklíče. Pokud je nalezena přípona souboru, vložená verze aplikace, jako je například Microsoft Word, je vytvořena místně v aplikaci Visual Studio. Tyto objekty dokumentu musí být složené soubory, které implementují <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> rozhraní, nebo objekt musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> rozhraní.  
  
 Pokud v registru není k dispozici žádný objekt pro vytváření editorů, pak prostředí vyhledá \\ klíč HKEY_CLASSES_ROOT. RTF a otevře Editor, který zde zadal. Pokud se přípona souboru nenajde v HKEY_CLASSES_ROOT, pak prostředí používá základní textový editor sady Visual Studio k otevření souboru, pokud se jedná o textový soubor.  
  
 Pokud se základní textový editor nezdařil, k němuž dojde v případě, že soubor není textový soubor, pak prostředí používá svůj binární editor souboru.  
  
 Pokud prostředí nalezne editor pro rozšíření. RTF ve svém registru, načte VSPackage, který implementuje tento objekt pro vytváření editoru. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodu na novém VSPackage. Volání VSPackage `QueryService` pro `SID_SVsRegistorEditor` , pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metody k registraci objektu pro vytváření editoru s prostředím.  
  
 Prostředí teď znovu zkontroluje svůj interní seznam registrovaných editorů a najde nově registrovaný objekt pro vytváření editoru pro soubory. RTF. Prostředí volá implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, předáním názvu souboru a typu zobrazení, který chcete vytvořit.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
