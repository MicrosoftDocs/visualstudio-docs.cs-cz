---
title: Standardní a vlastní konfigurace sady nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d08a7eb20c01568b3501f16348eb19afdcaefa2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802631"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standardní a vlastní konfigurace sady nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sada nástrojů MSBuild obsahuje odkazy na úlohy, cíle a nástroje, které můžete použít k sestavení projektu aplikace. Nástroj MSBuild obsahuje standardní sadu nástrojů, ale můžete také vytvořit vlastní sady nástrojů. Informace o tom, jak zadat sadu nástrojů, najdete v tématu [Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) .  

## <a name="standard-toolset-configurations"></a>Standardní konfigurace sady nástrojů  
 MSBuild 12,0 obsahuje následující standardní sady nástrojů:  

| ToolsVersion | Cesta sady nástrojů (uvedená ve vlastnosti Build MSBuildToolsPath nebo MSBuildBinPath) |
|--------------|--------------------------------------------------------------------------------------|
|     2,0      |           *Instalační cesta systému Windows*\Microsoft.NET\Framework\v2.0.50727\            |
|     3,5      |              *Instalační cesta systému Windows*\Microsoft.Net\Framework\v3.5\               |
|     4,0      |           *Instalační cesta systému Windows*\Microsoft.NET\Framework\v4.0.30319\            |
|     12.0     |                          *% ProgramFiles%* \MSBuild\12.0\Bin                           |

 `ToolsVersion`Hodnota určuje, která sada nástrojů se používá v projektu generovaném sadou Visual Studio. [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]Výchozí hodnota je "12,0" (bez ohledu na to, jakou verzi jste určili v souboru projektu), ale tento atribut můžete přepsat pomocí přepínače **/ToolsVersion** na příkazovém řádku. Informace o tomto atributu a dalších způsobech, jak určit `ToolsVersion` , naleznete v tématu [Přepising ToolsVersion Settings](../msbuild/overriding-toolsversion-settings.md).  

 Pokud `ToolsVersion` není zadaný, klíč registru **HKEY_LOCAL_MACHINE \Software\microsoft\msbuild \\<číslo verze \> \DefaultToolsVersion** definuje `ToolsVersion` , což je vždycky 2,0.  

 Následující klíče registru určují instalační cestu MSBuild.exe.  

|Klíč registru|Název klíče|Hodnota klíč řetězce|  
|------------------|--------------|----------------------|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0 \| MSBuildToolsPath|Cesta instalace .NET Framework 2,0|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5 \| MSBuildToolsPath|Cesta instalace .NET Framework 3,5|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0 \| MSBuildToolsPath|Instalační cesta .NET Framework 4|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ MSBuild\ToolsVersions\12.0 \| MSBuildToolsPath|Instalační cesta nástroje MSBuild|  

### <a name="sub-toolsets"></a>Dílčí sady nástrojů  
 Pokud klíč registru v předchozí tabulce obsahuje podklíč, nástroj MSBuild ho použije k určení cesty dílčí sady nástrojů, která může přepsat cestu v nadřazené sadě nástrojů. Následující podklíč je příkladem:  

 \ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  

 Pokud jsou některé vlastnosti definované v základní sadě nástrojů i v vybrané dílčí sadě nástrojů, použijí se definice vlastností v dílčí sadě nástrojů. Například sada nástrojů MSBuild 4,0 definuje `SDK40ToolsPath` , aby odkazovala na sadu SDK 7.0, ale sada nástrojů MSBuild 4.0 \ 11.0 definuje stejnou vlastnost, která odkazuje na 8.0 a sadu SDK. Pokud `VisualStudioVersion` je parametr nastaven na hodnotu, tak `SDK40ToolsPath` by odkazoval na 7,0 a, ale pokud `VisualStudioVersion` je nastaven na 11,0, vlastnost místo toho bude ukazovat na 8.0 a.  

 `VisualStudioVersion`Vlastnost Build určuje, zda bude dílčí sada nástrojů aktivní. Například `VisualStudioVersion` hodnota "12,0" Určuje dílčí sadu nástrojů MSBuild 12,0. Další informace naleznete v části sady [nástrojů sady nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)dílčích sad nástrojů.  

