---
title: Standardní a vlastní konfigurace sady nástrojů | Dokumentace Microsoftu
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
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a1d57903ec2a8c3afb439f27433898467028eb6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906699"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standardní a vlastní konfigurace sady nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Sada nástrojů MSBuild obsahuje odkazy na úkoly, cíle a nástroje, které můžete použít k sestavení projektu aplikace. Nástroj MSBuild obsahuje standardní sadu nástrojů, ale můžete také vytvořit vlastní sady nástrojů. Informace o tom, jak určit sadu nástrojů najdete v tématu [sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)  

## <a name="standard-toolset-configurations"></a>Konfigurace standardní sady nástrojů  
 Nástroj MSBuild 12.0 zahrnuje následující standardní sady nástrojů:  


| Atribut ToolsVersion | Cesta nástrojů (jak je uvedeno ve vlastnosti sestavení MSBuildToolsPath nebo MSBuildBinPath) |
|--------------|--------------------------------------------------------------------------------------|
|     2.0      |           *Instalační cesta Windows*\Microsoft.Net\Framework\v2.0.50727\            |
|     3.5      |              *Instalační cesta Windows*\Microsoft.NET\Framework\v3.5\               |
|     4.0      |           *Instalační cesta Windows*\Microsoft.NET\Framework\v4.0.30319\            |
|     12.0     |                          *%ProgramFiles%* \MSBuild\12.0\bin                           |

 `ToolsVersion` Hodnota určuje, které používají sady nástrojů projektu, který generuje sada Visual Studio. V [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] výchozí hodnota je "12.0" (nezáleží na tom, jaké verze zadaná v souboru projektu), ale tento atribut lze přepsat pomocí **/toolsversion** přepínač příkazového řádku. Informace o tento atribut a další způsoby, jak určit `ToolsVersion`, naleznete v tématu [přepsání nastavení ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  

 Pokud `ToolsVersion` není zadán, klíče registru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\\< číslo verze\>\DefaultToolsVersion** definuje `ToolsVersion`, což je vždy 2.0.  

 Následující klíče registru zadejte instalační cestu nástroje MSBuild.exe.  

|Klíč registru|Název klíče|Řetězcovou hodnotu klíče|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0\|MSBuildToolsPath|Cesta pro instalaci rozhraní .NET framework 2.0|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\|MSBuildToolsPath|Cesta pro instalaci rozhraní .NET framework 3.5|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\|MSBuildToolsPath|Cesta pro instalaci rozhraní .NET framework 4|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\12.0\|MSBuildToolsPath|Cesta pro instalaci nástroje MSBuild|  

### <a name="sub-toolsets"></a>Dílčí sady nástrojů  
 Pokud klíč registru v předchozí tabulce obsahuje podklíč, MSBuild na základě toho určí, že cesta k dílčí může přepsání cesty v nadřazené sady nástrojů. Následující podklíč je příklad:  

 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  

 Pokud všechny vlastnosti jsou definovány v základní sadu nástrojů a vybraný dílčí, použijí se definice vlastností v na dílčí sadu nástrojů. Například sada nástrojů MSBuild 4.0 definuje `SDK40ToolsPath` přejděte 7.0a na sadu SDK, ale MSBuild 4.0\11.0 definuje sadu nástrojů stejnou vlastnost tak, aby odkazoval 8.0a SDK. Pokud `VisualStudioVersion` není nastavena, `SDK40ToolsPath` by odkazovat na 7.0a, ale pokud `VisualStudioVersion` je nastavena na 11.0, vlastnost by místo toho přejděte na 8.0a.  

 `VisualStudioVersion` Vlastnost sestavení určuje, zda dílčí stane aktivním. Například `VisualStudioVersion` hodnota "12.0" Určuje dílčí nástroj MSBuild 12.0. Další informace najdete v části dílčí sady nástrojů v [sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  

> [!NOTE]
>  Doporučujeme vám, že byste se vyhnout změnou tohoto nastavení. Můžete však přidat vlastní nastavení a definici vlastních nástrojů pro celý počítač, podle popisu v následující části.  

## <a name="custom-toolset-definitions"></a>Definice vlastní sady nástrojů  
 Když standardní sadu nástrojů nesplňuje vaše požadavky na sestavení, můžete vytvořit vlastní sadu nástrojů. Například může mít scénáři sestavení testovacího prostředí, ve kterém musí mít samostatný systém pro vytváření [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projekty. Pomocí vlastních nástrojů můžete přiřadit vlastní hodnoty a `ToolsVersion` atribut při vytváření projektů nebo spustit MSBuild.exe. Tímto způsobem můžete také použít `$(MSBuildToolsPath)` vlastnost k importu souborů TARGETS z tohoto adresáře, stejně jako definovat vlastní vlastnosti vlastní sady nástrojů, které lze použít pro libovolný projekt, který používá tuto sadu nástrojů.  

 Zadejte vlastní sady nástrojů v konfiguračním souboru pro MSBuild.exe (nebo pro vlastní nástroj, který je hostitelem stroji MSBuild engine, pokud je to, co používáte). Konfigurační soubor MSBuild.exe může obsahovat třeba následující definici sady nástrojů, pokud jste si přáli přepsat výchozí chování ToolsVersion 12.0.  

```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  

 `<msbuildToolsets>` musí také být definovaná v konfiguračním souboru následujícím způsobem.  

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
>  Čtení správně, `<configSections>` musí být první část v `<configuration>` oddílu.  

 `ToolsetConfigurationSection` je vlastního konfiguračního oddílu, který lze použít libovolný hostitel MSBuild pro vlastní konfiguraci. Pokud používáte vlastní sady nástrojů, není nutné dělat nic se inicializovat modul sestavení s tím rozdílem, poskytuje konfiguraci položek souboru hostitele. Definováním položky registru, můžete určit sady nástrojů celý počítač, který se použije MSBuild.exe [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]a všechny hostitele nástroje MSBuild.  

> [!NOTE]
>  Pokud konfigurační soubor definuje nastavení pro `ToolsVersion` , který již byl definován v registru, nejsou sloučené dvě definice. Definice v konfiguračním souboru má přednost a nastavení v registru pro daný `ToolsVersion` jsou ignorovány.  

 Následující vlastnosti jsou specifické pro hodnotu `ToolsVersion` , který je používat v projektech:  

- **$(MSBuildBinPath)** je nastavena na `ToolsPath` hodnotu, která je zadán v registru nebo v konfiguračním souboru kde `ToolsVersion` je definována. `$(MSBuildToolsPath)` Nastavení v registru nebo konfiguračního souboru Určuje umístění základní úlohy a cíle. V souboru projektu to mapuje na vlastnost $(MSBuildBinPath) a také $(MSBuildToolsPath) vlastnosti.  

- `$(MSBuildToolsPath)` je rezervované vlastnosti, který poskytl MSBuildToolsPath vlastnost, která je určena v konfiguračním souboru. (Tato vlastnost nahradí `$(MSBuildBinPath)`. Nicméně `$(MSBuildBinPath)` je přenesena z důvodu kompatibility.) Vlastní sada nástrojů musí definovat buď `$(MSBuildToolsPath)` nebo `$(MSBuildBinPath)` ale nikoli oba současně, pokud obě mají stejnou hodnotu.  

  Můžete také přidat vlastní vlastnosti specifické pro danou hodnotu ToolsVersion do konfiguračního souboru pomocí stejné syntaxe, který použijete k přidání vlastnosti MSBuildToolsPath. Chcete-li zpřístupnit tyto vlastních vlastností do souboru projektu, použijte stejný název jako název hodnoty zadané v konfiguračním souboru. V konfiguračním souboru může definovat sady nástrojů, ale ne sub-sady nástrojů.  

## <a name="see-also"></a>Viz také  
 [Sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)



