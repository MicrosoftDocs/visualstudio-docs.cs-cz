---
title: Příkaz implementace | Dokumentace Microsoftu
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
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: be1bcecb740fb0c375d0f461639a8b0d5e40669a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765206"
---
# <a name="command-implementation"></a>Implementace příkazu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Implementace příkazu v sadě VSPackage, je třeba provést následující úkoly:  
  
1. V souboru .vsct nastavit skupinu příkazů a pak přidejte příkaz do ní. Další informace najdete v tématu [tabulky příkazů aplikace Visual Studio (. Vsct) soubory](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
2. Příkaz zaregistrujte pomocí sady Visual Studio.  
  
3. Implementace příkazu.  
  
   Následující části popisují, jak zaregistrovat a provádět příkazy.  
  
## <a name="registering-commands-with-visual-studio"></a>Registrace příkazy pomocí sady Visual Studio  
 Pokud váš příkaz se zobrazí v nabídce, je nutné přidat <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage a použijte jako hodnotu název nabídky nebo jeho ID prostředku.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Kromě toho je nutné zaregistrovat příkaz <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Tuto službu můžete získat pomocí <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodu, pokud vaše VSPackage je odvozen z <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Provádění příkazů  
 Existuje mnoho způsobů, jak implementovat příkazy. Příkaz statickou nabídku, což je příkaz, který se vždy zobrazí stejný způsobem a ve stejné nabídce, chcete-li vytvořit příkaz s použitím <xref:System.ComponentModel.Design.MenuCommand> podle příkladů v předchozí části. Vytvoření statické příkazu, je nutné zadat obslužnou rutinu události, která zodpovídá za provádění příkazu. Vzhledem k tomu, že příkaz je vždy povoleno a je viditelný, není nutné zajistit její stav se sadou Visual Studio. Pokud chcete změnit stav příkazu v závislosti na určitých podmínkách, můžete vytvořit příkaz jako jedna instance <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> třídy a konstruktoru, poskytuje obslužné rutiny události ke spuštění příkazu a stav dotazu obslužnou rutinu oznámit Visual Studio, když se změní stav příkazu. Můžete také implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> jako součást třídu příkazu nebo je můžete implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Pokud příkaz se poskytuje jako součást projektu. Tato dvě rozhraní a <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> všechny třídy mají metody, které upozornění na změnu stavu příkazu Visual Studio a dalších metodách, které poskytují provedení příkazu.  
  
 Když příkaz se přidá do příkazu služby, bude řetěz příkazů. Při implementaci metody stav oznámení a spuštění příkazu postará poskytují pouze s konkrétním příkazem a předávat všech ostatních případech k další příkazy v řetězci. Pokud příkaz předat (obvykle tak, že vrací <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), Visual Studio můžou přestat správně fungovat.  
  
## <a name="query-status-methods"></a>Stav metody dotazů  
 Při implementaci buď <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metody, zkontrolujte GUID sada, ke které patří příkaz příkazů a ID příkazu. Postupujte podle následujících pokynů:  
  
- Pokud identifikátor GUID není rozpoznána, musí vrátit implementaci některé z metod <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Pokud vaši implementaci některé z metod rozpozná identifikátor GUID, ale ve skutečnosti ještě implementována příkazu, pak metoda by měla vrátit <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Pokud vaše implementace některé z metod rozpozná GUID a příkaz, pak metoda by měla nastavit pole příznaků příkazů každý příkaz (v `prgCmds` parametr) pomocí následujících příznaků:  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Pokud příkaz je podporován.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Pokud příkaz by neměly být viditelné.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Pokud příkaz je zapnutá a byly vráceny se zobrazí.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Pokud je příkaz povolen.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Pokud příkaz by měl být skrytý, pokud se zobrazí v místní nabídce.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Pokud příkaz je kontroleru nabídky a není povolené, ale jeho seznamu rozevírací nabídky není prázdný a je stále k dispozici. (Tento příznak se používá jen zřídka.)  
  
- Pokud příkaz bylo definováno v souboru .vsct `TextChanges` příznak, nastavte následující parametry:  
  
  -   Nastavte `rgwz` elementu `pCmdText` parametr nový text příkazu.  
  
  -   Nastavte `cwActual` elementu `pCmdText` parametr velikosti řetězec příkazu.  
  
  Ujistěte se také, že aktuálním kontextu není funkce automatizace, pokud váš příkaz je určený speciálně pro zpracování funkcí automatizace.  
  
  Chcete-li označit, že podpory ke konkrétnímu příkazu, vraťte <xref:Microsoft.VisualStudio.VSConstants.S_OK>. U všech ostatních příkazů vrátí <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
  V následujícím příkladu metoda stav dotazu nejprve zajišťuje, že není funkce automatizace kontextu a potom vyhledá správný identifikátor GUID sady příkazů a ID příkazu. Samotný příkaz je nastavena na povolena a podporované. Ostatní příkazy se nepodporuje.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Spuštění metody  
 Implementace metody execute se podobá implementace metody stav dotazu. Nejprve zkontrolujte, zda kontext není funkce automatizace. Pak test pro identifikátor GUID a ID příkazu. Pokud identifikátor GUID nebo ID příkazu nebyla rozpoznána, vraťte <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 Zpracování příkazu, spusťte ji a vrátit <xref:Microsoft.VisualStudio.VSConstants.S_OK> Pokud spuštění úspěšné. Váš příkaz je zodpovědná za detekce chyb a oznámení; Proto se vrátí kód chyby, pokud se nezdaří spuštění. Následující příklad ukazuje, jak by měla být implementována metoda spuštění.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