> [!NOTE]
> Doporučujeme vyhnout se změnám těchto nastavení. Nicméně můžete přidat vlastní nastavení a definovat vlastní definice sady nástrojů v rámci počítače, jak je popsáno v další části.  

## <a name="custom-toolset-definitions"></a>Vlastní definice sady nástrojů  
 Pokud standardní sada nástrojů nesplňuje požadavky na sestavení, můžete vytvořit vlastní sadu nástrojů. Například můžete mít scénář testovacího prostředí, ve kterém musíte mít samostatný systém pro vytváření [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektů. Pomocí vlastní sady nástrojů můžete přiřadit k atributu vlastní hodnoty `ToolsVersion` při vytváření projektů nebo spuštění MSBuild.exe. Tímto způsobem můžete také použít `$(MSBuildToolsPath)` vlastnost pro import souborů. targets z tohoto adresáře a definovat vlastní vlastnosti sady nástrojů, které lze použít pro libovolný projekt, který tuto sadu nástrojů používá.  

 Zadejte vlastní sadu nástrojů v konfiguračním souboru pro MSBuild.exe (nebo pro vlastní nástroj, který hostuje modul MSBuild, pokud to je to, co používáte). Konfigurační soubor pro MSBuild.exe může například zahrnovat následující definici sady nástrojů, pokud chcete přepsat výchozí chování ToolsVersion 12,0.  

```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  

 `<msbuildToolsets>` musí být také definováno v konfiguračním souboru následujícím způsobem.  

```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  

> [!NOTE]
> Aby bylo možné je přečíst správně, `<configSections>` musí se jednat o první pododdíl v `<configuration>` části.  

 `ToolsetConfigurationSection` je vlastní konfigurační oddíl, který může být použit jakýmkoli hostitelem nástroje MSBuild pro vlastní konfiguraci. Použijete-li vlastní sadu nástrojů, hostitel nemusí provádět žádné akce k inicializaci modulu sestavení s výjimkou zadání položek konfiguračního souboru. Definováním položek v registru můžete určit sady nástrojů pro celý počítač, které se vztahují na MSBuild.exe, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a všechny hostitele nástroje MSBuild.  

> [!NOTE]
> Pokud konfigurační soubor definuje nastavení pro `ToolsVersion` , která byla již definována v registru, tyto dvě definice nejsou sloučeny. Definice v konfiguračním souboru má přednost a nastavení v registru pro, která `ToolsVersion` se mají ignorovat, se ignorují.  

 Následující vlastnosti jsou specifické pro hodnotu `ToolsVersion` , která se používá v projektech:  

- **$ (MSBuildBinPath)** je nastaveno na `ToolsPath` hodnotu, která je zadána buď v registru, nebo v konfiguračním souboru, kde `ToolsVersion` je definován. `$(MSBuildToolsPath)`Nastavení v registru nebo konfiguračního souboru určuje umístění základních úloh a cílů. V souboru projektu je tato vlastnost mapována na vlastnost $ (MSBuildBinPath) a také na vlastnost $ (MSBuildToolsPath).  

- `$(MSBuildToolsPath)` je vyhrazená vlastnost, která je poskytnuta vlastností MSBuildToolsPath, která je zadána v konfiguračním souboru. (Tato vlastnost nahrazuje `$(MSBuildBinPath)` . Nicméně `$(MSBuildBinPath)` se přenese z důvodu kompatibility.) Vlastní sada nástrojů musí definovat buď `$(MSBuildToolsPath)` nebo `$(MSBuildBinPath)` , ale ne obojí, pokud nemají stejnou hodnotu.  

  Do konfiguračního souboru můžete také přidat vlastní vlastnosti specifické pro ToolsVersion pomocí stejné syntaxe, kterou použijete k přidání vlastnosti MSBuildToolsPath. Chcete-li zpřístupnit tyto vlastní vlastnosti souboru projektu, použijte stejný název jako název hodnoty, která je zadána v konfiguračním souboru. V konfiguračním souboru lze definovat sady nástrojů, ale ne podsady nástrojů.  

## <a name="see-also"></a>Viz také  
 [Sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
