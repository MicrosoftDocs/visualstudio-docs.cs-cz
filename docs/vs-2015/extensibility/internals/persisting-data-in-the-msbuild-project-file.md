---
title: Trvalá data v souboru projektu MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39d2ab449c3623a90dd76729b46a9f353900fc88
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704118"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Trvalá data v souboru projektu nástroje MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtyp projektu může být nutné pro pozdější použití uchovat data specifická pro konkrétní typ do souboru projektu. Podtyp projektu používá trvalost souborů projektu k splnění následujících požadavků:  
  
1. Trvalá data používaná jako součást sestavení projektu. (Další informace o Microsoft Build Engine najdete v tématu [MSBuild](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b).) Informace související s sestavením mohou:  
  
    1. Data nezávislá na konfiguraci. To znamená, že data uložená v prvcích MSBuild s prázdnými nebo chybějícími podmínkami.  
  
    2. Data závislá na konfiguraci. To znamená, že data uložená v prvcích MSBuild, která jsou podmíněně pro konkrétní konfiguraci projektu. Příklad:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2. Zachovat data, která nejsou relevantní pro sestavení. Tato data je možné vyjádřit v XML volném formátu, který není ověřený proti schématu XML.  
  
    1. Data nezávislá na konfiguraci.  
  
    2. Data závislá na konfiguraci.  
  
## <a name="persisting-build-related-information"></a>Uchování informací souvisejících s sestavením  
 Trvalá data užitečná pro sestavení projektu jsou zpracovávána prostřednictvím nástroje MSBuild. Systém MSBuild udržuje hlavní tabulku informací týkajících se sestavení. Podtypy projektu zodpovídají za přístup k těmto datům za účelem získání a nastavení hodnot vlastností. Podtypy projektů mohou také rozšířit tabulku dat související s sestavením přidáním dalších vlastností, které mají být zachovány, a odebráním vlastností, aby nebyly uchovány.  
  
 Pro úpravu dat MSBuild je podtype projektu zodpovědný za načtení objektu vlastnosti MSBuild ze základního projektového systému prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> je rozhraní implementované v základním projektovém systému a pro něj probíhá agregace dotazů podtypu projektu spuštěním `QueryInterface` .  
  
 Následující postup popisuje kroky pro odebrání vlastnosti pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> .  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Odebrání vlastnosti ze souboru projektu MSBuild  
  
1. Zavolejte `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> podtyp projektu.  
  
2. Volejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> s `pszPropName` parametrem nastaveným na vlastnost, kterou chcete odebrat.  
  
### <a name="persisting-non-build-related-information"></a>Zachování informací o nesouvisejícím sestavení  
 Trvalost dat v souborech projektu, které nezáleží na sestavení, je zpracováván prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> .  
  
 Můžete implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> na hlavní `project subtype aggregator` objekt, `project subtype project configuration` objekt nebo obojí.  
  
 Následující body popisují hlavní koncepty týkající se trvalosti nesouvisejících informací o sestavách.  
  
- Základní projekt volá na hlavní typ dílčího typu projektu (tj. objekt vnějšího podtypu projektu), který načte a uloží konfiguraci nezávislá data a volá na objekty konfigurace podtypu projektu pro načtení nebo uložení dat závislých na konfiguraci.  
  
- Základní projekt volá metody <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> vícenásobné pro každou úroveň agregace podtypu projektu a předá identifikátor GUID pro každou úroveň.  
  
- Základní projekt projde nebo obdrží fragment XML, který je vyhrazen pro konkrétní podtyp projektu a používá tento mechanismus jako způsob zachování stavu mezi úrovněmi agregace.  
  
- Základní projekt volá implementaci podtypu vnějšího projektu, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> která je procházející identifikátorem GUID. Pokud identifikátor GUID patří nadřazenému podtypu projektu, zpracovává samotné volání; v opačném případě deleguje volání typu vnitřního projektu a tak dále, dokud není nalezen podtyp projektu, na který odpovídá identifikátor GUID.  
  
- Podtyp projektu může také změnit fragment XML před nebo poté, co deleguje volání podtypu vnitřního projektu. Následující příklad ukazuje výňatk ze souboru projektu, kde je název souboru, který obsahuje vlastnosti specifické pro podtyp projektu, předán dílčímu typu projektu.  
  
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
