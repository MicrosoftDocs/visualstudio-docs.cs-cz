---
title: Standardní a vlastní konfigurace sady nástrojů | Microsoft Docs
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76596d752ae2e552088fff607142abb215e9147b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595069"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standardní a vlastní konfigurace sady nástrojů
Sada nástrojů MSBuild obsahuje odkazy na úlohy, cíle a nástroje, které můžete použít k sestavení projektu aplikace. Nástroj MSBuild obsahuje standardní sadu nástrojů, ale můžete také vytvořit vlastní sady nástrojů. Informace o tom, jak zadat sadu nástrojů, najdete v tématu [Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) .

## <a name="standard-toolset-configurations"></a>Standardní konfigurace sady nástrojů

::: moniker range=">=vs-2019"
 MSBuild 16,0 obsahuje následující standardní sady nástrojů:

|ToolsVersion|Cesta sady nástrojů (uvedená ve vlastnosti Build MSBuildToolsPath nebo MSBuildBinPath)|
|------------------| - |
|2.0|*\<cestu instalace Windows > \Microsoft.Net\Framework\v2.0.50727\\*|
|3.5|*\<cestu instalace Windows > \Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<cestu instalace Windows > \Microsoft.NET\Framework\v4.0.30319\\*|
|Aktuální|*\<cestu k instalaci sady Visual Studio > \MSBuild\Current\bin*|

 Hodnota `ToolsVersion` určuje, která sada nástrojů se používá v projektu generovaném sadou Visual Studio. V aplikaci Visual Studio 2019 je výchozí hodnota "Current" (bez ohledu na to, jakou verzi jste určili v souboru projektu), ale tento atribut lze přepsat pomocí přepínače **/ToolsVersion** na příkazovém řádku. Informace o tomto atributu a dalších způsobech určení `ToolsVersion`naleznete v tématu [přepising ToolsVersion Settings](../msbuild/overriding-toolsversion-settings.md).

 ::: moniker-end

::: moniker range="vs-2017"
 MSBuild 15,0 obsahuje následující standardní sady nástrojů:

|ToolsVersion|Cesta sady nástrojů (uvedená ve vlastnosti Build MSBuildToolsPath nebo MSBuildBinPath)|
|------------------| - |
|2.0|*\<cestu instalace Windows > \Microsoft.Net\Framework\v2.0.50727\\*|
|3.5|*\<cestu instalace Windows > \Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<cestu instalace Windows > \Microsoft.NET\Framework\v4.0.30319\\*|
|15,0|*\<cestu k instalaci sady Visual Studio > adresáři \msbuild\15.0\Bin*|

 Hodnota `ToolsVersion` určuje, která sada nástrojů se používá v projektu generovaném sadou Visual Studio. V aplikaci Visual Studio 2017 je výchozí hodnota "15,0" (bez ohledu na to, jakou verzi jste určili v souboru projektu), ale tento atribut lze přepsat pomocí přepínače **/ToolsVersion** na příkazovém řádku. Informace o tomto atributu a dalších způsobech určení `ToolsVersion`naleznete v tématu [přepising ToolsVersion Settings](../msbuild/overriding-toolsversion-settings.md).
 ::: moniker-end

Visual Studio 2017 a novější verze nepoužívají klíč registru pro cestu k nástroji MSBuild. Pro verze nástroje MSBuild starší než 15,0, které jsou nainstalovány se sadou Visual Studio 2017, následující klíče registru určují instalační cestu nástroje MSBuild. exe.

|Klíč registru|Název klíče|Hodnota klíč řetězce|
|------------------|--------------|----------------------|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2.0\\** |**MSBuildToolsPath**|**Cesta instalace .NET Framework 2,0**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\\** |**MSBuildToolsPath**|**Cesta instalace .NET Framework 3,5**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\\** |**MSBuildToolsPath**|**Instalační cesta .NET Framework 4**|

### <a name="sub-toolsets"></a>Dílčí sady nástrojů
 Pokud klíč registru v předchozí tabulce obsahuje podklíč, nástroj MSBuild ho použije k určení cesty dílčí sady nástrojů, která přepisuje cestu v nadřazené sadě nástrojů. Následující podklíč je příkladem:

 **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**

 Pokud jsou některé vlastnosti definované v základní sadě nástrojů i v vybrané dílčí sadě nástrojů, použijí se definice vlastností v dílčí sadě nástrojů. Například sada nástrojů MSBuild 4,0 definuje `SDK40ToolsPath`, aby odkazovala na sadu SDK 7.0, ale sada nástrojů MSBuild 4.0 \ 11.0 definuje stejnou vlastnost, která odkazuje na 8.0 A sadu SDK. Pokud `VisualStudioVersion` nenastavíte, `SDK40ToolsPath` by odkazoval na 7.0 A, ale pokud je `VisualStudioVersion` nastavená na 11,0, vlastnost místo toho bude ukazovat na 8.0 A.

 Vlastnost `VisualStudioVersion` Build určuje, zda bude dílčí sada nástrojů aktivní. Například hodnota `VisualStudioVersion` "12,0" Určuje dílčí sadu nástrojů MSBuild 12,0. Další informace naleznete v části sady [nástrojů sady nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)dílčích sad nástrojů.

