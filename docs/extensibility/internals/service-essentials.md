---
title: Základy služeb | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8817ca48ff0a3f44a973986a173e647ce89c662c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303237"
---
# <a name="service-essentials"></a>Základy služeb
Služba je smlouva mezi dvěma Balíčky VSPackages. Jeden VSPackage poskytuje konkrétní sadu rozhraní pro jiné VSPackage využívat. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]je sama o sobě kolekce VSPackages, která poskytuje služby pro jiné VSPackages.

 Můžete například použít službu SVsActivityLog k získání rozhraní IVsActivityLog, které můžete použít k zápisu do protokolu aktivit. Další informace naleznete v [tématu How to: Use the Activity Log](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]poskytuje také některé vestavěné služby, které nejsou registrovány. VSPackages můžete nahradit vestavěné nebo jiné služby poskytnutím přepsání služby. Pro každou službu je povoleno pouze jedno přepsání služby.

 Služby nemají zjistitelnost. Proto musíte znát identifikátor služby (SID) služby, kterou chcete využívat, a musíte vědět, která rozhraní poskytuje. Tyto informace poskytuje referenční dokumentace pro službu.

- VSPackages, které poskytují služby, se nazývají poskytovatelé služeb.

- Služby, které jsou poskytovány do jiných VSPackages se nazývají globální služby.

- Služby, které jsou k dispozici pouze VSPackage, který je implementuje, nebo jakýkoli objekt, který vytvoří, se nazývají místní služby.

- Služby, které nahrazují předdefinované služby nebo služby poskytované jinými balíčky, se nazývají přepsání služby.

- Služby nebo přepsání služby jsou načteny na vyžádání, to znamená, že poskytovatel služeb je načten, když je služba, kterou poskytuje, požadována jiným balíčkem VSPackage.

- Pro podporu načítání na vyžádání registruje poskytovatel služeb [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]své globální služby u společnosti . Další informace naleznete v [tématu How to: Provide a Service](../../extensibility/how-to-provide-a-service.md).

- Po získání služby použijte [QueryInterface](/cpp/atl/queryinterface) (nespravovaný kód) nebo přetypování (spravovaný kód) k získání požadovaného rozhraní, například:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Spravovaný kód odkazuje na službu podle jejího typu, zatímco nespravovaný kód odkazuje na službu podle jeho GUID.

- Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načtení VSPackage, předá poskytovatele služeb VSPackage poskytnout VSPackage přístup ke globálním službám. To se označuje jako "siting" VSPackage.

- VSPackages mohou být poskytovateli služeb pro objekty, které vytvářejí. Formulář může například odeslat požadavek na barevnou službu do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]jeho rámce, který může požadavek předat společnosti .

- Spravované objekty, které jsou hluboce vnořené <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> nebo nejsou umístěny vůbec, může volat po přímém přístupu ke globálním službám.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Použití služby GetGlobalService

Někdy může být nutné získat službu z okna nástroje nebo kontejneru ovládacího prvku, který nebyl umístěn, nebo byl umístěn u poskytovatele služeb, který neví o požadované službě. Můžete například chtít zapisovat do protokolu aktivit z ovládacího prvku. Další informace o těchto a dalších scénářích naleznete v [tématu How to: Troubleshoot Services](../../extensibility/how-to-troubleshoot-services.md).

Většinu služeb sady Visual Studio můžete <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> získat voláním statické metody.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>spoléhá na zprostředkovatele služeb uložený v mezipaměti, který je inicializován při prvním vspackage odvozený z Package je umístěn. Musíte zaručit, že tato podmínka je splněna, jinak být připraven na službu null.

Naštěstí funguje <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> správně většinu času.

- Pokud VSPackage poskytuje službu známou pouze jiný VSPackage, VSPackage požadující službu je umístěn před VSPackage poskytující službu je načten.

- Pokud okno nástroje je vytvořen VSPackage, VSPackage je umístěn před vytvořením okna nástroje.

- Pokud je kontejner ovládacího prvku hostován oknem nástroje vytvořeným balíčkem VSPackage, je vbalíčku VSPackage umístěn před vytvořením kontejneru ovládacího prvku.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Získání služby z okna nástroje nebo kontejneru ovládacího prvku

- Vložte tento kód do konstruktoru, okna nástroje nebo kontejneru ovládacího prvku:

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

    Tento kód získá službu SVsActivityLog a přetypovává ji do rozhraní IVsActivityLog, které lze použít k zápisu do protokolu aktivit. Příklad najdete v [tématu Postup: Použití protokolu aktivit](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Viz také

- [Seznam dostupných služeb](../../extensibility/internals/list-of-available-services.md)
- [Používání a poskytování služeb](../../extensibility/using-and-providing-services.md)
- [Přetypování a převody typů](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Přetypování](/cpp/cpp/casting)