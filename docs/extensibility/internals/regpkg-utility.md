---
title: Nástroj RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f811eb37da730d63e199a0e378b8a9122143649e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724449"
---
# <a name="regpkg-utility"></a>Nástroj RegPkg
> [!NOTE]
> Upřednostňovaným způsobem, jak registrovat balíčky v aplikaci Visual Studio, je použití souborů. pkgdef. To umožňuje nasazení rozšíření bez nutnosti přístupu k systémovému registru, což je požadavek na nasazení VSIX. Soubory pkgdef se vytvářejí pomocí [nástroje CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Další informace o nasazení balíčku sady Visual Studio najdete v tématu [odeslání rozšíření sady Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 Nástroj RegPkg. exe registruje VSPackage pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a připraví ho pro nasazení. Tento nástroj se používá na pozadí během vývoje VSPackage. Spouští se jako součást procesu sestavení, takže můžete sestavit a spustit VSPackage v experimentálním podregistru.

 RegPkg může generovat skripty systémového registru v několika formátech. Tyto skripty můžete začlenit do projektů nasazení, jako jsou projekty. msi nebo Instalační služba systému Windows soubory XML sady nástrojů.

 RegPkg. exe se obvykle nachází v \<*cestě k instalaci sady Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg se řídí touto syntaxí:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root: root provádí registraci pod zadaným

 kořen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 /regfile: FileName vytvoří soubor. reg místo aktualizace registru.  Nelze použít s/vrgfile nebo/rgsfile nebo/wixfile.

 /rgsfile: FileName vytvoří soubor. rgs místo aktualizace registru.  Nelze použít s/vrgfile nebo/regfile nebo/wixfile.

 /vrgfile: FileName vytvoří soubor. vrg namísto aktualizace registru.  Nelze použít s/regfile nebo/rgsfile nebo/wixfile.

 /RGM vytvoří kromě souboru RGS i soubor. RGM.  Musí se kombinovat s/rgsfile.

 /wixfile: FileName vytvoří soubor, který je kompatibilní se sadou XML Instalační služba systému Windows, místo aktualizace registru.  Nelze použít s/regfile nebo/rgsfile nebo/vrgfile.

 /codebase vynutí registraci pomocí základu kódu místo sestavení.

 /Assembly je vynutí registraci pomocí sestavení místo základu kódu.

 /Unregister zruší registraci tohoto balíčku.  Nelze použít

 s/regfile nebo/vrgfile nebo/rgsfile nebo/wixfile.

## <a name="see-also"></a>Viz také:
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)
- [Řešení potíží s registrací balíčku RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)