---
title: Standardní a vlastní konfigurace sady nástrojů | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: fef5a84285afdaa429606937f3e537863b060ec8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632158"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standardní a vlastní konfigurace sady nástrojů

Sada nástrojů MSBuild obsahuje odkazy na úkoly, cíle a nástroje, které můžete použít k vytvoření projektu aplikace. MSBuild obsahuje standardní sadu nástrojů, ale můžete také vytvořit vlastní sady nástrojů. Informace o tom, jak určit sadu nástrojů, naleznete v [tématu Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)

## <a name="standard-toolset-configurations"></a>Standardní konfigurace sady nástrojů

::: moniker range=">=vs-2019"
 MSBuild 16.0 obsahuje následující standardní sady nástrojů:

|ToolsVersion|Cesta sady nástrojů (jak je uvedeno ve vlastnosti sestavení MSBuildToolsPath nebo MSBuildBinPath)|
|------------------| - |
|2.0|*\<Cesta k instalaci systému Windows>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Cesta k instalaci systému Windows>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Cesta k instalaci systému Windows>\Microsoft.NET\Framework\v4.0.30319\\*|
|Current|*\<Instalační cesta sady Visual Studio>\MSBuild\Current\Bin*|

 Hodnota `ToolsVersion` určuje, která sada nástrojů je používána projektem, který generuje visual studio. V sadě Visual Studio 2019 je výchozí hodnota "Aktuální" (bez ohledu na verzi zadanou v souboru projektu), ale můžete přepsat tento atribut pomocí **přepínače /toolsversion** na příkazovém řádku. Informace o tomto atributu a `ToolsVersion`další způsoby určení , naleznete v tématu [Overriding ToolsVersion settings](../msbuild/overriding-toolsversion-settings.md).

 ::: moniker-end

::: moniker range="vs-2017"
 MSBuild 15.0 obsahuje následující standardní sady nástrojů:

|ToolsVersion|Cesta sady nástrojů (jak je uvedeno ve vlastnosti sestavení MSBuildToolsPath nebo MSBuildBinPath)|
|------------------| - |
|2.0|*\<Cesta k instalaci systému Windows>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Cesta k instalaci systému Windows>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Cesta k instalaci systému Windows>\Microsoft.NET\Framework\v4.0.30319\\*|
|15.0|*\<Instalační cesta sady Visual Studio>\MSBuild\15.0\bin*|

 Hodnota `ToolsVersion` určuje, která sada nástrojů je používána projektem, který generuje visual studio. V sadě Visual Studio 2017 je výchozí hodnota "15.0" (bez ohledu na verzi zadanou v souboru projektu), ale můžete přepsat tento atribut pomocí **přepínače /toolsversion** na příkazovém řádku. Informace o tomto atributu a `ToolsVersion`další způsoby určení , naleznete v tématu [Overriding ToolsVersion settings](../msbuild/overriding-toolsversion-settings.md).
 ::: moniker-end

Visual Studio 2017 a novější verze nepoužívají klíč registru pro cestu k MSBuild. Pro verze MSBuild před 15.0, které jsou nainstalovány s Visual Studio 2017, následující klíče registru určit instalační cestu MSBuild.exe.

|Klíč registru|Název klíče|Hodnota klíče řetězce|
|------------------|--------------|----------------------|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2.0\\** |**MSBuildToolsPath**|**Instalační cesta rozhraní .NET Framework 2.0**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\\** |**MSBuildToolsPath**|**Instalační cesta rozhraní .NET Framework 3.5**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\\** |**MSBuildToolsPath**|**Instalační cesta rozhraní .NET Framework 4**|

