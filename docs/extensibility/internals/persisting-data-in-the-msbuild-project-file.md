---
title: Zachování dat v souboru projektu nástroje MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 324f9dfd4e381e9580e4940f06f652ef64d9d3ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132075"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Zachování dat v souboru projektu nástroje MSBuild
Podtyp projektu chtít zachovat data specifická pro dílčí do souboru projektu pro pozdější použití. Podtypem projektu používá trvalost soubor projektu do splňovat následující požadavky:  
  
1.  Zachovat data používá jako součást sestavení projektu. (Další informace o Microsoft Build Engine najdete v tématu [MSBuild](../../msbuild/msbuild.md).) Informace týkající se sestavení můžou buď:  
  
    1.  Nezávislé na konfigurační data. To znamená, že data uložená v MSBuild elementů s podmínkami, prázdný nebo nebyl nalezen.  
  
    2.  Data závislá na konfiguraci. To znamená, že data uložená v MSBuild prvky, které jsou pro konkrétní projekt konfiguraci záleží. Příklad:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Zachovat data, která se nevztahuje na sestavení. Tato data mohou být vyjádřeny v libovolném formátu XML, který není ověřený proti schématu XML.  
  
    1.  Nezávislé na konfigurační data.  
  
    2.  Data závislá na konfiguraci.  
  
## <a name="persisting-build-related-information"></a>Uložením informace týkající se sestavení  
 Trvalost dat užitečné pro sestavení projektu je prováděna pomocí nástroje MSBuild. Systém MSBuild uchovává hlavní tabulku informace týkající se sestavení. Projekt podtypů jsou zodpovědní za přístup k těmto datům k získání a nastavení hodnot vlastností. Projekt podtypů můžete také posílení tabulky dat souvisejících s sestavení přidáním další vlastnosti, které chcete nastavit jako trvalý a proto nejsou nastavené jako trvalé, a to odebráním vlastnosti.  
  
 Chcete-li upravit MSBuild data, podtypem projektu zodpovídá za načítání objektu vlastnosti nástroje MSBuild ze systému základní projektu prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> je rozhraní implementované v projektu systém jádra a totožný dílčí dotazy projektu pro něj spuštěním `QueryInterface`.  
  
 Následující postup popisuje kroky pro odebrání vlastnosti pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Pokud chcete odebrat ze souboru projektu nástroje MSBuild  
  
1.  Volání `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> podtypu projektu.  
  
2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> s `pszPropName` na vlastnost, kterou chcete odebrat.  
  
### <a name="persisting-non-build-related-information"></a>Zachování související informace bez sestavení  
 Trvalost dat v souborech projektu, který nezáleží na sestavení se zpracovává prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Můžete implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> v hlavním `project subtype aggregator` objekt, `project subtype project configuration` objektu, nebo obojí.  
  
 Následující body popisují hlavní koncepty týkající se trvalost bez sestavení související informace.  
  
-   Základní projekt volání na objekt hlavní projekt dílčí (tedy dílčí nejkrajnější projektu) agregátoru k načtení a uložení nezávislé konfigurační data, a volá na objekty projektu dílčí projektu konfigurace pro načtení nebo uložení konfigurace, které jsou závislé data.  
  
-   Základní projekt volá metody <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> více krát na jednotlivých úrovních agregace dílčí projektu a předá identifikátor GUID pro každou úroveň.  
  
-   Základní projekt předá nebo obdrží fragment XML, který je vyhrazený pro konkrétní projekt podtypem a používá tento mechanismus jako způsob zachování stavu mezi různými úrovněmi agregace.  
  
-   Základní projekt volá dílčí nejkrajnější projektu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementace předávání v identifikátor GUID. Pokud identifikátor GUID patří k podtypem nejkrajnější projektu, zpracovává volání sama o sobě; v opačném případě deleguje volání podtypem vnitřní projektu a tak dále, dokud nebude nalezen dílčí projektu, který odpovídá identifikátoru GUID.  
  
-   Podtyp projektu můžete také upravit XML fragment před nebo po deleguje volání podtypem vnitřní projektu. Následující příklad ukazuje výňatek ze souboru projektu, kde je název souboru obsahujícího vlastnosti, které jsou specifické pro projekt podtypem, předaný dílčí tohoto projektu.  
  
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
 [Podtypy projektů](../../extensibility/internals/project-subtypes.md)