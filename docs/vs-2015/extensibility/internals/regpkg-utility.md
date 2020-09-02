---
title: Nástroj RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64819781"
---
# <a name="regpkg-utility"></a>Nástroj RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Upřednostňovaným způsobem, jak registrovat balíčky v aplikaci Visual Studio, je použití souborů. pkgdef. To umožňuje nasazení rozšíření bez nutnosti přístupu k systémovému registru, což je požadavek na nasazení VSIX. Soubory pkgdef se vytvářejí pomocí [nástroje CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Další informace o nasazení balíčku sady Visual Studio najdete v tématu [odeslání rozšíření sady Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Nástroj RegPkg.exe registruje VSPackage pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a připraví ho pro nasazení. Tento nástroj se používá na pozadí během vývoje VSPackage. Spouští se jako součást procesu sestavení, takže můžete sestavit a spustit VSPackage v experimentálním podregistru.  
  
 RegPkg může generovat skripty systémového registru v několika formátech. Tyto skripty můžete začlenit do projektů nasazení, jako jsou projekty. msi nebo Instalační služba systému Windows soubory XML sady nástrojů.  
  
 RegPkg.exe se obvykle nachází v \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg se řídí touto syntaxí:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root: root  
 Provede registraci pod zadaným  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zobrazuje.  
  
 /regfile: název souboru  
 Místo aktualizace registru vytvoří soubor. reg.  Nelze použít s/vrgfile nebo/rgsfile nebo/wixfile.  
  
 /rgsfile: název souboru  
 Vytvoří soubor. rgs místo aktualizace registru.  Nelze použít s/vrgfile nebo/regfile nebo/wixfile.  
  
 /vrgfile: název souboru  
 Místo aktualizace registru vytvoří soubor. vrg.  Nelze použít s/regfile nebo/rgsfile nebo/wixfile.  
  
 /rgm  
 Společně s souborem RGS vytvoří soubor. RGM.  Musí se kombinovat s/rgsfile.  
  
 /wixfile: název souboru  
 Místo aktualizace registru vytvoří soubor kompatibilní se sadou nástrojů XML Instalační služba systému Windows.  Nelze použít s/regfile nebo/rgsfile nebo/vrgfile.  
  
 /codebase  
 Vynutí registraci pomocí základu kódu místo sestavení.  
  
 /Assembly je  
 Vynutí registraci pomocí sestavení místo základu kódu.  
  
 /Unregister  
 Zruší registraci tohoto balíčku.  Nelze použít  
  
 s/regfile nebo/vrgfile nebo/rgsfile nebo/wixfile.  
  
## <a name="see-also"></a>Viz také  
 [Uvolnění produktu](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Řešení potíží s registrací balíčku RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
