---
title: Určení, které Editor otevře soubor v projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 655a5a28e3e16a1b07c52c37ef00d89d145a17a1
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498539"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Určení, které editor otevře soubor v projektu
Když uživatel otevře soubor v projektu, prostředí prochází proces dotazování, nakonec otevřete příslušné editoru nebo návrháře pro tento soubor. Počáteční postup náhradník prostředí je stejný pro standardních a vlastních editorů. Prostředí používá celou řadu kritéria při dotazování které editor k použití pro otevření souboru a sady VSPackage se muset domluvit se prostředí během tohoto procesu.  
  
 Když uživatel například vybere **otevřít** příkaz **souboru** nabídky a následně klikne *filename.rtf* (nebo jakýkoli jiný soubor s *.rtf*rozšíření), volání prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementace pro každý projekt, nakonec procházením všechny instance projektu v řešení. Projekty vrátit sadu příznaků, které identifikují deklarací identity v dokumentu podle priority. Pomocí nejvyšší prioritou, prostředí volá odpovídající <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody. Další informace o procesu dotazování, naleznete v tématu [přidat projekt a šablony položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Projekt ostatní soubory deklarací všechny soubory, které nejsou převzatá podle jiných projektů. Tímto způsobem vlastních editorech můžete otevřít dokumenty, než standardní editory je otevřít. Pokud projekt ostatní soubory deklarací souboru, prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody k otevření souboru s standardní editor. Prostředí ověří jeho vnitřní seznam registrovaných editory pro jednu, která zpracovává *.rtf* soubory. Tento seznam se nachází v registru v klíči následující:  
  
 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<verze > \Editors\\\<guid objekt pro vytváření editoru > \Extensions**
  
 Prostředí také zkontroluje identifikátory tříd **HKEY_CLASSES_ROOT\CLSID** klíčů pro všechny objekty, které mají podklíč **DocObject**. Pokud přípona souboru je zde nalezen, embedded verzi aplikace, jako je například Microsoft Word, se vytvoří v místě v sadě Visual Studio. Tyto objekty dokumentu musí být složené soubory, které implementují <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> musí implementovat rozhraní, nebo objekt <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> rozhraní.  
  
 Pokud není žádný objekt factory editoru pro *.rtf* soubory v registru, pak prostředí vypadá **HKEY_CLASSES_ROOT\\.rtf** klíče a otevře se editor, existuje zadaná. Pokud přípona souboru nebyla nalezena v **HKEY_CLASSES_ROOT**, pak prostředí pomocí textového editoru sady Visual Studio core otevřete soubor, pokud se jedná textový soubor.  
  
 Pokud se nezdaří základní text editor, které dojde, že pokud soubor není textový soubor, pak prostředí používá jeho binární editor pro tento soubor.  
  
 Pokud prostředí najít editor pro *.rtf* rozšíření v jeho registru, načte sady VSPackage, která implementuje tento objekt pro vytváření editoru. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metoda u nového balíčku VSPackage. Volání VSPackage `QueryService` pro `SID_SVsRegistorEditor`, použije <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metody pro registraci objekt factory editoru s prostředím.  
  
 Prostředí proběhne znovu teď u jeho vnitřní seznam registrovaných editorů najít objekt factory editoru nově zaregistrovaný pro *.rtf* soubory. Prostředí volá vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodu v souboru název a zobrazit typ vytvoření.  
  
## <a name="see-also"></a>Viz také:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>