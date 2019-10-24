---
title: Řešení potíží s registrací balíčku RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 386a1a17c036207d122e4b3c7cb142a628dcfe38
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722268"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Řešení potíží s registrací balíčku RegPkg
> [!NOTE]
> Upřednostňovaným způsobem, jak registrovat balíčky v aplikaci Visual Studio, je použití souborů. pkgdef. To umožňuje nasazení rozšíření bez nutnosti přístupu k systémovému registru. Soubory pkgdef se vytvářejí pomocí [nástroje CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 K registraci balíčku pomocí RegPkg v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musíte použít verzi RegPkg, která je pro váš balíček vhodná.

## <a name="regpkg-versions-related-to-package-versions"></a>Verze RegPkg související s verzemi balíčků
 Existují dvě verze RegPkg. V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je k dispozici jedna verze. Tuto verzi použijte k registraci balíčků, které byly vytvořeny pomocí jednoho z následujících sestavení:

1. Microsoft. VisualStudioShell. 9.0. dll

2. Microsoft. VisualStudioShell. 10.0. dll

3. Microsoft. VisualStudioShell. 11.0. dll

   Nemůže registrovat balíčky, které byly sestaveny pomocí staršího sestavení Microsoft. VisualStudio. Shell. dll.

   Starší verze RegPkg může registrovat balíčky, které byly sestaveny pomocí sestavení Microsoft. VisualStudio. Shell. dll. Nicméně nemůže registrovat balíčky sestavené pomocí novějších verzí tohoto sestavení.

## <a name="see-also"></a>Viz také:
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)