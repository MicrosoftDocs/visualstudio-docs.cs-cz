---
title: 'Postupy: použití proměnných prostředí v sestavení | Dokumentace Microsoftu'
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
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 463acc185a73b9a483bf74c98d4bde1cf0f42494
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877501"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Postupy: Použití proměnných prostředí v sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Při sestavování projektů, je často nutné nastavit možnosti sestavení pomocí informací, které nejsou v souboru projektu nebo soubory, které tvoří vašeho projektu. Tyto informace jsou obvykle uložená v proměnné prostředí.  
  
## <a name="referencing-environment-variables"></a>Odkazuje na proměnné prostředí  
 Všechny proměnné prostředí jsou k dispozici na [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) projektu soubor jako vlastnosti.  
  
> [!NOTE]
>  Pokud soubor projektu obsahuje explicitní definice vlastnosti, která má stejný název jako proměnné prostředí, přepíše vlastnost v souboru projektu hodnotu proměnné prostředí.  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Chcete-li použít proměnné prostředí v projektu nástroje MSBuild  
  
- Odkazujte na proměnné prostředí stejným způsobem, jako byste to udělali proměnné deklarované v souboru projektu. Například následující kód odkazuje na proměnnou prostředí BIN_PATH:  
  
   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
  Můžete použít `Condition` atribut poskytnout výchozí hodnotu pro vlastnost, pokud nebyla nastavena proměnná prostředí.  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>Chcete-li zadat výchozí hodnotu pro vlastnost  
  
-   Použití `Condition` atribut u vlastnosti a nastavte vlastnost na hodnotu pouze tehdy, pokud nemá žádnou hodnotu. Například následující kód nastaví `ToolsPath` vlastnost c:\tools pouze tehdy, pokud `ToolsPath` není nastavena proměnná prostředí:  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  Názvy vlastností nejsou malá a velká písmena tak obě `$(ToolsPath)` a `$(TOOLSPATH)` odkazovat na stejnou vlastnost nebo prostředí proměnnou.  
  
## <a name="example"></a>Příklad  
 Následující soubor projektu používá proměnné prostředí a zadejte umístění adresáře.  
  
```  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  

[MSBuild](msbuild.md)

[Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties1.md)

[Postupy: Sestavení stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md)


