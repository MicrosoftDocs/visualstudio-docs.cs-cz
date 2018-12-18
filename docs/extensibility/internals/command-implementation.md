---
title: Příkaz implementace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f002e660b2c3b745e4a7ea67f715b613b96bd0a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510436"
---
# <a name="command-implementation"></a>Implementace příkazu
Implementace příkazu v sadě VSPackage, je třeba provést následující úkoly:  
  
1.  V *.vsct* souborů, nastavit skupiny příkazů a potom k němu přidejte příkaz. Další informace najdete v tématu [soubory tabulky (.vsct) příkazů sady Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).
  
2.  Příkaz zaregistrujte pomocí sady Visual Studio.  
  
3.  Implementace příkazu.  
    
Následující části popisují, jak zaregistrovat a provádět příkazy.  
  
## <a name="register-commands-with-visual-studio"></a>Příkazy registru pomocí sady Visual Studio  
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
  
## <a name="implement-commands"></a>Implementace příkazy  
 Existuje mnoho způsobů, jak implementovat příkazy. Příkaz statickou nabídku, což je příkaz, který se vždy zobrazí stejný způsobem a ve stejné nabídce, chcete-li vytvořit příkaz s použitím <xref:System.ComponentModel.Design.MenuCommand> podle příkladů v předchozí části. Vytvoření statické příkazu, je nutné zadat obslužnou rutinu události, která zodpovídá za provádění příkazu. Vzhledem k tomu, že příkaz je vždy povoleno a je viditelný, není nutné zajistit její stav se sadou Visual Studio. Pokud chcete změnit stav příkazu v závislosti na určitých podmínkách, můžete vytvořit příkaz jako jedna instance <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> třídy a v konstruktoru, poskytují obslužnou rutinu události ke spuštění příkazu a `QueryStatus` obslužná rutina upozornit Vizuálu Studio, když se změní stav příkazu. Můžete také implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> jako součást třídu příkazu nebo je můžete implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Pokud příkaz se poskytuje jako součást projektu. Tato dvě rozhraní a <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> všechny třídy mají metody, které upozornění na změnu stavu příkazu Visual Studio a dalších metodách, které poskytují provedení příkazu.  
  
 Když příkaz se přidá do příkazu služby, bude řetěz příkazů. Při implementaci metody stav oznámení a spuštění příkazu postará poskytují pouze s konkrétním příkazem a předávat všech ostatních případech k další příkazy v řetězci. Pokud příkaz předat (obvykle tak, že vrací <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), Visual Studio můžou přestat správně fungovat.  
  
## <a name="querystatus-methods"></a>QueryStatus metody  
 Při implementaci buď <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metody, zkontrolujte GUID sada, ke které patří příkaz příkazů a ID příkazu. Postupujte podle následujících pokynů:  
  
-   Pokud identifikátor GUID není rozpoznána, musí vrátit implementaci některé z metod <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.  
  
-   Pokud vaše implementace některé z metod rozpozná identifikátor GUID, ale ještě implementována příkazu, pak metoda by měla vrátit <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
-   Pokud vaše implementace některé z metod rozpozná GUID a příkaz, pak metoda by měla nastavit pole příznaků příkazů každý příkaz (v `prgCmds` parametr) pomocí následujících <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> příznaky:  
  
    -   `OLECMDF_SUPPORTED`: Tento příkaz se nepodporuje.  
  
    -   `OLECMDF_INVISIBLE`: Tento příkaz by neměly být viditelné.  
  
    -   `OLECMDF_LATCHED`: Tento příkaz je zapnutá a byly vráceny se zobrazí.  
  
    -   `OLECMDF_ENABLED`: Příkaz je povolen.  
  
    -   `OLECMDF_DEFHIDEONCTXTMENU`: Tento příkaz skryt, pokud se zobrazí v místní nabídce.  
  
    -   `OLECMDF_NINCHED`: Tento příkaz je kontroleru nabídky a není povolené, ale jeho seznamu rozevírací nabídky není prázdný a je stále k dispozici. (Tento příznak se používá jen zřídka.)  
  
-   Pokud byl příkaz definovaný v *.vsct* souboru `TextChanges` příznak, nastavte následující parametry:  
  
    -   Nastavte `rgwz` elementu `pCmdText` parametr nový text příkazu.  
  
    -   Nastavte `cwActual` elementu `pCmdText` parametr velikosti řetězec příkazu.  
  

Ujistěte se také, že aktuálním kontextu není funkce automatizace, pokud váš příkaz je určený speciálně pro zpracování funkcí automatizace.  
  
Chcete-li označit, že podpory ke konkrétnímu příkazu, vraťte <xref:Microsoft.VisualStudio.VSConstants.S_OK>. U všech ostatních příkazů vrátí <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
V následujícím příkladu `QueryStatus` metoda nejprve zajišťuje, že není funkce automatizace kontextu a pak vyhledá správný identifikátor GUID sady příkazů a ID příkazu. Samotný příkaz je nastavena na povolena a podporované. Ostatní příkazy se nepodporuje.  
  
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
 Provádění `Exec` způsob se podobá provádění `QueryStatus` metody. Nejprve zkontrolujte, zda kontext není funkce automatizace. Pak test pro identifikátor GUID a ID příkazu. Pokud identifikátor GUID nebo ID příkazu nebyla rozpoznána, vraťte <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)