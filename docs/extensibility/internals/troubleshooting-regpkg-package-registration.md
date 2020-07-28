---
title: Řešení potíží s registrací balíčku RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5266579ff235a0f6c4f3e555d79d5a00de2c194
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234858"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Řešení potíží s registrací balíčku RegPkg
> [!NOTE]
> Upřednostňovaným způsobem, jak registrovat balíčky v aplikaci Visual Studio, je použití souborů. pkgdef. To umožňuje nasazení rozšíření bez nutnosti přístupu k systémovému registru. Soubory pkgdef se vytvářejí pomocí [nástroje CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Pokud chcete balíček zaregistrovat pomocí RegPkg v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , musíte použít verzi RegPkg, která je pro váš balíček vhodná.

## <a name="regpkg-versions-related-to-package-versions"></a>Verze RegPkg související s verzemi balíčků
 Existují dvě verze RegPkg. V systému je obsažena jedna verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Tuto verzi použijte k registraci balíčků, které byly vytvořeny pomocí jednoho z následujících sestavení:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Nemůže registrovat balíčky, které byly sestaveny pomocí dřívějšího sestavení Microsoft.VisualStudio.Shell.dll.

   Starší verze RegPkg mohou registrovat balíčky, které byly vytvořeny pomocí sestavení Microsoft.VisualStudio.Shell.dll. Nicméně nemůže registrovat balíčky sestavené pomocí novějších verzí tohoto sestavení.

## <a name="see-also"></a>Viz také:
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)
- [Řešení potíží s Visual Studiem](/troubleshoot/visualstudio/welcome-visual-studio/)
