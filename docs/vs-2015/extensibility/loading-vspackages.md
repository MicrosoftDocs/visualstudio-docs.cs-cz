---
title: Načítání VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802260"
---
# <a name="loading-vspackages"></a>Načítání rozšíření VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sady VSPackage jsou načteny do sady Visual Studio pouze v případě, že jsou jejich funkce požadovány. Například VSPackage je načten, když aplikace Visual Studio používá objekt pro vytváření projektu nebo službu, kterou VSPackage implementuje. Tato funkce se nazývá opožděné načítání, které se používá, kdykoli je to možné, ke zvýšení výkonu.  
  
> [!NOTE]
> Visual Studio může určit určité informace VSPackage, například příkazy, které VSPackage nabízí, bez načítání VSPackage.  
  
 Sady VSPackage lze nastavit na automatické načítání v konkrétním kontextu uživatelského rozhraní, například při otevření řešení. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Atribut nastaví tento kontext.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Automatické načítání VSPackage v konkrétním kontextu  
  
- Přidejte `ProvideAutoLoad` atribut do atributů VSPackage:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>Seznam kontextů uživatelského rozhraní a jejich hodnot GUID naleznete v výčtových polích pro.  
  
- Nastavte zarážku v <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodě.  
  
- Sestavte rozhraní VSPackage a spusťte ladění.  
  
- Načtěte řešení nebo ho vytvořte.  
  
     Rozhraní VSPackage načte a zastaví na zarážce.  
  
## <a name="forcing-a-vspackage-to-load"></a>Vynucení načtení VSPackage  
 Za určitých okolností může být nutné, aby VSPackage vynutil načtení jiného VSPackage. Například odlehčené VSPackage mohou načíst větší VSPackage v kontextu, který není k dispozici jako CMDUIContext.  
  
 Metodu můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> k vynucení načtení VSPackage.  
  
- Vložte tento kód do <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody VSPackage, která vynutí načtení další VSPackage:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Po inicializaci rozhraní VSPackage se vynutí `PackageToBeLoaded` načtení.  
  
     Pro komunikaci VSPackage by se nemělo používat vynucené načítání. Použijte místo toho [použití a poskytování služeb](../extensibility/using-and-providing-services.md) .  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Použití vlastního atributu k registraci VSPackage  
 V některých případech může být nutné vytvořit nový registrační atribut pro vaše rozšíření. Registrační atributy můžete použít k přidání nových klíčů registru nebo k přidání nových hodnot do existujících klíčů. Nový atribut musí být odvozen z <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> a musí přepsat <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody a.  
  
## <a name="creating-a-registry-key"></a>Vytvoření klíče registru  
 V následujícím kódu vlastní atribut vytvoří **vlastní** podklíč pod klíčem pro VSPackage, který je zaregistrován.  
  
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
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Vytvoření nové hodnoty v existujícím klíči registru  
 Můžete přidat vlastní hodnoty do existujícího klíče. Následující kód ukazuje, jak přidat novou hodnotu do registračního klíče VSPackage.  
  
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
