---
title: Implementace příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a208fabd3d205793763698cde0f6fe367c7bb8b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195058"
---
# <a name="command-implementation"></a>Implementace příkazu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Chcete-li implementovat příkaz v VSPackage, je nutné provést následující úlohy:  
  
1. V souboru. vsct nastavte skupinu příkazů a přidejte do ní příkaz. Další informace naleznete v tématu [tabulka příkazů sady Visual Studio (. Vsct) soubory](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2. Zaregistrujte příkaz v aplikaci Visual Studio.  
  
3. Implementujte příkaz.  
  
   Následující části vysvětlují, jak registrovat a implementovat příkazy.  
  
## <a name="registering-commands-with-visual-studio"></a>Registrace příkazů v aplikaci Visual Studio  
 Pokud je váš příkaz zobrazen v nabídce, je nutné přidat <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> do VSPackage a použít jako hodnotu buď jako název nabídky, nebo její ID prostředku.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Kromě toho je nutné příkaz zaregistrovat pomocí <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> . Tuto službu můžete získat pomocí <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metody, pokud je váš VSPackage odvozen od <xref:Microsoft.VisualStudio.Shell.Package> .  
  
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
  
## <a name="implementing-commands"></a>Implementace příkazů  
 Existuje několik způsobů, jak implementovat příkazy. Pokud chcete použít statický příkaz nabídky, který je vždy stejný jako příkaz a v téže nabídce, vytvořte příkaz pomocí příkazu, <xref:System.ComponentModel.Design.MenuCommand> jak je znázorněno v příkladech v předchozí části. Chcete-li vytvořit statický příkaz, je nutné poskytnout obslužnou rutinu události, která je zodpovědná za provedení příkazu. Vzhledem k tomu, že je příkaz vždy povolen a viditelný, není nutné zadávat jeho stav do sady Visual Studio. Chcete-li změnit stav příkazu v závislosti na určitých podmínkách, můžete vytvořit příkaz jako instanci <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> třídy a v jeho konstruktoru poskytnout obslužnou rutinu události pro spuštění příkazu a obslužné rutiny stavu dotazu, aby při změně stavu příkazu informovaly sadu Visual Studio. Můžete také implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> jako součást třídy příkazu nebo můžete implementovat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Pokud poskytujete příkaz jako součást projektu. Tato dvě rozhraní a <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Třída mají všechny metody, které upozorňují na změnu stavu příkazu, a další metody, které poskytují spuštění příkazu.  
  
 Když se do příkazového řádku přidá příkaz, dojde k jeho jednomu z řetězců příkazů. Při implementaci oznamování stavu a metod provádění pro příkaz se ujistěte, že zadáte pouze pro tento konkrétní příkaz a předáte všechny ostatní případy jiným příkazům v řetězu. Pokud se nedaří předat příkaz na (obvykle vrácením <xref:Microsoft.VisualStudio.OLE.Interop.Constants> ), Visual Studio může přestat pracovat správně.  
  
## <a name="query-status-methods"></a>Metody stavu dotazů  
 Pokud implementujete buď <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> , nebo metodu, vyhledejte identifikátor GUID sady příkazů, do které příkaz patří, a ID příkazu. Postupujte podle těchto pokynů:  
  
- Pokud identifikátor GUID není rozpoznán, vaše implementace obou metod musí vracet <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
- Pokud vaše implementace obou metod rozpoznává identifikátor GUID, ale nemá ve skutečnosti implementován příkaz, pak by metoda měla vrátit <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
- Pokud vaše implementace obou metod rozpoznává identifikátor GUID i příkaz, pak by metoda měla nastavit pole příznak příkazu každého příkazu (v `prgCmds` parametru) pomocí následujících příznaků:  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> je-li příkaz podporován.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Pokud by se příkaz neměl zobrazovat.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Pokud je příkaz zapnutý a zdá se, že je zaškrtnutý.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Pokud je příkaz povolený.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Pokud by měl být příkaz skrytý, pokud se zobrazí v místní nabídce.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> je-li příkaz řadičem nabídky a není povolen, ale seznam jeho rozevírací nabídky není prázdný a je stále k dispozici. (Tento příznak se používá zřídka.)  
  
- Pokud byl příkaz definován v souboru. vsct s `TextChanges` příznakem, nastavte následující parametry:  
  
  - Nastavte `rgwz` element `pCmdText` parametru na nový text příkazu.  
  
  - Nastavte `cwActual` element `pCmdText` parametru na velikost řetězce příkazu.  
  
  Také se ujistěte, že aktuální kontext není funkce automatizace, pokud váš příkaz není určen konkrétně pro zpracování funkcí automatizace.  
  
  Chcete-li určit, že budete podporovat konkrétní příkaz, vraťte <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Pro všechny ostatní příkazy vraťte <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
  V následujícím příkladu metoda dotaz-stav nejprve zajistí, že kontext není funkce automatizace a pak najde správný identifikátor GUID sady příkazů a ID příkazu. Samotný příkaz je nastaven na povoleno a podporováno. Žádné jiné příkazy nejsou podporovány.  
  
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
  
## <a name="execution-methods"></a>Metody spuštění  
 Implementace metody Execute se podobá implementaci metody dotazu-status. Nejprve se ujistěte, že kontext není funkce automatizace. Pak testujte identifikátor GUID i identifikátor příkazu. Pokud identifikátor GUID nebo ID příkazu není rozpoznán, vrátí <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
 Chcete-li zpracovat příkaz, spusťte jej a vraťte se, <xref:Microsoft.VisualStudio.VSConstants.S_OK> Pokud je spuštění úspěšné. Váš příkaz zodpovídá za detekci a oznamování chyb; Proto pokud se spuštění nepovede, vrátí kód chyby. Následující příklad ukazuje, jak by měla být implementována metoda provedení.  
  
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
