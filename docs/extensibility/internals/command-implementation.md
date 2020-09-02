---
title: Implementace příkazu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709582"
---
# <a name="command-implementation"></a>Implementace příkazu
Chcete-li implementovat příkaz v VSPackage, je nutné provést následující úlohy:

1. V souboru *. vsct* nastavte skupinu příkazů a přidejte do ní příkaz. Další informace naleznete v tématu [soubory tabulek příkazů sady Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

2. Zaregistrujte příkaz v aplikaci Visual Studio.

3. Implementujte příkaz.

Následující části vysvětlují, jak registrovat a implementovat příkazy.

## <a name="register-commands-with-visual-studio"></a>Registrace příkazů pomocí sady Visual Studio
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

## <a name="implement-commands"></a>Implementovat příkazy
 Existuje několik způsobů, jak implementovat příkazy. Pokud chcete použít statický příkaz nabídky, který je vždy stejný jako příkaz a v téže nabídce, vytvořte příkaz pomocí příkazu, <xref:System.ComponentModel.Design.MenuCommand> jak je znázorněno v příkladech v předchozí části. Chcete-li vytvořit statický příkaz, je nutné poskytnout obslužnou rutinu události, která je zodpovědná za provedení příkazu. Vzhledem k tomu, že je příkaz vždy povolen a viditelný, není nutné zadávat jeho stav do sady Visual Studio. Chcete-li změnit stav příkazu v závislosti na určitých podmínkách, můžete vytvořit příkaz jako instanci <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> třídy a v jeho konstruktoru poskytnout obslužnou rutinu události pro spuštění příkazu a `QueryStatus` obslužné rutiny, které upozorní sadu Visual Studio, když se změní stav příkazu. Můžete také implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> jako součást třídy příkazu nebo můžete implementovat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Pokud poskytujete příkaz jako součást projektu. Tato dvě rozhraní a <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Třída mají všechny metody, které upozorňují na změnu stavu příkazu, a další metody, které poskytují spuštění příkazu.

 Když se do příkazového řádku přidá příkaz, dojde k jeho jednomu z řetězců příkazů. Při implementaci oznamování stavu a metod provádění pro příkaz se ujistěte, že zadáte pouze pro tento konkrétní příkaz a předáte všechny ostatní případy jiným příkazům v řetězu. Pokud se nedaří předat příkaz na (obvykle vrácením <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> ), Visual Studio může přestat pracovat správně.

## <a name="querystatus-methods"></a>Metody QueryStatus
 Pokud implementujete buď <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> , nebo metodu, vyhledejte identifikátor GUID sady příkazů, do které příkaz patří, a ID příkazu. Postupujte podle těchto pokynů:

- Pokud identifikátor GUID není rozpoznán, vaše implementace obou metod musí vracet <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP> .

- Pokud vaše implementace obou metod rozpoznává identifikátor GUID, ale neimplementovala příkaz, metoda by měla vrátit <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

- Pokud vaše implementace obou metod rozpoznává identifikátor GUID i příkaz, pak by metoda měla nastavit pole příznak příkazu každého příkazu (v `prgCmds` parametru) pomocí následujících <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> příznaků:

  - `OLECMDF_SUPPORTED`: Příkaz je podporován.

  - `OLECMDF_INVISIBLE`: Příkaz by neměl být viditelný.

  - `OLECMDF_LATCHED`: Příkaz je přepnut na a zdá se, že byl zkontrolován.

  - `OLECMDF_ENABLED`: Příkaz je povolen.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Příkaz by měl být skrytý, pokud se zobrazí v místní nabídce.

  - `OLECMDF_NINCHED`: Příkaz je kontroler nabídek a není povolen, ale seznam jeho rozevíracích nabídek není prázdný a je stále k dispozici. (Tento příznak se používá zřídka.)

- Pokud byl příkaz definován v souboru *. vsct* s `TextChanges` příznakem, nastavte následující parametry:

  - Nastavte `rgwz` element `pCmdText` parametru na nový text příkazu.

  - Nastavte `cwActual` element `pCmdText` parametru na velikost řetězce příkazu.

Také se ujistěte, že aktuální kontext není funkce automatizace, pokud váš příkaz není určen konkrétně pro zpracování funkcí automatizace.

Chcete-li určit, že budete podporovat konkrétní příkaz, vraťte <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Pro všechny ostatní příkazy vraťte <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

V následujícím příkladu `QueryStatus` Metoda nejprve zajistí, že kontext není funkce automatizace a pak najde správný identifikátor GUID sady příkazů a ID příkazu. Samotný příkaz je nastaven na povoleno a podporováno. Žádné jiné příkazy nejsou podporovány.

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

## <a name="execution-methods"></a>Metody spuštění
 Implementace metody se `Exec` podobá implementaci `QueryStatus` metody. Nejprve se ujistěte, že kontext není funkce automatizace. Pak otestujte identifikátor GUID i identifikátor příkazu. Pokud identifikátor GUID nebo ID příkazu není rozpoznán, vrátí <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

 Chcete-li zpracovat příkaz, spusťte jej a vraťte se, <xref:Microsoft.VisualStudio.VSConstants.S_OK> Pokud je spuštění úspěšné. Váš příkaz zodpovídá za detekci a oznamování chyb; Proto pokud se spuštění nepovede, vrátí kód chyby. Následující příklad ukazuje, jak by měla být implementována metoda provedení.

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

- [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
