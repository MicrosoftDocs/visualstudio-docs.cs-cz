---
title: Služba Essentials | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90cec13c403194c70b9d44cff349b53495a0e160
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776457"
---
# <a name="service-essentials"></a>Základy služeb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Služba je kontrakt mezi dvěma rozšíření VSPackages. Jeden VSPackage poskytuje určitou sadu rozhraní pro jiné VSPackage využívat. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] je kolekce rozšíření VSPackages, která poskytuje služby do jiné balíků VSPackages.  
  
 Můžete například použít službu SVsActivityLog získat IVsActivityLog rozhraní, který můžete použít k zápisu do protokolu aktivit. Další informace najdete v tématu [postupy: použití protokolu aktivit](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poskytuje také některé integrované služby, které nejsou registrovány. Rozšíření VSPackages můžete nahradit integrované nebo jiných služeb tím, že poskytuje přepsání služby. Smí obsahovat jenom jednu službu přepsání pro libovolnou službu.  
  
 Services k dispozici žádné možnosti rozpoznání. Proto musíte znát služby identifikátor (SID), který chcete používat službu, a musíte znát rozhraní, která poskytuje. Referenční dokumentace pro službu poskytuje tyto informace.  
  
-   Rozšíření VSPackages, které poskytují služby, se nazývají poskytovatelé služeb.  
  
-   Služby, které jsou k dispozici další balíčky VSPackages, se nazývají služeb global services.  
  
-   Služby, které jsou k dispozici pouze pro sady VSPackage, která implementuje je, nebo na libovolný objekt, který vytvoří, se nazývají místních služeb.  
  
-   Služby, které nahrazují integrované služby nebo služeb poskytovaných další balíčky, se nazývají přepsání služby.  
  
-   Služby nebo přepsání služby jsou načtena na vyžádání, to znamená, je načteno poskytovatele služeb, když službu, kterou poskytuje požádá o jiný VSPackage.  
  
-   Poskytovatel služeb pro podporu načítání na vyžádání, zaregistruje jeho služeb global services s [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Další informace najdete v tématu [registrace služby](../../misc/registering-services.md).  
  
-   Po obdržení služby použijte [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (nespravovaný kód) nebo přetypování (spravovaný kód) Chcete-li získat požadované rozhraní, například:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Spravovaný kód odkazuje na službu podle jeho typu, zatímco nespravovaný kód odkazuje na službu podle její identifikátor GUID.  
  
-   Když [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] načte VSPackage, předá poskytovatel služeb VSPackage chcete dát VSPackage přístup ke službám global services. To se označuje jako "umístění" sady VSPackage.  
  
-   Rozšíření VSPackages může být poskytovatelů služeb pro objekty, které vytvářejí. Například může formuláře odeslat žádost o službu barva jeho snímek, který může předat požadavky na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   Spravované objekty, které jsou vnořeny hluboko, nebo není umístěna vůbec, může volat <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pro přímý přístup ke službám global services. Další informace najdete v tématu [postupy: použití GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Viz také  
 [Seznam dostupných služeb](../../extensibility/internals/list-of-available-services.md)   
 [Používání a poskytování služeb](../../extensibility/using-and-providing-services.md)   
 [Přetypování a převody typů](http://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Přetypování](http://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)

