---
title: Instalace mimo složku rozšíření se souborem VSIX V3 | Microsoft Docs
description: Přečtěte si informace o instalaci prostředků rozšíření sady Visual Studio SDK mimo složku rozšíření a umístění, která jsou platná.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24b1e1a73ff588e5531eec2025c8a3c9e94760a4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898445"
---
# <a name="install-outside-the-extensions-folder"></a>Instalace mimo složku rozšíření

Od verze Visual Studio 2017 a VSIX V3 (verze 3) se prostředky rozšíření dají instalovat mimo složku rozšíření. V současné době jsou povolena následující umístění jako platná umístění instalace (kde [INSTALLDIR] je namapována na instalační adresář instance sady Visual Studio):

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets (podporuje se jenom pro Visual Studio 2017; zastaralé pro Visual Studio 2019 a novější)

> [!NOTE]
> Formát VSIX neumožňuje instalaci mimo strukturu instalační složky sady Visual Studio. 

Aby bylo možné podporovat instalaci do těchto adresářů, musí být VSIX nainstalováno pro jednotlivé instance počítače. To lze povolit zaškrtnutím políčka "Všichni uživatelé" v Návrháři Extension. vsixmanifest Designer:

![kontrolovat všechny uživatele](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Jak nastavit InstallRoot

Chcete-li nastavit instalační adresáře, můžete použít okno **vlastnosti** v aplikaci Visual Studio. Například můžete nastavit `InstallRoot` vlastnost odkazu na projekt na jedno z výše uvedených umístění:

![instalace kořenových vlastností](media/install-root-properties.png)

Tím se do odpovídající vlastnosti přidá nějaká metadata `ProjectReference` v souboru. csproj projektu VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Pokud dáváte přednost, můžete soubor. csproj upravit přímo.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Jak nastavit podcestu pod InstallRoot

Pokud byste chtěli nainstalovat do dílčí cesty pod, můžete to udělat tak, že `InstallRoot` nastavíte vlastnost, která je `VsixSubPath` stejně jako `InstallRoot` vlastnost. Řekněme například, že se má výstup odkazu na projekt nainstalovat do: [INSTALLDIR] \MSBuild\MyCompany\MySDK\1.0. To lze snadno provést pomocí návrháře vlastností:

![nastavit dílčí cestu](media/set-subpath.png)

Odpovídající změny. csproj budou vypadat takto:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Další informace

Změny návrháře vlastností se použijí na více než jenom odkazy na projekt. můžete `InstallRoot` také nastavit metadata pro položky v projektu (pomocí stejných metod popsaných výše).
