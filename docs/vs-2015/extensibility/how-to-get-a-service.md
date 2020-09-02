---
title: 'Postupy: získání služby | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ef86b8cde506aad3e00aa6b5dbc6470c0087de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204178"
---
# <a name="how-to-get-a-service"></a>Postupy: Získání služby
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pro přístup k různým funkcím často potřebujete získat služby sady Visual Studio. Obecně platí, že služba Visual Studio poskytuje jedno nebo více rozhraní, které můžete použít. Většinu služeb můžete získat ze sady VSPackage.  
  
 Všechny VSPackage, které jsou odvozeny z <xref:Microsoft.VisualStudio.Shell.Package> a které byly správně na pracovišti, si mohou vyžádat jakoukoli globální službu. Vzhledem k tomu, že třída balíčku implementuje <xref:System.IServiceProvider> , jakýkoli VSPackage, který je odvozen z balíčku, je také poskytovatelem služeb.  
  
 Když Visual Studio načte a <xref:Microsoft.VisualStudio.Shell.Package> , předá <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodě během inicializace. To se označuje *jako umístění* VSPackage. Třída Package zabalí tohoto poskytovatele služeb a poskytuje <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodu pro získání služeb.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Získání služby z inicializovaného VSPackage  
  
1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekt VSIX s názvem `GetServiceExtension` . Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** v části **Visual C#/rozšiřitelnost**.  
  
2. Nyní přidejte šablonu vlastní položky příkazu s názvem **GetServiceCommand**. V dialogovém okně **Přidat novou položku** přejít na **Visual C#/rozšiřitelnost** a vyberte **vlastní příkaz**. V poli **název** v dolní části okna změňte název souboru příkazů na **GetServiceCommand.cs**. Další informace o tom, jak vytvořit vlastní příkaz, [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3. V GetServiceCommand.cs odeberte tělo metody MenuItemCommand a přidejte následující kód:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Tento kód získá službu SVsActivityLog a přetypování ji na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> rozhraní, které lze použít k zápisu do protokolu aktivit. Příklad naleznete v tématu [How to: Use a log Activity](../extensibility/how-to-use-the-activity-log.md).  
  
4. Sestavte projekt a spusťte ladění. Objeví se experimentální instance.  
  
5. V nabídce nástroje experimentální instance najděte tlačítko **vyvolat GetServiceCommand** . Po kliknutí na toto tlačítko by se měla zobrazit okno se zprávou s informacemi o tom, že **se našla služba protokolu aktivit.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Získání služby z okna nástroje nebo kontejneru ovládacího prvku  
 Někdy může být nutné získat službu z okna nástroje nebo kontejneru ovládacího prvku, který nebyl zadaný, nebo jinak byl vytvořen s poskytovatelem služeb, který neví o požadované službě. Například můžete chtít zapisovat do protokolu aktivit z ovládacího prvku.  
  
 Statická <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metoda závisí na poskytovateli služby uložené v mezipaměti, který je inicializován při prvním spuštění jakékoli sady VSPackage odvozené od aplikace <xref:Microsoft.VisualStudio.Shell.Package> .  
  
 Vzhledem k tomu, že konstruktor VSPackage je volán před tím, než je web VSPackage, nejsou v rámci konstruktoru VSPackage obvykle k dispozici globální služby. Alternativní řešení naleznete v tématu [How to: Troubleshooting Services](../extensibility/how-to-troubleshoot-services.md) .  
  
 Zde je příklad způsobu, jak získat službu v okně nástroje nebo jiném prvku, který není VSPackage.  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Získání služby z objektu DTE  
 Můžete také získat služby z <xref:EnvDTE.DTEClass> objektu. Je však nutné získat objekt DTE jako službu ze sady VSPackage nebo voláním statické <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody.  
  
 Objekt DTE implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , který můžete použít k dotazování na službu pomocí <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> .  
  
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
 [Postupy: poskytování služby](../extensibility/how-to-provide-a-service.md)   
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)   
 [Základy služeb](../extensibility/internals/service-essentials.md)
