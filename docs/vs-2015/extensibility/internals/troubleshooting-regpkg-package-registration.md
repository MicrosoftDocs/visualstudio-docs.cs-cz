---
title: Řešení potíží s registrací balíčku RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241975e475252a18d5e5a91c6e8c4fb40c067a95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807455"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Řešení potíží s registrací balíčku RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Upřednostňovaným způsobem, jak registrovat balíčky v aplikaci Visual Studio, je použití souborů. pkgdef. To umožňuje nasazení rozšíření bez nutnosti přístupu k systémovému registru. Soubory pkgdef se vytvářejí pomocí [nástroje CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Pokud chcete balíček zaregistrovat pomocí RegPkg v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , musíte použít verzi RegPkg, která je pro váš balíček vhodná.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Verze RegPkg související s verzemi balíčků  
 Existují dvě verze RegPkg. V systému je obsažena jedna verze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Tuto verzi použijte k registraci balíčků, které byly vytvořeny pomocí jednoho z následujících sestavení:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   Nemůže registrovat balíčky, které byly sestaveny pomocí dřívějšího sestavení Microsoft.VisualStudio.Shell.dll.  
  
   Starší verze RegPkg mohou registrovat balíčky, které byly vytvořeny pomocí sestavení Microsoft.VisualStudio.Shell.dll. Nicméně nemůže registrovat balíčky sestavené pomocí novějších verzí tohoto sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Uvolnění produktu](../../misc/releasing-a-visual-studio-integration-product.md)
