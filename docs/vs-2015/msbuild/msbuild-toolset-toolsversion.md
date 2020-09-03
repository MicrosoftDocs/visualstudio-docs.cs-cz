---
title: Sada nástrojů MSBuild (ToolsVersion) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf22fdf3d0cd9196794aa3929e9952f57bbfa2f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68872001"
---
# <a name="msbuild-toolset-toolsversion"></a>Sada nástrojů MSBuild (atribut ToolsVersion)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj MSBuild používá sadu nástrojů úkolů, cílů a nástrojů k sestavení aplikace. Sada nástrojů MSBuild obsahuje obvykle soubor Microsoft. Common. Tasks, soubor Microsoft. Common. targets a kompilátory, jako je například csc.exe a vbc.exe. Většinu sad nástrojů lze použít ke kompilaci aplikací na více než jednu verzi .NET Framework a více než jedné systémové platformě. Sada nástrojů MSBuild 2,0 se ale dá použít jenom k cílení na .NET Framework 2,0.

## <a name="toolsversion-attribute"></a>ToolsVersion – atribut
 Zadejte sadu nástrojů v `ToolsVersion` atributu prvku [projektu](../msbuild/project-element-msbuild.md) v souboru projektu. Následující příklad určuje, že projekt by měl být sestaven pomocí sady nástrojů MSBuild 12,0.

```
<Project ToolsVersion="12.0" ... </Project>
```

