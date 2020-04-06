---
title: Provádění příkazů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709582"
---
# <a name="command-implementation"></a>Implementace příkazu
Chcete-li implementovat příkaz v balíčku VSPackage, je nutné provést následující úkoly:

1. V souboru *.vsct* nastavte skupinu příkazů a přidejte do ní příkaz. Další informace naleznete v tématu [Visual Studio příkaz tabulka (.vsct) soubory](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

2. Zaregistrujte příkaz v sadě Visual Studio.

3. Implementujte příkaz.

V následujících částech je vysvětleno, jak zaregistrovat a implementovat příkazy.

## <a name="register-commands-with-visual-studio"></a>Registrace příkazů v sadě Visual Studio
 Pokud se váš příkaz má zobrazit v <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> nabídce, je nutné přidat do vspackage a použít jako hodnotu buď název nabídky nebo jeho ID prostředku.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Kromě toho je nutné zaregistrovat <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>příkaz s . Tuto službu můžete získat <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> pomocí metody, pokud je <xref:Microsoft.VisualStudio.Shell.Package>váš VSPackage odvozen z .

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

## <a name="implement-commands"></a>Implementace příkazů
 Existuje několik způsobů, jak implementovat příkazy. Pokud chcete statický příkaz nabídky, což je příkaz, který se vždy zobrazí stejným způsobem <xref:System.ComponentModel.Design.MenuCommand> a ve stejné nabídce, vytvořte příkaz pomocí, jak je znázorněno v příkladech v předchozí části. Chcete-li vytvořit statický příkaz, musíte zadat obslužnou rutinu události, která je zodpovědná za provedení příkazu. Vzhledem k tomu, že příkaz je vždy povolena a viditelná, není třeba zadat jeho stav sady Visual Studio. Pokud chcete změnit stav příkazu v závislosti na určitých podmínkách, můžete <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> vytvořit příkaz jako instanci třídy a v jeho `QueryStatus` konstruktoru poskytnout obslužnou rutinu události ke spuštění příkazu a obslužnou rutinu, která upozorní visual studio při změně stavu příkazu. Můžete také <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementovat jako součást třídy příkazu nebo můžete implementovat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> pokud poskytujete příkaz jako součást projektu. Dvě rozhraní a <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> třída všechny mají metody, které upozorňují Visual Studio na změnu stavu příkazu a další metody, které poskytují provádění příkazu.

 Když je příkaz přidán do služby příkazu, stane se jedním z řetězu příkazů. Při implementaci stav oznámení a spuštění metody pro příkaz, dbejte na to, poskytnout pouze pro tento konkrétní příkaz a předat všechny ostatní případy na ostatní příkazy v řetězci. Pokud se vám nepodaří předat příkaz <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>na (obvykle vrácením ), Visual Studio může přestat pracovat správně.

## <a name="querystatus-methods"></a>QueryStatus metody
 Pokud implementujete <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> nebo metodu, zkontrolujte identifikátor GUID sady příkazů, do které příkaz patří, a ID příkazu. Postupujte podle následujících pokynů:

- Pokud identifikátor GUID není rozpoznán, implementace <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>obou metod musí vrátit .

- Pokud implementace obou metod rozpozná identifikátor GUID, ale neimplementoval a <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>neimplementoval příkaz, měla by metoda vrátit .

- Pokud implementace obou metod rozpozná identifikátor GUID i příkaz, měla by metoda nastavit pole command-flags každého příkazu (v parametru) `prgCmds` pomocí následujících <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> příznaků:

  - `OLECMDF_SUPPORTED`: Příkaz je podporován.

  - `OLECMDF_INVISIBLE`: Příkaz by neměl být viditelný.

  - `OLECMDF_LATCHED`: Příkaz je zapnutý a zdá se, že byl zkontrolován.

  - `OLECMDF_ENABLED`: Příkaz je povolen.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Příkaz by měl být skrytý, pokud se zobrazí v místní nabídce.

  - `OLECMDF_NINCHED`: Příkaz je řadič nabídky a není povolen, ale jeho rozevírací seznam nabídky není prázdný a je stále k dispozici. (Tento příznak se používá zřídka.)

- Pokud byl příkaz definován v souboru *.vsct* s příznakem, `TextChanges` nastavte následující parametry:

  - Nastavte `rgwz` prvek parametru `pCmdText` na nový text příkazu.

  - Nastavte `cwActual` prvek parametru `pCmdText` na velikost příkazového řetězce.

Také se ujistěte, že aktuální kontext není funkce automatizace, pokud váš příkaz je speciálně určen pro zpracování funkcí automatizace.

Chcete-li označit, že podporujete určitý příkaz, vraťte <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Pro všechny ostatní příkazy vraťte <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.

V následujícím příkladu `QueryStatus` metoda nejprve zajistí, že kontext není automatizační funkcí, a pak najde správný identifikátor GUID sady příkazů a ID příkazu. Samotný příkaz je nastaven tak, aby byl povolen a podporován. Nejsou podporovány žádné další příkazy.

```csharp
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

## <a name="execution-methods"></a>Metody provádění
 Implementace `Exec` metody se podobá implementaci `QueryStatus` metody. Nejprve se ujistěte, že kontext není funkce automatizace. Potom otestujte identifikátor GUID i ID příkazu. Pokud identifikátor GUID nebo ID příkazu není rozpoznán, vraťte <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.

 Chcete-li příkaz zpracovat, <xref:Microsoft.VisualStudio.VSConstants.S_OK> spusťte jej a vraťte se, pokud je spuštění úspěšné. Váš příkaz je zodpovědný za detekci chyb a oznámení; proto vrátí kód chyby, pokud se spuštění nezdaří. Následující příklad ukazuje, jak by měla být implementována metoda spuštění.

```csharp
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

- [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
