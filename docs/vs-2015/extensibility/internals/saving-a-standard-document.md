---
title: Uložení standardního dokumentu | Dokumentace Microsoftu
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
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72415a4ddfa3de9511aab4b52ae37960af872fde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803575"
---
# <a name="saving-a-standard-document"></a>Uložení standardního dokumentu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prostředí zpracovává uložit, uložit jako a uložte všechny příkazy. Když uživatel vybere **Uložit**, **uložit jako**, nebo **Uložit vše** z **souboru** nabídky nebo zavření řešení, což vede k  **Uložit vše**, spustí následující proces.  
  
 ![Standardní Editor](../../extensibility/internals/media/public.gif "veřejné")  
Uložit, uložit jako a Uložit vše zpracování příkazů pro standardní editor  
  
 Tento proces je podrobně popsán v následujících krocích:  
  
1. Když **Uložit** a **uložit jako** příkazy jsou vybrané, používá prostředí <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> služby k určení aktivního okna dokumentu, a proto položky by měly být uloženy. Jakmile okno aktivního dokumentu je známé, vyhledá prostředí hierarchie ukazatele a identifikátor položky (itemID) dokumentu v tabulce spuštěných dokumentů. Další informace najdete v tématu [spuštěná tabulka dokumentů](../../extensibility/internals/running-document-table.md).  
  
    Když **Uložit vše** příkaz, prostředí používá informace v tabulce spuštěných dokumentů pro kompilaci seznam všech položek na Uložit.  
  
2. Když řešení obdrží <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> volání, prochází sadu vybraných položek (to znamená více výběrů, které jsou vystavené <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> služby).  
  
3. Pro každou položku do výběru, toto řešení využívá ukazatel hierarchie volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodou ke zjištění, zda **Uložit** příkazu nabídky by měla být povolená. Pokud jeden nebo více položek jsou chybná, pak bude **Uložit** je příkaz povolen. Pokud v hierarchii používá standardní editor, pak dotazování na hierarchii delegáty nesprávné stav do editoru voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.  
  
4. Pro každou vybranou položku není čistá, toto řešení využívá ukazatel hierarchie volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metodu na odpovídající hierarchie.  
  
    Je běžné, hierarchie a použít standardní editor k úpravě dokumentu. V takovém případě data dokumentu objekt pro tento editor by měl podporovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> rozhraní. Po přijetí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> volání metody projektu by měla být podkladem editoru, který je dokument uložen voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metodu na datový objekt dokumentu. V editoru můžete povolit prostředí pro zpracování **uložit jako** dialogové okno, voláním `Query Service` pro <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> rozhraní. Vrátí ukazatel <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní. Editor musíte pak zavolat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> metoda předání ukazatele na editor <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementace prostřednictvím `pPersistFile` parametru. Pak provede operaci uložit a poskytuje prostředí **uložit jako** dialogové okno editoru. Prostředí pak zavolá zpět do editoru s <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5. Pokud se uživatel pokouší uložit bez názvu dokumentu (to znamená, že dříve neuloženého dokumentu), příkazu Uložit jako ve skutečnosti provedena.  
  
6. Prostředí pro příkazu Uložit jako, zobrazí dialogové okno Uložit jako, do výzvy k zadání názvu souboru.  
  
    Pokud se změnil se název souboru a pak hierarchii zodpovídá za aktualizace rámce dokumentu informace uložené v mezipaměti voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
   Pokud **uložit jako** příkaz přesune umístění dokumentu a hierarchie je citlivé na umístění dokumentu. pak v hierarchii je zodpovědný za předání vlastnictví okno otevřeného dokumentu do jiné hierarchie. Například k tomu dochází, pokud projekt sleduje, zda soubor je interní nebo externí soubor aplikace (různé) ve vztahu k projektu. Chcete-li změnit vlastnictví souboru do projektu s různorodými soubory pomocí následujícího postupu.  
  
## <a name="changing-file-ownership"></a>Změna vlastnictví souboru  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Chcete-li změnit vlastnictví souborů ostatních souborech projektu  
  
1.  Služba pro dotazování <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> rozhraní.  
  
     Ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> je vrácena.  
  
2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) způsob přenosu dokumentu do nové hierarchie. Provedení příkazu Uložit jako hierarchii volá tuto metodu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md)

