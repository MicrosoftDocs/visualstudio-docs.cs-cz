---
title: Načítání VSPackage | Microsoft Docs
description: Přečtěte si o načítání VSPackage v aplikaci Visual Studio, včetně opožděného načítání, které se používá, kdykoli je to možné, ke zvýšení výkonu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 39a58bcbad79191f54a7b4eeb2aa12e90d8a6e44
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073284"
---
# <a name="load-vspackages"></a>Načíst VSPackage
Sady VSPackage jsou načteny do sady Visual Studio pouze v případě, že jsou jejich funkce požadovány. Například VSPackage je načten, když aplikace Visual Studio používá objekt pro vytváření projektu nebo službu, kterou VSPackage implementuje. Tato funkce se nazývá opožděné načítání, které se používá, kdykoli je to možné, ke zvýšení výkonu.

> [!NOTE]
> Visual Studio může určit určité informace VSPackage, například příkazy, které VSPackage nabízí, bez načítání VSPackage.

 Sady VSPackage lze nastavit na automatické načítání v konkrétním kontextu uživatelského rozhraní, například při otevření řešení. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>Atribut nastaví tento kontext.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Automatické načtení VSPackage v konkrétním kontextu

- Přidejte `ProvideAutoLoad` atribut do atributů VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>Seznam kontextů uživatelského rozhraní a jejich hodnot GUID naleznete v výčtových polích pro.

- Nastavte zarážku v <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodě.

- Sestavte rozhraní VSPackage a spusťte ladění.

- Načtěte řešení nebo ho vytvořte.

     Rozhraní VSPackage načte a zastaví na zarážce.

## <a name="force-a-vspackage-to-load"></a>Vynutit načtení VSPackage
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

     Pro komunikaci VSPackage by se nemělo používat vynucené načítání. Místo toho použijte [a poskytněte služby](../extensibility/using-and-providing-services.md) .

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../extensibility/internals/vspackages.md)
