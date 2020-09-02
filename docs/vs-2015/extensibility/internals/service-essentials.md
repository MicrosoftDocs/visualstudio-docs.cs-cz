---
title: Základy služby | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696071"
---
# <a name="service-essentials"></a>Základy služeb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Služba je smlouva mezi dvěma VSPackage. Jeden VSPackage poskytuje konkrétní sadu rozhraní, které se mají využít pro další VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] je kolekcí VSPackage, která poskytuje služby jiným VSPackage.  
  
 Službu SVsActivityLog můžete například použít k získání rozhraní IVsActivityLog, které můžete použít k zápisu do protokolu aktivit. Další informace najdete v tématu [Postupy: použití protokolu aktivit](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] také poskytuje některé předdefinované služby, které nejsou registrovány. Sady VSPackage můžou nahradit integrované nebo jiné služby poskytnutím přepsání služby. Pro jakoukoli službu je povoleno pouze jedno přepsání služby.  
  
 Služby nemají žádnou zjistitelnost. Proto musíte znát identifikátor služby (SID) služby, kterou chcete spotřebovat, a musíte znát, která rozhraní poskytuje. Tato informace je k dispozici v referenční dokumentaci k této službě.  
  
- VSPackage, které poskytují služby, se nazývají poskytovatelé služeb.  
  
- Služby, které jsou poskytovány jiným VSPackage, se nazývají globální služby.  
  
- Služby, které jsou k dispozici pouze pro VSPackage, které je implementují, nebo pro libovolný objekt, který vytvoří, se nazývají místní služby.  
  
- Služby, které nahrazují integrované služby nebo služby poskytované jinými balíčky, se nazývají přepsání služby.  
  
- Služby nebo přepsání služby se načítají na vyžádání, to znamená, že poskytovatel služeb se načte, když služba, kterou poskytuje, je vyžadovaná jiným rozhraním VSPackage.  
  
- Pro podporu načítání na vyžádání zaregistruje poskytovatel služeb své globální služby pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Další informace najdete v tématu [Registrace služeb](../../misc/registering-services.md).  
  
- Po získání služby použijte [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (nespravovaný kód) nebo přetypování (spravovaný kód), abyste získali požadované rozhraní, například:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- Spravovaný kód odkazuje na službu podle typu, zatímco nespravovaný kód odkazuje na službu pomocí jejího identifikátoru GUID.  
  
- Když [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] načte VSPackage, předá poskytovateli služeb pro VSPackage, aby získal přístup k globálním službám. Označuje se jako "umístění" sady VSPackage.  
  
- Sady VSPackage můžou být poskytovatelé služeb pro objekty, které vytvářejí. Například formulář může poslat požadavek na službu barev do svého rámce, který může požadavek předat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Spravované objekty, které jsou hluboko vnořené nebo nejsou na stejné úrovni, můžou volat <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pro přímý přístup ke globálním službám. Další informace naleznete v tématu [How to: use GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Viz také  
 [Seznam dostupných služeb](../../extensibility/internals/list-of-available-services.md)   
 [Používání a poskytování služeb](../../extensibility/using-and-providing-services.md)   
 [Přetypování a převody typů](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Přetypování](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
