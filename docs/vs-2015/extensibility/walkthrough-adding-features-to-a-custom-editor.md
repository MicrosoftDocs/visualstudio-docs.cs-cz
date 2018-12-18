---
title: 'Návod: Přidání funkcí do vlastního editoru | Dokumentace Microsoftu'
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
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2379a488d042ab8905844c9c536f79ecb4b03268
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737044"
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Návod: Přidání funkcí do vlastního editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po vytvoření vlastního editoru můžete k němu přidat další funkce.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Chcete-li vytvořit editor pro balíček VSPackage  
  
1.  Vytvoření vlastního editoru pomocí šablony projektu balíček Visual Studio.  
  
     Další informace najdete v tématu [návod: vytvoření vlastního editoru](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Rozhodněte, jestli chcete editor pro podporu zobrazení jedné nebo více zobrazení.  
  
     Editor, který podporuje **nové okno** příkazu, nebo obsahuje zobrazení formuláře a zobrazení kódu, vyžaduje samostatnou dokumentu datové objekty a objekty zobrazení dokumentu. V editoru, který podporuje pouze jedno zobrazení je možné implementovat datový objekt dokumentu a objekt zobrazení dokumentu na stejný objekt.  
  
     Příklad více zobrazení, naleznete v tématu [podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementovat objekt pro vytváření editoru implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> rozhraní.  
  
     Další informace najdete v tématu [objekty pro vytváření editoru](../extensibility/editor-factories.md).  
  
4.  Rozhodněte, jestli chcete editor k použití aktivace na místě nebo zjednodušená vkládání pro správu okna dokumentu zobrazení objektu.  
  
     Zjednodušená vkládání okno editoru hostitelem zobrazení dokumentu standardu během místní aktivace okno editoru hostuje ovládací prvek ActiveX nebo jiný aktivní objekt jako jeho zobrazení dokumentu. Další informace najdete v tématu [zjednodušená vkládání](../extensibility/simplified-embedding.md) a [aktivace na místě](../misc/in-place-activation.md).  
  
5.  Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní pro zpracování příkazů.  
  
6.  Zadejte trvalost dokumentu a reakci na změny v externím souboru následujícím způsobem:  
  
    1.  Chcete-li zachovat soubor, implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> a <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> na váš editor dokumentu datový objekt.  
  
    2.  Chcete-li reagovat na změny externí soubor, implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> na váš editor dokumentu datový objekt.  
  
        > [!NOTE]
        >  Volání `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> k získání ukazatele na `IVsFileChangeEx`.  
  
7.  Koordinovat událostí úpravy dokumentu pomocí správy zdrojového kódu. To uděláte takto:  
  
    1.  Ukazatel na `IVsQueryEditQuerySave2` voláním `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Volání při výskytu první události edit <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody.  
  
         Tento parametr vyzve uživatele k rezervovat soubor, pokud není již rezervován. Je potřeba zpracovat stav "soubor není rezervován" aby se předešlo chybám  
  
    3.  Obdobně volat před uložením tohoto souboru, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> metody.  
  
         Tato metoda se zobrazí výzva k uložení souboru, pokud nebyla uložena, nebo pokud se změnil od posledního uložení.  
  
8.  Povolit **vlastnosti** okno k zobrazení vlastností vybraného textu v editoru. To uděláte takto:  
  
    1.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> výběr textu každý čas změny předáním hodnoty ve vaší implementaci <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Volání `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> služby k získání ukazatele na <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Povolit uživatelům přetahování položek mezi editoru a **nástrojů**, nebo mezi externích editorech (například Microsoft Word) a **nástrojů**. To uděláte takto:  
  
    1.  Implementace `IDropTarget` na editor k upozornění rozhraní IDE, editor je cíl přetažení.  
  
    2.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> rozhraní pro zobrazení, můžete povolit nebo zakázat položky v editoru **nástrojů**.  
  
    3.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> a volat `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> služby k získání ukazatel <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> rozhraní.  
  
         To umožňuje vašeho balíčku VSPackage pro přidání nové položky **nástrojů**.  
  
10. Rozhodněte, zda chcete další volitelné funkce pro editor.  
  
    -   Pokud chcete, aby váš editor pro podporu najít a nahradit příkazy, implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Pokud chcete použít okno nástroje osnovy dokumentu v editoru, implementovat `IVsDocOutlineProvider`.  
  
    -   Pokud chcete použít stavového řádku v editoru, implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> a volat `QueryService` pro <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> k získání ukazatele na `IVsStatusBar`.  
  
         Editor může například zobrazit řádku / informace o sloupci, režim výběru (datový proud stream / pole) a režim vložení (vložení / overstrike).  
  
    -   Pokud chcete, aby váš editor pro podporu `Undo` příkazu, doporučujeme použít model Správce akcí zpět OLE. Jako alternativu můžete použít editor popisovač `Undo` přímo příkazu.  
  
11. Vytvoření registru informace, včetně identifikátory GUID pro sady VSPackage, nabídky, editor a další funkce.  
  
     Následuje obecný příkladu vložíte do vašeho skriptu souboru .rgs ukazují, jak správně zaregistrovat editoru kódu.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Implementace podpora kontextové nápovědy.  
  
     To umožňuje poskytovat podporu pro položky v editoru Nápověda F1 a okna dynamické nápovědy. Další informace najdete v části [jak: poskytuje kontext pro editory](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Vystavení modelu automatizačních objektů z editoru implementací `IDispatch` rozhraní.  
  
     Další informace najdete v tématu [přispívání do modelu automatizace](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Robustní programování  
  
-   Je vytvořena instance editoru, když volá rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody. Pokud editor podporuje několik zobrazení `CreateEditorInstance` vytvoří data dokumentu a zobrazit objekty dokumentu. Pokud už je datový objekt dokumentu otevřít, nenulovým `punkDocDataExisting` je předána hodnota `IVsEditorFactory::CreateEditorInstance`. Vaše implementace objektu factory editoru musí zjistit, zda je existující objekt data dokumentu kompatibilní pomocí dotazu pro příslušné rozhraní. Další informace najdete v tématu [podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md).  
  
-   Pokud používáte zjednodušený postup pro vkládání, implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> rozhraní.  
  
-   Pokud se rozhodnete použít aktivace na místě, implementace následujících rozhraní:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  `IOleInPlaceComponent` Rozhraní se používá pro zabránění OLE 2 slučování nabídek.  
  
     Vaše `IOleCommandTarget` implementace zpracovává příkazy, jako **Vyjmout**, **kopírování**, a **vložit**. Při implementaci `IOleCommandTarget`, rozhodněte, zda editor vyžaduje svou vlastní souboru .vsct definovat vlastní struktury příkaz nabídky nebo pokud můžete implementovat standardní příkazy určené [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Obvykle editory použít a rozšířit rozhraní IDE nabídky a definovat jejich vlastní panely nástrojů. Často je ale nutné definovat vlastní specifické příkazy kromě pomocí rozhraní IDE sady standardních příkazů editoru. K tomuto účelu musí deklarovat editor standardní příkazy používá a v souboru .vsct definovat nové příkazy, kontextové nabídky, nejvyšší úrovně nabídky a panely nástrojů. Pokud vytvoříte místní aktivace editoru, pak implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> a definovat nabídek a panelů nástrojů editoru v souboru .vsct namísto použití OLE 2 slučování nabídek.  
  
-   Aby se zabránilo nakupení v uživatelském rozhraní příkaz nabídky, používejte stávajících příkazů v integrovaném vývojovém prostředí před inventing nových příkazů. Sdílené příkazy jsou definovány v SharedCmdDef.vsct a ShellCmdDef.vsct. Tyto soubory jsou nainstalovány ve výchozím nastavení v podadresáři VisualStudioIntegration\Common\Inc vaše [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] instalace.  
  
-   `ISelectionContainer` můžete vyjádřit jednu i více výběrů. Každý vybraný objekt je implementovaný jako `IDispatch` objektu.  
  
-   Implementuje rozhraní IDE `IOleUndoManager` jako služby přístupné <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> nebo jako objekt, který se dá vytvořit instance prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Váš editor implementuje `IOleUndoUnit` rozhraní pro každou `Undo` akce.  
  
-   Existují dvě místa vlastního editoru můžete zveřejnit objekty automatizace:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>Viz také  
 [Přispívání do modelu automatizace](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Postupy: Poskytnutí kontextu pro editory](../extensibility/how-to-provide-context-for-editors.md)

