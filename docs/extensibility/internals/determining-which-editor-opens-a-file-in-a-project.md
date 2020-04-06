---
title: Určení, který editor otevře soubor v projektu | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708658"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Určení editoru, který otevře soubor v projektu
Když uživatel otevře soubor v projektu, prostředí prochází procesem dotazování a nakonec otevře příslušný editor nebo návrhář pro tento soubor. Počáteční postup používaný prostředím je stejný pro standardní i vlastní editory. Prostředí používá řadu kritérií při dotazování, který editor použít k otevření souboru a VSPackage musí koordinovat s prostředím během tohoto procesu.

 Například když uživatel vybere příkaz **Otevřít** z nabídky **Soubor** a pak zvolí *filename.rtf* (nebo jakýkoli jiný soubor s <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> příponou *RTF),* prostředí volá implementaci pro každý projekt, případně cykluje přes všechny instance projektu v řešení. Projekty vrátí sadu příznaků, které identifikují deklarace identity v dokumentu podle priority. Použití nejvyšší prioritu prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> příslušnou metodu. Další informace o procesu dotazování naleznete v tématu [Přidání šablon položek projektu a projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Projekt Různé soubory nárokuje všechny soubory, které nejsou nárokovány jinými projekty. Tímto způsobem mohou vlastní editory otevřít dokumenty před jejich otevřením standardními editory. Pokud projekt Různé soubory nárokuje soubor, prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodu k otevření souboru pomocí standardního editoru. Prostředí zkontroluje svůj interní seznam registrovaných editorů pro ten, který zpracovává *soubory RTF.* Tento seznam je umístěn v registru na následující klíč:

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<verze>\Editors\\\<editor factory guid>\Extensions**

 Prostředí také kontroluje identifikátory tříd v klíči **HKEY_CLASSES_ROOT\CLSID** pro všechny objekty, které mají podklíč **DocObject**. Pokud je zde nalezena přípona souboru, je v aplikaci Visual Studio vytvořena vložená verze aplikace, například Aplikace Microsoft Word. Tyto objekty dokumentu musí být <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> složené soubory, které <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementují rozhraní nebo objekt musí implementovat rozhraní.

 Pokud v registru neexistuje žádná továrna editoru pro soubory *RTF,* prostředí vyhledá **klíč HKEY_CLASSES_ROOT\\.rtf** a otevře zde zadaný editor. Pokud přípona souboru není nalezena v **HKEY_CLASSES_ROOT**, pak prostředí používá základní textový editor sady Visual Studio k otevření souboru, pokud se jedná o textový soubor.

 Pokud základní textový editor selže, ke kterému dochází, pokud soubor není textový soubor, pak prostředí používá jeho binární editor pro soubor.

 Pokud prostředí najít editor pro rozšíření *.rtf* ve svém registru, načte VSPackage, který implementuje tento editor factory. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodu na nový VSPackage. VSPackage volání `QueryService` `SID_SVsRegistorEditor`pro , <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> pomocí metody zaregistrovat editor factory s prostředím.

 Prostředí nyní znovu zkontroluje svůj interní seznam registrovaných editorů, aby nalezlo nově registrovanou továrnu editorů pro soubory *RTF.* Prostředí volá implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody, předávání v názvu souboru a typ zobrazení vytvořit.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
