---
title: Registrace služeb | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: 64f2afa6e853978e919e466f91475bed1e8d698c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62971287"
---
# <a name="registering-services"></a>Registrace služeb
Pro podporu načítání na vyžádání musí poskytovatel služeb registrovat své globální služby pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Během vývoje jsou poskytovatelé spravovaných služeb registrovat služby a přepsání služby přidáním atributů ke zdrojovému kódu pro balíčky a následným sestavením balíčků v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí. Tím spustíte nástroj RegPkg.exe ve výsledném sestavení, zaregistrujete balíček a připravíte ho k nasazení. Další informace najdete v tématu [Postup: registrace služby](../misc/how-to-register-a-service.md).  
  
 Nespraví poskytovatelé služeb musí zaregistrovat služby, které poskytují, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v části služby nebo v oddílu přepsání služby v registru systému. Následující fragment souboru REG ukazuje, jak může být služba SVsTextManager, zaregistrovaná:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 V předchozím příkladu je číslo verze verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , například 7,1 nebo 8,0, klíč {F5E7E71D-1401-11D1-883B-0000F87579D2} je identifikátor (SID) služby, SVsTextManager a výchozí hodnota {F5E7E720-1401-11D1-883B-0000F87579D2} je identifikátor GUID balíčku VSPackage správce textu, který tuto službu poskytuje.  
  
## <a name="remote-services-and-background-threads"></a>Vzdálené služby a vlákna na pozadí  
 Služby, které zadáte, nejsou automaticky k dispozici vzdáleně nebo pro vlákna na pozadí. Aby byly k dispozici, je nutné sestavit a zaregistrovat knihovnu typů.  
  
 Z nespravovaného kódu, který používá knihovnu aplikace Visual Studio (VSL), můžete svou knihovnu typů zaregistrovat tímto způsobem:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 Ze spravovaného kódu můžete přidat krok po sestavení, například:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>Viz také  
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)   
 [Základy služeb](../extensibility/internals/service-essentials.md)