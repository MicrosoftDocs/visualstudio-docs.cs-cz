---
title: Trvalá Data v souboru projektu nástroje MSBuild | Dokumentace Microsoftu
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
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 059ddc7b9b8fe0de06530af704bb5f7e271f6744
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749642"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Trvalá data v souboru projektu nástroje MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtyp projektu může být nutné zachovat data specifická pro podtyp do souboru projektu pro pozdější použití. Podtyp projektu používá trvalost souborů projektu pro splnění následujících požadavků:  
  
1.  Zachovat data použít při vytváření projektu. (Další informace o procesu Microsoft Build Engine, naleznete v tématu [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b).) Informace týkající se sestavení můžou buď:  
  
    1.  Nezávislé na konfigurační data. To znamená, že data uložená v MSBuild prvky s podmínkami, prázdný nebo chybí.  
  
    2.  Data závislá na konfiguraci. To znamená, že data uložená v MSBuild prvky, které jsou pro konkrétní projekt konfiguraci záleží. Příklad:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Zachovat data, která nejsou relevantní pro sestavení. Tato data mohou být vyjádřeny v volného tvaru XML, který není ověřený proti schématu XML.  
  
    1.  Nezávislé na konfigurační data.  
  
    2.  Data závislá na konfiguraci.  
  
## <a name="persisting-build-related-information"></a>Trvalé informace související s buildem  
 Trvalost dat užitečné při sestavování projektu probíhá prostřednictvím funkce MSBuild. Systém MSBuild udržuje hlavní tabulku informace týkající se sestavení. Podtypy projektů jsou zodpovědné za přístup k těmto datům získat a nastavit hodnoty vlastností. Podtypy projektů můžete také rozšířit tabulky související s buildem dat tak, že přidáte další vlastnosti chcete nastavit jako trvalý a to odebráním vlastnosti, nejsou trvalé.  
  
 Upravit MSBuild data, podtyp projektu zodpovídá za načítání objektu vlastnosti MSBuild ze systému základního projektu prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> je rozhraní implementované v systému projektu jádra a agregačních dotazů podtyp projektu pro něj spuštěním `QueryInterface`.  
  
 Následující postup popisuje kroky pro odebrání vlastnosti pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Odebrání vlastnosti ze souboru projektu MSBuild  
  
1.  Volání `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> podtypu projektu.  
  
2.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> s `pszPropName` na vlastnost, kterou chcete odebrat.  
  
### <a name="persisting-non-build-related-information"></a>Související informace o zachování bez sestavení  
 Trvalost dat v souborech projektu, který není důležitá pro sestavení probíhá prostřednictvím funkce <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Můžete implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> v hlavním `project subtype aggregator` objektu, `project subtype project configuration` objektu, nebo obojí.  
  
 Následující body popisují hlavní koncepty týkající se trvalého související informace mimo sestavení.  
  
-   Základní projekt volá na objekt hlavního projektu podtyp (to znamená, podtyp projektu vnějšího) agregátoru načítají a ukládají data konfigurace nezávislé a volá na objekty konfigurace projektu podtyp projektu k načtení nebo uložení závislé na konfiguraci data.  
  
-   Základní projekt volá metody <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> více na jednotlivých úrovních agregace podtyp projektu a předá identifikátor GUID pro každou úroveň.  
  
-   Základní projekt předá nebo přijímá fragment XML, který je vyhrazen pro konkrétní projekt podtyp a používá tento mechanismus jako způsob uchování stavu mezi úrovních agregace.  
  
-   Základní projekt volá podtyp projektu nejkrajnější <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementace předávajícího identifikátor GUID. Pokud identifikátor GUID vlastníky podtyp nejkrajnější projektu, zpracovává volání sebe sama; v opačném případě deleguje volání do vnitřní projektu podtyp a tak dále, dokud nebude nalezen podtyp projektu, který odpovídá identifikátoru GUID.  
  
-   Podtyp projektu můžete také upravit XML fragment před nebo po deleguje volání vnitřní projektu podtyp. Následující příklad ukazuje výňatek ze souboru projektu, kde je název souboru, který obsahuje vlastnosti specifické pro projekt podtypem, předat této podtyp projektu.  
  
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

