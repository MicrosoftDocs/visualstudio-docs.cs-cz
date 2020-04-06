---
title: RegPkg Utility | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705640"
---
# <a name="regpkg-utility"></a>Nástroj RegPkg
> [!NOTE]
> Upřednostňovaným způsobem registrace balíčků v sadě Visual Studio je použití souborů .pkgdef. To umožňuje nasazení rozšíření bez nutnosti přístupu k systémovému registru, což je požadavek pro nasazení VSIX. Pkgdef soubory jsou vytvořeny pomocí [CreatePkgDef Utility](../../extensibility/internals/createpkgdef-utility.md). Další informace o nasazení balíčků sady Visual Studio naleznete v [tématu Odesílání rozšíření sady Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 Nástroj RegPkg.exe registruje Balíček [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSpackage a připravuje jej pro nasazení. Tento nástroj se používá na pozadí během vývoje VSPackage. Spustí se jako součást procesu sestavení, takže můžete sestavit a spustit VSPackage v experimentální podregistru.

 RegPkg může generovat skripty systémových registrů v několika formátech. Tyto skripty můžete začlenit do projektů nasazení, jako jsou projekty MSI nebo soubory nástrojů XML Instalační služby systému Windows.

 Program RegPkg.exe je \<obvykle umístěn v *instalační cestě sady Visual Studio SDK*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg následuje tuto syntaxi:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Provádí registraci pod zadaným

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kořenové.

 /regfile:FileName Vytvoří soubor REG namísto aktualizace registru.  Nelze použít s /vrgfile nebo /rgsfile nebo /wixfile.

 /rgsfile:FileName Vytvoří soubor RGS namísto aktualizace registru.  Nelze použít s /vrgfile nebo /regfile nebo /wixfile.

 /vrgfile:FileName Vytvoří soubor .vrg, nikoli aktualizaci registru.  Nelze použít s souborem /regfile nebo /rgsfile nebo /wixfile.

 /rgm Vytvoří soubor RGM kromě souboru rgs.  Musí být kombinován s /rgsfile.

 /wixfile:FileName Vytvoří soubor kompatibilní s sadou nástrojů XML instalační služby systému Windows, nikoli aktualizaci registru.  Nelze použít s souborem /regfile nebo /rgsfile nebo /vrgfile.

 /codebase vynutí registraci s CodeBase spíše než sestavení.

 /assembly Forces registrace s sestavení spíše než CodeBase.

 /unregister Zruší registraci tohoto balíčku.  Nelze použít

 s /regfile nebo /vrgfile nebo /rgsfile nebo /wixfile.

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)
- [Řešení potíží s registrací balíčku RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