## <a name="how-the-toolsversion-attribute-works"></a>Princip fungování atributu ToolsVersion
 Při vytváření projektu v aplikaci Visual Studio nebo upgradu existujícího projektu je atribut s názvem `ToolsVersion` automaticky zahrnut do souboru projektu a jeho hodnota odpovídá verzi nástroje MSBuild, která je součástí edice sady Visual Studio. Další informace najdete v tématu [cílení na konkrétní verzi .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

 Je-li `ToolsVersion` v souboru projektu definována hodnota, nástroj MSBuild používá tuto hodnotu k určení hodnot vlastností sady nástrojů, které jsou k dispozici pro projekt. Jedna vlastnost sady nástrojů je `$(MSBuildToolsPath)` , která určuje cestu .NET Frameworkch nástrojů. Je požadována pouze tato vlastnost sady nástrojů (nebo `$(MSBuildBinPath)` ).

 Počínaje Visual Studio 2013 je verze sady nástrojů MSBuild stejná jako číslo verze sady Visual Studio. Nástroj MSBuild je výchozím nastavením této sady nástrojů v sadě Visual Studio a na příkazovém řádku bez ohledu na verzi sady nástrojů zadanou v souboru projektu.  Toto chování lze přepsat pomocí příznaku/ToolsVersion. Další informace najdete v tématu [přepsání nastavení ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 V následujícím příkladu nástroj MSBuild nalezne soubor Microsoft. CSharp. targets pomocí `MSBuildToolsPath` rezervované vlastnosti.

```
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Můžete upravit hodnotu `MSBuildToolsPath` definováním vlastní sady nástrojů. Další informace najdete v tématu [standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md) .

 Když na příkazovém řádku sestavíte řešení a určíte `ToolsVersion` pro msbuild.exe, všechny projekty a jejich závislosti typu projekt-projekt jsou sestaveny podle toho `ToolsVersion` , i když každý projekt v řešení určí svou vlastní `ToolsVersion` . Chcete-li definovat `ToolsVersion` hodnotu na základě jednotlivých projektů, přečtěte si téma [přepisování nastavení ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 `ToolsVersion`Atribut se používá také pro migraci projektu. Například pokud otevřete projekt sady Visual Studio 2008 v aplikaci Visual Studio 2010, soubor projektu je aktualizován tak, aby zahrnoval ToolsVersion = "4.0". Pokud se pokusíte tento projekt otevřít v sadě Visual Studio 2008, nerozpozná upgradovaný, `ToolsVersion` a proto projekt sestaví, jako by byl atribut stále nastaven na hodnotu 3,5.

 Sady Visual Studio 2010 a Visual Studio 2012 používají ToolsVersion 4,0. Visual Studio 2013 používá ToolsVersion 12,0. V mnoha případech můžete projekt otevřít ve všech třech verzích sady Visual Studio beze změny. Sada Visual Studio vždy používá správnou sadu nástrojů, ale budete upozorněni, pokud použitá verze neodpovídá verzi v souboru projektu. V téměř všech případech je toto upozornění neškodné, protože sady nástrojů jsou ve většině případů kompatibilní.

 Dílčí sady nástrojů, které jsou popsány dále v tomto tématu, umožňují nástroji MSBuild automaticky přepínat, kterou sadu nástrojů použít v závislosti na kontextu, ve kterém je sestavení spouštěno. Nástroj MSBuild například používá novější sadu nástrojů, pokud je spuštěn v sadě Visual Studio 2012 než při spuštění v sadě Visual Studio 2010, aniž by bylo nutné explicitně měnit soubor projektu. Další informace najdete v tématu o tom, jak se používá [vlastní verze projektů](../misc/making-custom-projects-version-aware.md).

## <a name="toolset-implementation"></a>Implementace sady nástrojů
 Implementujte sadu nástrojů výběrem cest různých nástrojů, cílů a úloh, které tvoří sadu nástrojů. Nástroje v sadě nástrojů, které nástroj MSBuild definuje, pocházejí z následujících zdrojů:

- Složka .NET Framework.

- Další spravované nástroje.

  Mezi spravované nástroje patří ResGen.exe a TlbImp.exe.

  Nástroj MSBuild nabízí dva způsoby, jak získat přístup ke sadě nástrojů:

- Pomocí vlastností sady nástrojů

- Pomocí <xref:Microsoft.Build.Utilities.ToolLocationHelper> metod

  Vlastnosti sady nástrojů určují cesty nástrojů. Nástroj MSBuild používá hodnotu `ToolsVersion` atributu v souboru projektu k vyhledání odpovídajícího klíče registru a poté pomocí informací v klíči registru nastaví vlastnosti sady nástrojů. Například pokud `ToolsVersion` má hodnotu `12.0` , MSBuild nastaví vlastnosti sady nástrojů podle tohoto klíče registru: HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0.

  Jedná se o vlastnosti sady nástrojů:

- `MSBuildToolsPath` Určuje cestu binárních souborů nástroje MSBuild.

- `SDK40ToolsPath` Určuje cestu dalších spravovaných nástrojů pro MSBuild 4. x (což může být 4,0 nebo 4,5).

- `SDK35ToolsPath` Určuje cestu dalších spravovaných nástrojů pro MSBuild 3,5.

  Alternativně můžete určit sadu nástrojů programově voláním metod <xref:Microsoft.Build.Utilities.ToolLocationHelper> třídy. Třída zahrnuje tyto metody:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> Vrátí cestu ke složce .NET Framework.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> Vrátí cestu k souboru ve složce .NET Framework.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> Vrátí cestu ke složce spravovaných nástrojů.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> Vrátí cestu k souboru, který je obvykle umístěn ve složce spravované nástroje.

- [GetPathToBuildTools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) vrátí cestu nástrojů pro sestavení.

### <a name="sub-toolsets"></a>Dílčí sady nástrojů
 Jak je popsáno výše v tomto tématu, nástroj MSBuild pomocí klíče registru určí cestu základních nástrojů. Pokud má klíč podklíč, nástroj MSBuild ho použije k určení cesty dílčí sady nástrojů, která obsahuje další nástroje. V tomto případě je sada nástrojů definovaná kombinací definic vlastností, které jsou definovány v obou klíčích.

> [!NOTE]
> Pokud názvy vlastností sady nástrojů kolidují, hodnota, která je definována pro cestu k podklíči, přepíše hodnotu definovanou pro cestu k kořenovému klíči.

 Dílčí sady nástrojů se stanou aktivními v přítomnosti `VisualStudioVersion` vlastnosti Build. Tato vlastnost může mít jednu z těchto hodnot:

- "10,0" Určuje dílčí sadu nástrojů .NET Framework 4.

- "11,0" Určuje dílčí sadu nástrojů .NET Framework 4,5

- "12,0" Určuje dílčí sadu nástrojů .NET Framework 4.5.1

  Dílčí sady nástrojů 10,0 a 11,0 by měly být použity s ToolsVersion 4,0. V novějších verzích by se měla shodovat verze dílčí sady nástrojů a ToolsVersion.

  Během sestavení MSBuild automaticky určí a nastaví výchozí hodnotu pro `VisualStudioVersion` vlastnost, pokud již není definována.

  MSBuild poskytuje přetížení pro `ToolLocationHelper` metody, které přidávají `VisualStudioVersion` výčtové hodnoty jako parametr.

  Dílčí sady nástrojů byly představeny v .NET Framework 4,5.

## <a name="see-also"></a>Viz také

- [Standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md)
- [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)
