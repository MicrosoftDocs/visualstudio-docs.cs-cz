---
title: Služba Essentials | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26bfa7ce51249adc883415d09689ed390b7dfabc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934402"
---
# <a name="service-essentials"></a>Základy služeb
Služba je kontrakt mezi dvěma rozšíření VSPackages. Jeden VSPackage poskytuje určitou sadu rozhraní pro jiné VSPackage využívat. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je kolekce rozšíření VSPackages, která poskytuje služby do jiné balíků VSPackages.  
  
 Můžete například použít službu SVsActivityLog získat IVsActivityLog rozhraní, který můžete použít k zápisu do protokolu aktivit. Další informace najdete v tématu [postupy: použití protokolu aktivit](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje také některé integrované služby, které nejsou registrovány. Rozšíření VSPackages můžete nahradit integrované nebo jiných služeb tím, že poskytuje přepsání služby. Smí obsahovat jenom jednu službu přepsání pro libovolnou službu.  
  
 Services k dispozici žádné možnosti rozpoznání. Proto musíte znát služby identifikátor (SID), který chcete používat službu, a musíte znát rozhraní, která poskytuje. Referenční dokumentace pro službu poskytuje tyto informace.  
  
- Rozšíření VSPackages, které poskytují služby, se nazývají poskytovatelé služeb.  
  
- Služby, které jsou k dispozici další balíčky VSPackages, se nazývají služeb global services.  
  
- Služby, které jsou k dispozici pouze pro sady VSPackage, která implementuje je, nebo na libovolný objekt, který vytvoří, se nazývají místních služeb.  
  
- Služby, které nahrazují integrované služby nebo služeb poskytovaných další balíčky, se nazývají přepsání služby.  
  
- Služby nebo přepsání služby jsou načtena na vyžádání, to znamená, je načteno poskytovatele služeb, když službu, kterou poskytuje požádá o jiný VSPackage.  
  
- Poskytovatel služeb pro podporu načítání na vyžádání, zaregistruje jeho služeb global services s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Další informace najdete v tématu [postupy: poskytování služby](../../extensibility/how-to-provide-a-service.md).  
  
- Po obdržení služby použijte [QueryInterface](/cpp/atl/queryinterface) (nespravovaný kód) nebo přetypování (spravovaný kód) Chcete-li získat požadované rozhraní, například:  
  
  ```vb  
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
  ```  
  
  ```csharp  
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  ```  
  
- Spravovaný kód odkazuje na službu podle jeho typu, zatímco nespravovaný kód odkazuje na službu podle její identifikátor GUID.  
  
- Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načte VSPackage, předá poskytovatel služeb VSPackage chcete dát VSPackage přístup ke službám global services. To se označuje jako "umístění" sady VSPackage.  
  
- Rozšíření VSPackages může být poskytovatelů služeb pro objekty, které vytvářejí. Například může formuláře odeslat žádost o službu barva jeho snímek, který může předat požadavky na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
- Spravované objekty, které jsou vnořeny hluboko, nebo není umístěna vůbec, může volat <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pro přímý přístup ke službám global services.   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>Použití GetGlobalService  
  
V některých případech budete muset získat službu z panelu nástrojů nebo ovládací prvek kontejneru, který nebyl byl umístěn, jinak byl umístěn u poskytovatele služeb, které neví o službu, kterou chcete. Můžete například chtít zapisovat do protokolu aktivit z v rámci ovládacího prvku. Další informace o těchto a dalších scénářů najdete v tématu [postupy: řešení potíží s služby](../../extensibility/how-to-troubleshoot-services.md).  
  
Většina služeb Visual Studio můžete získat voláním statické <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody.  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> spoléhá na služby uložený v mezipaměti je umístěna zprostředkovatele, který je inicializován při prvním jakékoli VSPackage odvozený z balíčku. Je nutné zaručit, že tato podmínka je splněna, jinak se připravit null služby.  
  
Naštěstí <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ve většině případů funguje správně.  
  
-   Pokud VSPackage poskytuje službu znáte jenom jiné VSPackage, VSPackage žádosti o služby je umístěn před VSPackage za předpokladu, že načtení služby.  
  
-   Pokud VSPackage vytvoří panel nástrojů, sady VSPackage je umístěn před vytvořením okna nástrojů.  
  
-   Pokud kontejneru ovládacího prvku je hostitelem nástroje okna vytvořeného rozhraním VSPackage, sady VSPackage je umístěn před vytvořením kontejneru ovládacího prvku.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Chcete-li získat službu z v rámci nástroje okna nebo ovládací prvek kontejneru  
  
-   Vložte tento kód v konstruktoru, okno nástroje nebo kontejneru ovládacího prvku:  
  
    ```csharp  
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```  
    ```vb  
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```  
    
    Tento kód získá služby SVsActivityLog a přetypování IVsActivityLog rozhraní, který slouží k zápisu do protokolu aktivit. Příklad najdete v tématu [postupy: použití protokolu aktivit](../../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Viz také  
 [Seznam dostupných služeb](../../extensibility/internals/list-of-available-services.md)   
 [Používání a poskytování služeb](../../extensibility/using-and-providing-services.md)   
 [Přetypování a převody typů](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Přetypování](/cpp/cpp/casting)