---
title: Nástroj RegPkg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d677aaf155e533c27a775f3995b53dd59b65385
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130944"
---
# <a name="regpkg-utility"></a>Nástroj RegPkg
> [!NOTE]
>  Pomocí souborů .pkgdef je upřednostňovaný způsob, jak zaregistrovat balíčky v sadě Visual Studio. To umožňuje aniž by museli získat přístup k registru systému, který představuje požadavek pro nasazení VSIX pro rozšíření nasazení. Pkgdef soubory jsou vytvořeny pomocí [CreatePkgDef nástroj](../../extensibility/internals/createpkgdef-utility.md). Další informace o nasazení balíčku sady Visual Studio najdete v tématu [přesouvání rozšíření Visual Studia](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Nástroj RegPkg.exe zaregistruje VSPackage s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a připraví je k nasazení. Tento nástroj se používá na pozadí během vývoje VSPackage. Tak, aby můžete sestavit a spustit VSPackage v experimentální hive, spouští se jako součást procesu sestavení.  
  
 RegPkg mohou vytvářet skripty registru systému v různých formátech. Můžete začlenit tyto skripty v projekty nasazení, jako jsou projekty .msi nebo soubory sada nástrojů XML pro instalační program systému Windows.  
  
 RegPkg.exe se obvykle nachází ve \< *cesta instalace Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg dodržuje tuto syntaxi:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Provádí registraci v rámci zadaného  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kořenový adresář.  
  
 /RegFile:filename  
 Vytvoří soubor .reg spíše než aktualizace registru.  Nelze použít s /vrgfile nebo /rgsfile nebo /wixfile.  
  
 /rgsfile:filename  
 Vytvoří soubor .rgs spíše než aktualizace registru.  Nelze použít s /vrgfile nebo /regfile nebo /wixfile.  
  
 /vrgfile:filename  
 Vytvoří soubor .vrg spíše než aktualizace registru.  Nelze použít s /regfile nebo /rgsfile nebo /wixfile.  
  
 /rgm  
 Vytvoří soubor .rgm kromě rgs souboru.  Musí být kombinován s /rgsfile.  
  
 /wixfile:filename  
 Vytvoří soubor kompatibilní s sada nástrojů Windows Installer XML místo aktualizace registru.  Nelze použít s /regfile nebo /rgsfile nebo /vrgfile.  
  
 /codebase  
 Vynutí registrace CodeBase než sestavení.  
  
 /Assembly  
 Vynutí registrace pomocí sestavení na rozdíl od základu kódu.  
  
 / zrušení registrace  
 Zruší registraci tohoto balíčku.  Nelze použít  
  
 s /regfile nebo /vrgfile nebo /rgsfile nebo /wixfile.  
  
## <a name="see-also"></a>Viz také  
 [Balíčky VSPackage](../../extensibility/internals/vspackages.md)  
 [Řešení potíží s registrací balíčku RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)