> [!NOTE]
> Doporučujeme vyhnout se změnám těchto nastavení. Nicméně můžete přidat vlastní nastavení a definovat vlastní definice sady nástrojů v rámci počítače, jak je popsáno v další části.

## <a name="custom-toolset-definitions"></a>Vlastní definice sady nástrojů
 Pokud standardní sada nástrojů nesplňuje požadavky na sestavení, můžete vytvořit vlastní sadu nástrojů. Například můžete mít scénář testovacího prostředí, ve kterém musíte mít samostatný systém pro vytváření [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]ch projektů. Pomocí vlastní sady nástrojů můžete přiřadit k atributu `ToolsVersion` vlastní hodnoty při vytváření projektů nebo spuštění nástroje *MSBuild. exe*. Tímto způsobem můžete také použít vlastnost `$(MSBuildToolsPath)` k importu *. cíle* souborů z tohoto adresáře a také definování vlastních vlastností sady nástrojů, které lze použít pro libovolný projekt, který tuto sadu nástrojů používá.

 Zadejte vlastní sadu nástrojů v konfiguračním souboru pro *MSBuild. exe* (nebo pro vlastní nástroj, který hostuje modul MSBuild, pokud to je to, co používáte). Například konfigurační soubor pro nástroj *MSBuild. exe* může zahrnovat následující definici sady nástrojů, pokud chcete definovat sadu nástrojů s názvem *MyCustomToolset*.

```xml
<msbuildToolsets default="MyCustomToolset">
   <toolset toolsVersion="MyCustomToolset">
      <property name="MSBuildToolsPath"
        value="C:\SpecialPath" />
   </toolset>
</msbuildToolsets>
```

 v konfiguračním souboru musí být také definováno `<msbuildToolsets>`, a to následujícím způsobem.

```xml
<configSections>
   <section name="msbuildToolsets"
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,
       Microsoft.Build, Version=15.1.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a"
   </section>
</configSections>
```

> [!NOTE]
> Aby se správně četl, `<configSections>` musí být první pododdíl v části `<configuration>`.

 `ToolsetConfigurationSection` je vlastní konfigurační oddíl, který může být použit jakýmkoli hostitelem nástroje MSBuild pro vlastní konfiguraci. Použijete-li vlastní sadu nástrojů, hostitel nemusí provádět žádné akce k inicializaci modulu sestavení s výjimkou zadání položek konfiguračního souboru. Definováním položek v registru můžete určit sady nástrojů pro celý počítač, které se vztahují na *MSBuild. exe*, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]a všechny hostitele nástroje MSBuild.

> [!NOTE]
> Pokud konfigurační soubor definuje nastavení pro `ToolsVersion`, která již byla definována v registru, nejsou tyto dvě definice sloučeny. Definice v konfiguračním souboru má přednost a nastavení v registru pro tyto `ToolsVersion` jsou ignorována.

 Následující vlastnosti jsou specifické pro hodnotu `ToolsVersion`, která se používá v projektech:

- **$ (MSBuildBinPath)** je nastaveno na hodnotu `ToolsPath`, která je zadána buď v registru, nebo v konfiguračním souboru, kde je `ToolsVersion` definována. Nastavení `$(MSBuildToolsPath)` v registru nebo konfiguračního souboru určuje umístění základních úloh a cílů. V souboru projektu je tato vlastnost mapována na vlastnost $ (MSBuildBinPath) a také na vlastnost $ (MSBuildToolsPath).

- `$(MSBuildToolsPath)` je vyhrazená vlastnost, která je poskytována vlastností MSBuildToolsPath, která je zadána v konfiguračním souboru. (Tato vlastnost nahrazuje `$(MSBuildBinPath)`. Kvůli kompatibilitě se ale přenese `$(MSBuildBinPath)`.) Vlastní sada nástrojů musí definovat buď `$(MSBuildToolsPath)`, nebo `$(MSBuildBinPath)`, ale ne obojí, pokud obě nemají stejnou hodnotu.

  Do konfiguračního souboru můžete také přidat vlastní vlastnosti specifické pro ToolsVersion pomocí stejné syntaxe, kterou použijete k přidání vlastnosti MSBuildToolsPath. Chcete-li zpřístupnit tyto vlastní vlastnosti souboru projektu, použijte stejný název jako název hodnoty, která je zadána v konfiguračním souboru. V konfiguračním souboru lze definovat sady nástrojů, ale ne podsady nástrojů.

## <a name="see-also"></a>Viz také:
- [Sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
