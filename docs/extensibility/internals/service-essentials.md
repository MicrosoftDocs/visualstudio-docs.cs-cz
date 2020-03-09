---
title: Základy služby | Microsoft Docs
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409710"
---
# <a name="service-essentials"></a>Základy služeb
Služba je smlouva mezi dvěma VSPackage. Jeden VSPackage poskytuje konkrétní sadu rozhraní, které se mají využít pro další VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je kolekce VSPackage, která poskytuje služby jiným VSPackage.

 Službu SVsActivityLog můžete například použít k získání rozhraní IVsActivityLog, které můžete použít k zápisu do protokolu aktivit. Další informace najdete v tématu [Postupy: použití protokolu aktivit](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] také poskytuje některé předdefinované služby, které nejsou registrovány. Sady VSPackage můžou nahradit integrované nebo jiné služby poskytnutím přepsání služby. Pro jakoukoli službu je povoleno pouze jedno přepsání služby.

 Služby nemají žádnou zjistitelnost. Proto musíte znát identifikátor služby (SID) služby, kterou chcete spotřebovat, a musíte znát, která rozhraní poskytuje. Tato informace je k dispozici v referenční dokumentaci k této službě.

- VSPackage, které poskytují služby, se nazývají poskytovatelé služeb.

- Služby, které jsou poskytovány jiným VSPackage, se nazývají globální služby.

- Služby, které jsou k dispozici pouze pro VSPackage, které je implementují, nebo pro libovolný objekt, který vytvoří, se nazývají místní služby.

- Služby, které nahrazují integrované služby nebo služby poskytované jinými balíčky, se nazývají přepsání služby.

- Služby nebo přepsání služby se načítají na vyžádání, to znamená, že poskytovatel služeb se načte, když služba, kterou poskytuje, je vyžadovaná jiným rozhraním VSPackage.

- Pro podporu načítání na vyžádání zaregistruje poskytovatel služeb své globální služby pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Další informace najdete v tématu [Postup: poskytování služby](../../extensibility/how-to-provide-a-service.md).

- Po získání služby použijte [QueryInterface](/cpp/atl/queryinterface) (nespravovaný kód) nebo přetypování (spravovaný kód), abyste získali požadované rozhraní, například:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Spravovaný kód odkazuje na službu podle typu, zatímco nespravovaný kód odkazuje na službu pomocí jejího identifikátoru GUID.

- Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načte VSPackage, předává poskytovateli služeb rozhraní VSPackage, aby přístup k globálním službám poskytoval rozhraní VSPackage. Označuje se jako "umístění" sady VSPackage.

- Sady VSPackage můžou být poskytovatelé služeb pro objekty, které vytvářejí. Například formulář může poslat požadavek na službu barev do svého rámce, což může předat požadavek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Spravované objekty, které jsou hluboko vnořené nebo nejsou na stejné úrovni, můžou volat <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pro přímý přístup ke globálním službám.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Použití GetGlobalService

Někdy může být nutné získat službu z okna nástroje nebo kontejneru ovládacího prvku, který nebyl zadaný, nebo jinak byl vytvořen s poskytovatelem služeb, který neví o požadované službě. Například můžete chtít zapisovat do protokolu aktivit z ovládacího prvku. Další informace o těchto a dalších scénářích najdete v tématu [How to: Troubleshooting Services](../../extensibility/how-to-troubleshoot-services.md).

Většinu služeb sady Visual Studio můžete získat voláním metody static <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> spoléhá na poskytovatele služby uložené v mezipaměti, který je inicializován při prvním spuštění všech rozhraní VSPackage odvozených od balíčku. Musíte zaručit, že je tato podmínka splněná, nebo je možné ji připravit na službu s hodnotou null.

Naštěstí <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funguje správně ve většině času.

- Pokud VSPackage poskytuje službu známou pouze pro jiný VSPackage, rozhraní VSPackage požadující službu je umístěno dříve, než bude načtena služba VSPackage.

- Pokud je okno nástroje vytvořeno pomocí VSPackage, rozhraní VSPackage je umístěno před vytvořením okna nástroje.

- Pokud je kontejner ovládacího prvku hostován oknem nástrojů vytvořeným VSPackage, rozhraní VSPackage je umístěno před vytvořením kontejneru ovládacího prvku.

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

    Tento kód získá službu SVsActivityLog a přetypování ji na rozhraní IVsActivityLog, které lze použít k zápisu do protokolu aktivit. Příklad naleznete v tématu [How to: Use a log Activity](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Viz také

- [Seznam dostupných služeb](../../extensibility/internals/list-of-available-services.md)
- [Používání a poskytování služeb](../../extensibility/using-and-providing-services.md)
- [Přetypování a převody typů](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Přetypování](/cpp/cpp/casting)