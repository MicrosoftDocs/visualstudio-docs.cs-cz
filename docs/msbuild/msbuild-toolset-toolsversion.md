---
title: Sada nástrojů MSBuild (ToolsVersion) | Dokumenty společnosti Microsoft
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6aaa6309e04f5143b70ff233c0b621ab2350b9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633119"
---
# <a name="msbuild-toolset-toolsversion"></a>Sada nástrojů MSBuild (atribut ToolsVersion)

MSBuild používá sadu nástrojů úkolů, cílů a nástrojů k vytvoření aplikace. Sada nástrojů MSBuild obvykle obsahuje soubor *microsoft.common.tasks,* soubor *Microsoft.common.targets* a kompilátory, například *csc.exe* a *vbc.exe*. Většinu sad nástrojů lze použít ke kompilaci aplikací do více než jedné verze rozhraní .NET Framework a více než jedné systémové platformy. Sadu nástrojů MSBuild 2.0 lze však použít k cílení pouze na rozhraní .NET Framework 2.0.

## <a name="toolsversion-attribute"></a>ToolsVersion, atribut

::: moniker range=">=vs-2019"
 Určete sadu nástrojů `ToolsVersion` v atributu prvku [Project](../msbuild/project-element-msbuild.md) v souboru projektu. Následující příklad určuje, že projekt by měl být vytvořen pomocí sady nástrojů MSBuild "Current".

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 Určete sadu nástrojů `ToolsVersion` v atributu prvku [Project](../msbuild/project-element-msbuild.md) v souboru projektu. Následující příklad určuje, že projekt by měl být vytvořen pomocí sady nástrojů MSBuild 15.0.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> Některé typy projektů `sdk` používají `ToolsVersion`atribut namísto . Další informace naleznete [v tématu Balíčky, metadata a architektury](/dotnet/core/packages) a [dodatky k formátu csproj pro .NET Core](/dotnet/core/tools/csproj).

