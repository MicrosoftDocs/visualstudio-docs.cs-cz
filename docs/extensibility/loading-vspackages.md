---
title: Nakládka vspackages | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702956"
---
# <a name="load-vspackages"></a>Načíst vspackages
VSPackages jsou načteny do sady Visual Studio pouze v případě, že je požadována jejich funkce. Například VSPackage je načten, když Visual Studio používá factory projektu nebo služby, které implementuje VSPackage. Tato funkce se nazývá zpožděné načítání, které se používá vždy, když je to možné ke zlepšení výkonu.

> [!NOTE]
> Visual Studio můžete určit určité informace VSPackage, jako jsou příkazy, které nabízí VSPackage bez načtení VSPackage.

 VSPackages lze nastavit automatické načtení v kontextu určitého uživatelského rozhraní (UI), například při otevření řešení. Atribut <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> nastaví tento kontext.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Automatické načtení balíčku VSPackage v určitém kontextu

- Přidejte `ProvideAutoLoad` atribut do atributů VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Podívejte se na výčtová <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> pole pro seznam kontextů uživatelského rozhraní a jejich hodnoty GUID.

- Nastavte zarážku <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> v metodě.

- Sestavení VSPackage a začít ladění.

- Načtěte řešení nebo ho vytvořte.

     VSPackage načte a zastaví na zarážky.

## <a name="force-a-vspackage-to-load"></a>Vynutit načtení balíčku VSPackage
 Za určitých okolností VSPackage může mít vynutit další VSPackage načíst. Například lehký VSPackage může načíst větší VSPackage v kontextu, který není k dispozici jako CMDUIContext.

 Můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> metodu k vynucení VSPackage načíst.

- Vložte tento <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> kód do metody VSPackage, která vynutí načtení jiného balíčku VSPackage:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Když je inicializován vSPackage, bude vynutit `PackageToBeLoaded` zatížení.

     Silové načítání by nemělo být použito pro komunikaci VSPackage. Místo toho [použijte použít a poskytovat služby.](../extensibility/using-and-providing-services.md)

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../extensibility/internals/vspackages.md)
