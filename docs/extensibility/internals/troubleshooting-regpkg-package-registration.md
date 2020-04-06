---
title: Poradce při potížích regpkg registrace balíčku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704331"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Řešení potíží s registrací balíčku RegPkg
> [!NOTE]
> Upřednostňovaným způsobem registrace balíčků v sadě Visual Studio je použití souborů .pkgdef. To umožňuje nasazení rozšíření bez nutnosti přístupu k systémovému registru. Pkgdef soubory jsou vytvořeny pomocí [CreatePkgDef Utility](../../extensibility/internals/createpkgdef-utility.md).

 Chcete-li zaregistrovat balíček [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pomocí programu RegPkg v aplikaci , musíte použít verzi regpkg, která je vhodná pro váš balíček.

## <a name="regpkg-versions-related-to-package-versions"></a>Verze RegPkg související s verzemi balíčků
 Existují dvě verze RegPkg. Jedna verze je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]součástí aplikace . Tato verze slouží k registraci balíčků, které byly vytvořeny pomocí jednoho z následujících sestavení:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Nemůže zaregistrovat balíčky, které byly vytvořeny pomocí dřívějšího sestavení Microsoft.VisualStudio.Shell.dll.

   Starší verze RegPkg můžete zaregistrovat balíčky, které byly vytvořeny pomocí sestavení Microsoft.VisualStudio.Shell.dll. Však nelze zaregistrovat balíčky vytvořené pomocí novějších verzí tohoto sestavení.

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)
