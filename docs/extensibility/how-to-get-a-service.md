---
title: 'Postup: Získání služby | Dokumenty společnosti Microsoft'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710960"
---
# <a name="how-to-get-a-service"></a>Postup: Získání služby

Často potřebujete získat služby sady Visual Studio pro přístup k různým funkcím. Obecně platí, že služba sady Visual Studio poskytuje jedno nebo více rozhraní, které můžete použít. Většinu služeb můžete získat z balíčku VSPackage.

Všechny VSPackage, který <xref:Microsoft.VisualStudio.Shell.Package> je odvozen z a který byl správně umístěn můžete požádat o jakékoli globální služby. Vzhledem `Package` k <xref:System.IServiceProvider>tomu, že třída implementuje , všechny VSPackage, který je odvozen od `Package` je také poskytovatelem služeb.

Při Visual Studio <xref:Microsoft.VisualStudio.Shell.Package>načte <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , předá objekt u <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metody během inicializace. To se nazývá *siting* VSPackage. Třída `Package` zabalí tohoto poskytovatele služeb <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> a poskytuje metodu pro získání služeb.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Získání služby z inicializovaného balíčku VSPackage

1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX s názvem `GetServiceExtension`. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** vyhledáním "vsix".

2. Nyní přidejte vlastní šablonu položky příkazu s názvem **GetServiceCommand**. V dialogovém okně **Přidat novou položku** přejděte na položku**Rozšiřitelnost** **jazyka Visual C#** > a vyberte **vlastní příkaz**. V poli **Název** v dolní části okna změňte název příkazového souboru na *GetServiceCommand.cs*. Další informace o vytvoření vlastního příkazu naleznete [v příkazu Vytvořit rozšíření pomocí příkazu nabídky.](../extensibility/creating-an-extension-with-a-menu-command.md)

3. V *GetServiceCommand.cs*odstraňte tělo `MenuItemCommand` metody a přidejte následující kód:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Tento kód získá službu SVsActivityLog a <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> přetypovává ji do rozhraní, které lze použít k zápisu do protokolu aktivit. Příklad najdete v [tématu Postup: Použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).

4. Sestavení projektu a začít ladění. Zobrazí se experimentální instance.

5. V nabídce **Nástroje** experimentální instance najděte tlačítko **Invoke GetServiceCommand.** Po klepnutí na toto tlačítko by se mělo zobrazit okno se zprávou, ve které je uvedeno, že **služba Nalezen protokol aktivit.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Získání služby z okna nástroje nebo kontejneru ovládacího prvku

Někdy může být nutné získat službu z okna nástroje nebo kontejneru ovládacího prvku, který nebyl umístěn, nebo byl umístěn u poskytovatele služeb, který neví o požadované službě. Můžete například chtít zapisovat do protokolu aktivit z ovládacího prvku.

Statická <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metoda závisí na zprostředkovateli služeb uložené v mezipaměti, který je <xref:Microsoft.VisualStudio.Shell.Package> inicializován při prvním spuštění libovolného balíčku VSPackage odvozeného z je umístěn.

Vzhledem k tomu, že konstruktor VSPackage je volána před VSPackage je umístěn, globální služby jsou obvykle k dispozici z v rámci konstruktoru VSPackage. Postup: [Řešení potíží se službami](../extensibility/how-to-troubleshoot-services.md) pro řešení řešení řešení.

Zde je příklad způsobu, jak získat službu v okně nástroje nebo jiný non-VSPackage element.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Získání služby z objektu DTE

Můžete také získat <xref:EnvDTE.DTEClass> služby z objektu. Však musíte získat DTE objekt jako službu z VSPackage <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> nebo voláním statické metody.

DTE objekt implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, které můžete použít k <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>dotazování na službu pomocí .

Tady je postup, jak získat službu z objektu DTE.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>Viz také

- [Postup: Poskytnutí služby](../extensibility/how-to-provide-a-service.md)
- [Využívání a poskytování služeb](../extensibility/using-and-providing-services.md)
- [Základy služeb](../extensibility/internals/service-essentials.md)