## <a name="how-the-toolsversion-attribute-works"></a>Jak funguje atribut ToolsVersion

 Při vytváření projektu v sadě Visual Studio nebo upgrade `ToolsVersion` existujícího projektu je atribut s názvem automaticky zahrnut do souboru projektu a jeho hodnota odpovídá verzi MSBuild, která je součástí edice Visual Studio. Další informace naleznete v [tématu Přehled cílení na rozhraní Framework](../ide/visual-studio-multi-targeting-overview.md).

 Pokud `ToolsVersion` je hodnota definována v souboru projektu, MSBuild používá tuto hodnotu k určení hodnot vlastností sady nástrojů, které jsou k dispozici pro projekt. Vlastnost One Toolset je `$(MSBuildToolsPath)`, která určuje cestu k nástrojům rozhraní .NET Framework. Je vyžadována pouze `$(MSBuildBinPath)`vlastnost sady nástrojů (nebo ).

 Počínaje Visual Studio 2013, verze sady nástrojů MSBuild je stejná jako číslo verze sady Visual Studio. MSBuild výchozí pro tuto sadu nástrojů v rámci sady Visual Studio a na příkazovém řádku, bez ohledu na verzi sady nástrojů zadanou v souboru projektu.  Toto chování lze přepsat pomocí -ToolsVersion příznak. Další informace naleznete [v tématu Přepsat nastavení ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 V následujícím příkladu MSBuild najde soubor *Microsoft.CSharp.targets* pomocí vyhrazené vlastnosti. `MSBuildToolsPath`

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Hodnotu můžete upravit `MSBuildToolsPath` definováním vlastní sady nástrojů. Další informace naleznete [v tématu Standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md).

 Při vytváření řešení na příkazovém `ToolsVersion` řádku a zadejte *formsbuild.exe*, všechny projekty a `ToolsVersion`jejich závislosti mezi projekty jsou vytvořeny `ToolsVersion`podle tohoto , i v případě, že každý projekt v řešení určuje jeho vlastní . Chcete-li `ToolsVersion` definovat hodnotu pro projekt, viz [Přepsání ToolsVersion nastavení](../msbuild/overriding-toolsversion-settings.md).

 Atribut `ToolsVersion` se také používá pro migraci projektu. Pokud například otevřete projekt sady Visual Studio 2008 v sadě Visual Studio 2010, soubor projektu se aktualizuje tak, aby zahrnoval ToolsVersion="4.0". Pokud se pak pokusíte otevřít tento projekt v sadě Visual Studio 2008, nerozpozná upgradované `ToolsVersion` a proto vytvoří projekt, jako by atribut byl stále nastaven na 3,5.

 Visual Studio 2010 a Visual Studio 2012 používají ToolsVersion 4.0. Visual Studio 2013 používá ToolsVersion 12.0. Visual Studio 2015 používá ToolsVersion 14.0 a Visual Studio 2017 používá ToolsVersion 15.0. V mnoha případech můžete otevřít projekt ve více verzích sady Visual Studio bez evidenčních úprav. Visual Studio vždy používá správnou sadu nástrojů, ale budete upozorněni, pokud použitá verze neodpovídá verzi v souboru projektu. Téměř ve všech případech je toto upozornění neškodné, protože sady nástrojů jsou ve většině případů kompatibilní.

 Podsady nástrojů, které jsou popsány dále v tomto tématu, umožňují MSBuild automaticky přepínat, které sady nástrojů použít na základě kontextu, ve kterém je sestavení spuštěno. Například MSBuild používá novější sadu nástrojů při spuštění v sadě Visual Studio 2012 než při spuštění v sadě Visual Studio 2010, aniž byste museli explicitně měnit soubor projektu.

## <a name="toolset-implementation"></a>Implementace sady nástrojů

 Implementujte sadu nástrojů výběrem cest různých nástrojů, cílů a úkolů, které tvoří sadu nástrojů. Nástroje v sadě nástrojů, které definuje MSBuild, pocházejí z následujících zdrojů:

- Složka rozhraní .NET Framework.

- Další spravované nástroje.

  Spravované nástroje zahrnují *ResGen.exe* a *TlbImp.exe*.

Nástroj MSBuild nabízí dva způsoby přístupu k sadě nástrojů:

- Pomocí vlastností sady nástrojů

- Pomocí <xref:Microsoft.Build.Utilities.ToolLocationHelper> metod

Vlastnosti sady nástrojů určují cesty nástrojů. Počínaje Visual Studio 2017 MSBuild již nemá pevné umístění. Ve výchozím nastavení je umístěn ve složce *MSBuild\15.0\Bin* vzhledem k umístění instalace sady Visual Studio. V dřívějších verzích msbuild používá `ToolsVersion` hodnotu atributu v souboru projektu vyhledejte odpovídající klíč registru a potom používá informace v klíči registru k nastavení vlastností sady nástrojů. Pokud `ToolsVersion` má například `12.0`hodnotu , nastaví msbuild vlastnosti sady nástrojů podle tohoto klíče registru: **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**.

 Jedná se o vlastnosti sady nástrojů:

- `MSBuildToolsPath`určuje cestu binárních souborů MSBuild.

- `SDK40ToolsPath`určuje cestu dalšíspravované nástroje pro MSBuild 4.x (což může být 4.0 nebo 4.5).

- `SDK35ToolsPath`určuje cestu dalších spravovaných nástrojů pro MSBuild 3.5.

Alternativně můžete nastavit sadu nástrojů programově voláním metody <xref:Microsoft.Build.Utilities.ToolLocationHelper> třídy. Třída zahrnuje tyto metody:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A>vrátí cestu ke složce rozhraní .NET Framework.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A>vrátí cestu k souboru ve složce rozhraní .NET Framework.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A>vrátí cestu ke složce spravovaných nástrojů.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A>vrátí cestu k souboru, který je obvykle umístěn ve složce spravovaných nástrojů.

- [GetPathToBuildTools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) vrátí cestu nástroje sestavení.

### <a name="sub-toolsets"></a>Podsady nástrojů

 Pro verze MSBuild před 15.0 používá MSBuild klíč registru k určení cesty k základním nástrojům. Pokud klíč obsahuje podklíč, MSBuild jej používá k určení cesty podsady nástrojů, která obsahuje další nástroje. V tomto případě je sada nástrojů definována kombinací definic vlastností, které jsou definovány v obou klíčích.

> [!NOTE]
> Pokud názvy vlastností sady nástrojů kolidují, hodnota definovaná pro cestu podklíče přepíše hodnotu, která je definována pro cestu kořenového klíče.

 Podsady nástrojů se stanou aktivními `VisualStudioVersion` v přítomnosti vlastnosti sestavení. Tato vlastnost může mít jednu z těchto hodnot:

- "10.0" určuje podsadu nástrojů rozhraní .NET Framework 4

- "11.0" určuje podsadu nástrojů rozhraní .NET Framework 4.5

- "12.0" určuje podsadu nástrojů rozhraní .NET Framework 4.5.1

Podsady nástrojů 10.0 a 11.0 by měly být použity s ToolsVersion 4.0. V novějších verzích by se měla shodovat verze podsady nástrojů a ToolsVersion.

Během sestavení MSBuild automaticky určí a nastaví `VisualStudioVersion` výchozí hodnotu pro vlastnost, pokud ještě není definována.

MSBuild poskytuje přetížení `ToolLocationHelper` pro metody, `VisualStudioVersion` které přidávají výčtovou hodnotu jako parametr

Podsady nástrojů byly zavedeny v rozhraní .NET Framework 4.5.

## <a name="see-also"></a>Viz také

- [Standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md)
- [Multicílení](../msbuild/msbuild-multitargeting-overview.md)
