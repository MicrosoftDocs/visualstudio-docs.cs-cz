---
title: Uchování dat v souboru projektu MSBuild | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706687"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Trvalá data v souboru projektu nástroje MSBuild
Podtyp projektu může být nutné zachovat data specifická pro podtyp do souboru projektu pro pozdější použití. Podtyp projektu používá trvalost souboru projektu ke splnění následujících požadavků:

1. Zachovat data použitá jako součást vytváření projektu. (Další informace o modulu microsoft build engine, naleznete v tématu [MSBuild](../../msbuild/msbuild.md).) Informace týkající se sestavení mohou buď:

    1. Data nezávislá na konfiguraci. To znamená data uložená v elementech MSBuild s prázdnými nebo chybějícími podmínkami.

    2. Data závislá na konfiguraci. To znamená data uložená v elementech MSBuild, která jsou podmíněna pro konkrétní konfiguraci projektu. Například:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Zachovat data, která není relevantní pro sestavení. Tato data mohou být vyjádřena ve volném formátu XML, který není ověřen proti schématu XML.

    1. Data nezávislá na konfiguraci.

    2. Data závislá na konfiguraci.

## <a name="persisting-build-related-information"></a>Trvalé informace související se sestavením
 Trvalost dat užitečných pro vytváření projektu je zpracována prostřednictvím MSBuild. Systém MSBuild udržuje hlavní tabulku informací souvisejících s sestavením. Podtypy projektu jsou zodpovědné za přístup k těmto datům získat a nastavit hodnoty vlastností. Podtypy projektu můžete také rozšířit tabulku dat související s sestavením přidáním dalších vlastností, které mají být trvalé a odebráním vlastností, aby nebyly trvalé.

 Chcete-li upravit data MSBuild, podtyp projektu je zodpovědný za načítání objektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>vlastnosti MSBuild ze systému základního projektu prostřednictvím . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>je rozhraní implementované v systému základního projektu a agregace dotazů podtypu projektu spuštěním `QueryInterface`.

 Následující postup popisuje kroky pro odebrání <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>vlastnosti pomocí .

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Odebrání vlastnosti ze souboru projektu MSBuild

1. Volání `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> podtypu projektu.

2. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> `pszPropName` s nastavenou na vlastnost, kterou chcete odebrat.

### <a name="persisting-non-build-related-information"></a>Trvalé informace související s nesestavením
 Trvalost dat v souborech projektu, které nezáleží na sestavení je zpracována prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.

 Můžete implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> na `project subtype aggregator` hlavní `project subtype project configuration` objekt, objekt nebo obojí.

 Následující body popisují hlavní pojmy týkající se trvalosti nebuild související informace.

- Základní projekt volá na hlavní projekt podtyp (to znamená, že nejvzdálenější projekt podtyp) agregátor objekt načíst a uložit data nezávislé na konfiguraci a volá na projekt podtyp projektu konfigurace objektů načíst nebo uložit data závislé na konfiguraci.

- Základní projekt volá metody <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> vícekrát pro každou úroveň agregace podtypu projektu a předá identifikátor GUID pro každou úroveň.

- Základní projekt předá nebo obdrží fragment XML, který je vyhrazen pro určitý podtyp projektu a používá tento mechanismus jako způsob trvalého stavu mezi úrovněmi agregace.

- Základní projekt volá provádění nejkrajnějšího <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>podtypu projektu, který je předává v identifikátoru GUID. Pokud identifikátor GUID patří k nejvzdálenějšímu podtypu projektu, zpracovává samotné volání; jinak deleguje volání vnitřního podtypu projektu a tak dále, dokud nebude nalezen podtyp projektu, kterému odpovídá identifikátor GUID.

- Podtyp projektu můžete také upravit fragment XML před nebo po delegování volání vnitřního podtypu projektu. Následující příklad ukazuje výňatek ze souboru projektu, kde je název souboru, který obsahuje vlastnosti specifické pro podtyp projektu, předán tomuto podtypu projektu.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Viz také
- [Podtypy projektů](../../extensibility/internals/project-subtypes.md)