### <a name="sub-toolsets"></a>Podsady nástrojů

 Pokud klíč registru v předchozí tabulce obsahuje podklíč, msbuild jej používá k určení cesty k podsadě nástrojů, která přepíše cestu v nadřazené sadě nástrojů. Následující podklíč je příklad:

 **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**

 Pokud jsou v základní sadě nástrojů i ve vybrané podsadě nástrojů definovány nějaké vlastnosti, použijí se definice vlastností v podsadě nástrojů. Například sada nástrojů MSBuild 4.0 `SDK40ToolsPath` definuje tak, aby ukazovala na sadu SDK 7.0A, ale sada nástrojů MSBuild 4.0\11.0 definuje stejnou vlastnost tak, aby ukazovala na sadu 8.0A SDK. Pokud `VisualStudioVersion` je unset, `SDK40ToolsPath` by přejděte na `VisualStudioVersion` 7.0A, ale pokud je nastavena na 11,0, vlastnost by místo toho přejděte na 8.0A.

 Vlastnost `VisualStudioVersion` sestavení označuje, zda se podsada nástrojů stane aktivní. Například `VisualStudioVersion` hodnota "12.0" určuje podsadu nástrojů MSBuild 12.0. Další informace naleznete v části Podsady nástrojů [sady nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

> [!NOTE]
> Doporučujeme, abyste se vyhnuli změně těchto nastavení. Nicméně můžete přidat vlastní nastavení a definovat vlastní definice sady nástrojů pro celý počítač, jak popisuje další část.

## <a name="custom-toolset-definitions"></a>Definice vlastní sady nástrojů

 Pokud standardní sada nástrojů nesplňuje vaše požadavky na sestavení, můžete vytvořit vlastní sadu nástrojů. Například můžete mít scénář testovacího prostředí sestavení, ve kterém musíte mít samostatný systém pro vytváření projektů jazyka C++. Pomocí vlastní sady nástrojů můžete přiřadit vlastní `ToolsVersion` hodnoty atributu při vytváření projektů nebo spuštění *nástroje MSBuild.exe*. Tímto způsobem můžete také `$(MSBuildToolsPath)` použít vlastnost k importu souborů *.targets* z tohoto adresáře a také k definování vlastních vlastností sady nástrojů, které lze použít pro jakýkoli projekt, který tuto sadu nástrojů používá.

 Zadejte vlastní sadu nástrojů v konfiguračním souboru pro *nástroj MSBuild.exe* (nebo pro vlastní nástroj, který hostuje modul MSBuild, pokud je to, co používáte). Například konfigurační soubor pro *nástroj MSBuild.exe* může obsahovat následující definici sady nástrojů, pokud chcete definovat sadu nástrojů s názvem *MyCustomToolset*.

```xml
<msbuildToolsets default="MyCustomToolset">
   <toolset toolsVersion="MyCustomToolset">
      <property name="MSBuildToolsPath"
        value="C:\SpecialPath" />
   </toolset>
</msbuildToolsets>
```

 `<msbuildToolsets>`musí být také definovány v konfiguračním souboru, a to následovně.

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
> Chcete-li být `<configSections>` správně přečteni, musí `<configuration>` být první podsekce v sekci.

 `ToolsetConfigurationSection`je vlastní konfigurační oddíl, který může použít libovolný hostitel MSBuild pro vlastní konfiguraci. Pokud používáte vlastní sadu nástrojů, hostitel nemusí dělat nic k inicializaci modulu sestavení s výjimkou poskytnutí položek konfiguračního souboru. Definováním položek v registru můžete určit sady nástrojů pro celý počítač, které se vztahují k nástroji *MSBuild.exe*, Visual Studio a všem hostitelům nástroje MSBuild.

> [!NOTE]
> Pokud konfigurační soubor `ToolsVersion` definuje nastavení pro, který již byl definován v registru, dvě definice nejsou sloučeny. Definice v konfiguračním souboru má přednost `ToolsVersion` a nastavení v registru, které jsou ignorovány.

 Následující vlastnosti jsou specifické `ToolsVersion` pro hodnotu, která se používá v projektech:

- **$(MSBuildBinPath)** je nastavena na hodnotu, `ToolsPath` která je zadána `ToolsVersion` v registru nebo v konfiguračním souboru, kde je definován. Nastavení `$(MSBuildToolsPath)` v registru nebo konfiguračním souboru určuje umístění základních úloh a cílů. V souboru projektu se tento mapuje na vlastnost $(MSBuildBinPath) a také na vlastnost $(MSBuildToolsPath).

- `$(MSBuildToolsPath)`je vyhrazená vlastnost, která je dodávána vlastností MSBuildToolsPath, která je zadána v konfiguračním souboru. (Tato vlastnost `$(MSBuildBinPath)`nahrazuje . Nicméně, `$(MSBuildBinPath)` se přenáší do dalšího pro kompatibilitu.) Vlastní sada nástrojů musí `$(MSBuildToolsPath)` `$(MSBuildBinPath)` definovat buď nebo ne obojí, pokud oba mají stejnou hodnotu.

  Můžete také přidat vlastní vlastnosti Specifické pro ToolsVersion do konfiguračního souboru pomocí stejné syntaxe, kterou použijete k přidání vlastnosti MSBuildToolsPath. Chcete-li zpřístupnit tyto vlastní vlastnosti pro soubor projektu, použijte stejný název jako název hodnoty, která je zadána v konfiguračním souboru. V konfiguračním souboru můžete definovat sady nástrojů, ale ne dílčí sady nástrojů.

## <a name="see-also"></a>Viz také

- [Sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
