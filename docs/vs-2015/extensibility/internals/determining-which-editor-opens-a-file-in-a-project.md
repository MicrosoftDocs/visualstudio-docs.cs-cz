---
title: Určení, které Editor otevře soubor v projektu | Dokumentace Microsoftu
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
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 832fd838246c075087700494b09757184be687a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741607"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Určení editoru, který otevře soubor v projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Když uživatel otevře soubor v projektu, prostředí prochází proces dotazování, nakonec otevřete příslušné editoru nebo návrháře pro tento soubor. Počáteční postup náhradník prostředí je stejný pro standardních a vlastních editorů. Prostředí používá celou řadu kritéria při dotazování které editor k použití pro otevření souboru a sady VSPackage se muset domluvit se prostředí během tohoto procesu.  
  
 Když uživatel například vybere **otevřít** příkaz **souboru** nabídky a následně klikne `filename`RTF (nebo jakýkoli jiný soubor s příponou .rtf) volání prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementace pro každý projekt, nakonec procházením všechny instance projektu v řešení. Projekty vrátit sadu příznaků, které identifikují deklarací identity v dokumentu podle priority. Pomocí nejvyšší prioritou, prostředí volá odpovídající <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody. Další informace o procesu dotazování [přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Projekt ostatní soubory deklarací všechny soubory, které nejsou převzatá podle jiných projektů. Tímto způsobem vlastních editorech můžete otevřít dokumenty, než standardní editory je otevřít. Pokud projekt ostatní soubory deklarací souboru, prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody k otevření souboru s standardní editor. Prostředí ověří jeho vnitřní seznam registrovaných editory pro takový, který zpracovává soubory RTF. Tento seznam se nachází v registru v klíči následující:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 Prostředí také zkontroluje identifikátory třída v klíči HKEY_CLASSES_ROOT\CLSID pro všechny objekty, které mají dílčí klíče DocObject. Pokud přípona souboru je zde nalezen, embedded verzi aplikace, jako je například Microsoft Word, se vytvoří v místě v sadě Visual Studio. Tyto objekty dokumentu musí být složené soubory, které implementují <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> musí implementovat rozhraní, nebo objekt <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> rozhraní.  
  
 Pokud neexistuje žádný objekt factory editoru pro soubory .rtf v registru, pak prostředí vypadá v HKEY_CLASSES_ROOT \\klíč ve formátu RTF a otevře se editor existuje zadaná. Pokud přípona souboru nebyla nalezena v registru HKEY_CLASSES_ROOT, prostředí používá editoru sady Visual Studio core text k otevření souboru, pokud se jedná textový soubor.  
  
 Pokud se nezdaří základní text editor, které dojde, že pokud soubor není textový soubor, pak prostředí používá jeho binární editor pro tento soubor.  
  
 Pokud prostředí v jeho registru najít editor pro rozšíření RTF, načte sady VSPackage, která implementuje tento objekt pro vytváření editoru. Prostředí volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metoda u nového balíčku VSPackage. Volání VSPackage `QueryService` pro `SID_SVsRegistorEditor`, použije <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metody pro registraci objekt factory editoru s prostředím.  
  
 Prostředí teď znovu ověří jeho vnitřní seznam registrovaných editorů najít objekt factory editoru nově zaregistrovaný pro soubory ve formátu RTF. Prostředí volá vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodu v souboru název a zobrazit typ vytvoření.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

