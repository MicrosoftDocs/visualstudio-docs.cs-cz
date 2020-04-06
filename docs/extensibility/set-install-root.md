---
title: Instalace mimo složky rozšíření s VSIX v3 | Dokumenty společnosti Microsoft
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700186"
---
# <a name="install-outside-the-extensions-folder"></a>Instalace mimo složku rozšíření

Počínaje Visual Studio 2017 a VSIX v3 (verze 3), prostředky rozšíření lze nainstalovat mimo složky rozšíření. V současné době jsou následující umístění povolena jako platná umístění instalace (kde je [INSTALLDIR] mapována na instalační adresář instance sady Visual Studio):

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schémata
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licence
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets (podporováno pouze pro Visual Studio 2017; zastaralé pro Visual Studio 2019 a novější)

> [!NOTE]
> Formát VSIX neumožňuje instalaci mimo strukturu instalačních složek sady Visual Studio. 

Pro podporu instalace do těchto adresářů, VSIX musí být nainstalován "per-instance per-machine". To lze povolit zaškrtnutím zaškrtávacího políčka "všichni uživatelé" v návrháři extension.vsixmanifest:

![kontrola všech uživatelů](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Jak nastavit InstallRoot

Chcete-li nastavit instalační adresáře, můžete použít okno **Vlastnosti** v sadě Visual Studio. Můžete například nastavit `InstallRoot` vlastnost odkazu na projekt na jedno z výše uvedených umístění:

![instalace kořenových vlastností](media/install-root-properties.png)

Tím přidáte některá metadata `ProjectReference` do odpovídající vlastnosti uvnitř souboru .csproj projektu VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Soubor .csproj můžete upravit přímo, pokud dáváte přednost.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Jak nastavit podcestu pod InstallRoot

Pokud chcete nainstalovat do podcesty pod `InstallRoot`, můžete tak učinit `VsixSubPath` nastavením vlastnosti stejně `InstallRoot` jako vlastnost. Řekněme například, že chceme, aby se výstup odkazu na projekt nainstaloval na "[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0". Můžeme to udělat snadno s nemovitostmi designer:

![nastavit podcestu](media/set-subpath.png)

Odpovídající změny .csproj budou vypadat takto:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Další informace

Změny návrháře vlastností platí pro více než jen odkazy na projekt; můžete nastavit `InstallRoot` metadata pro položky uvnitř projektu také (pomocí stejných metod popsaných výše).
