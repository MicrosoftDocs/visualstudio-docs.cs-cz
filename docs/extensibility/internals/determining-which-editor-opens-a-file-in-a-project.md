---
title: Určení editoru, který otevře soubor v projektu | Microsoft Docs
description: Přečtěte si o klíčích registru a metodách sady Visual Studio SDK používaných sadou Visual Studio k určení, který Editor otevře soubor v projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48d642c8a3b7883507c06453c0025badc299ce75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963416"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Určete, který Editor otevře soubor v projektu.
Když uživatel otevře soubor v projektu, prostředí projde procesem cyklického dotazování a nakonec otevře příslušný editor nebo návrháře pro tento soubor. Počáteční postup používaný prostředím je stejný pro standardní i vlastní editory. Prostředí používá různá kritéria při cyklickém dotazování, který Editor použít k otevření souboru a VSPackage musí během tohoto procesu koordinovat prostředí.

 Například když uživatel vybere příkaz **otevřít** v nabídce **soubor** a pak zvolí *filename. RTF* (nebo jakýkoli jiný soubor s příponou *. RTF* ), prostředí zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementaci pro každý projekt a nakonec projde všechny instance projektu v řešení. Projekty vrací sadu příznaků, které identifikují deklarace identity v dokumentu podle priority. Při použití nejvyšší priority prostředí volá příslušnou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodu. Další informace o procesu cyklického dotazování naleznete v tématu [Přidání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Projekt různých souborů deklarace identity všechny soubory, které nejsou vyžádány jinými projekty. Tímto způsobem mohou vlastní editory otevřít dokumenty před tím, než je otevřou standardní editory. Pokud projekt různé soubory deklaruje soubor, prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodu pro otevření souboru pomocí standardního editoru. Prostředí zkontroluje svůj interní seznam registrovaných editorů pro jeden, který zpracovává soubory *. RTF* . Tento seznam najdete v registru v následujícím klíči:

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ \<version> \Editors \\ \<editor factory guid> \Extensions**

 Prostředí také kontroluje identifikátory třídy v **HKEY_CLASSES_ROOT\CLSID** klíč pro všechny objekty, které mají podklíč **DocObject**. Pokud je nalezena přípona souboru, vložená verze aplikace, jako je například Microsoft Word, je vytvořena místně v aplikaci Visual Studio. Tyto objekty dokumentu musí být složené soubory, které implementují <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> rozhraní, nebo objekt musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> rozhraní.

 Pokud v registru není k dispozici žádný *objekt pro vytváření* editorů, pak prostředí vyhledá klíč **HKEY_CLASSES_ROOT \\ . RTF** a otevře Editor, který zde zadal. Pokud se přípona souboru nenajde v **HKEY_CLASSES_ROOT**, pak prostředí používá základní textový editor sady Visual Studio k otevření souboru, pokud se jedná o textový soubor.

 Pokud se základní textový editor nezdařil, k němuž dojde v případě, že soubor není textový soubor, pak prostředí používá svůj binární editor souboru.

 Pokud prostředí nalezne editor pro rozšíření *. RTF* ve svém registru, načte VSPackage, který implementuje tento objekt pro vytváření editoru. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodu na novém VSPackage. Volání VSPackage `QueryService` pro `SID_SVsRegistorEditor` , pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metody k registraci objektu pro vytváření editoru s prostředím.

 Prostředí teď znovu zkontroluje svůj interní seznam registrovaných editorů a najde nově registrovaný objekt pro vytváření editoru pro soubory *. RTF* . Prostředí volá implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, předáním názvu souboru a typu zobrazení, který chcete vytvořit.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
