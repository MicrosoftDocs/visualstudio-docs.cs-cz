---
title: Načítání rozšíření VSPackages | Dokumentace Microsoftu
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
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e351f49ea3e9579202e21868361e5d6f3d53b8fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753884"
---
# <a name="loading-vspackages"></a>Načítání rozšíření VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozšíření VSPackages se načtou do sady Visual Studio pouze v případě jejich funkce je povinný. Například VSPackage se načte, když Visual Studio používá objekt pro vytváření projektu nebo služba, která implementuje sady VSPackage. Tato funkce je volána opožděné načtení, který se používá vždy, když je možné zvýšit výkon.  
  
> [!NOTE]
>  Visual Studio můžete určit určité VSPackage informace, jako jsou příkazy, které nabízí VSPackage bez načtení sady VSPackage.  
  
 Rozšíření VSPackages lze nastavit na automaticky načíst v kontextu konkrétní uživatelské rozhraní (UI), například při otevření řešení. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Atribut nastaví tento kontext.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Autoloading VSPackage v určitém kontextu  
  
-   Přidat `ProvideAutoLoad` atribut VSPackage atributy:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Zobrazit výčet pole <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> seznam kontexty uživatelského rozhraní a jejich hodnoty identifikátor GUID.  
  
-   Nastavit zarážku <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
-   Sestavení sady VSPackage a spusťte ladění.  
  
-   Načítání řešení nebo vytvořit novou.  
  
     Sady VSPackage načte a zastaví na zarážce.  
  
## <a name="forcing-a-vspackage-to-load"></a>Vynucení VSPackage načtení  
 Za určitých okolností může mít VSPackage vynutit jiný VSPackage, který se má načíst. Zjednodušené VSPackage může například načíst větší VSPackage v kontextu, který není k dispozici jako CMDUIContext.  
  
 Můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> metoda přinutit VSPackage načíst.  
  
-   Vložte tento kód do <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metoda sady VSPackage, která vynutí jiného VSPackage načíst:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Při inicializaci sady VSPackage, vynutí `PackageToBeLoaded` načíst.  
  
     Platnost načítání by neměl použít pro komunikaci VSPackage. Použití [Using a poskytování služeb](../extensibility/using-and-providing-services.md) místo.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Pomocí vlastního atributu k registraci VSPackage  
 V některých případech budete muset vytvořit nový atribut registrace pro vaše rozšíření. Přidat nové klíče registru nebo přidat nové hodnoty pro existující klíče, můžete použít atributy registrace. Nový atribut musí být odvozen od <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, a musí přepsat <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> a <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody.  
  
## <a name="creating-a-registry-key"></a>Vytváří se klíč registru  
 Následující kód vytvoří vlastní atribut **vlastní** podklíče pod klíčem pro sady VSPackage, která je registrována.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Vytváří se nová hodnota v rámci existující klíč registru  
 Vlastní hodnoty můžete přidat do existujícího klíče. Následující kód ukazuje, jak přidat novou hodnotu balíčku VSPackage registrační klíč.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)

