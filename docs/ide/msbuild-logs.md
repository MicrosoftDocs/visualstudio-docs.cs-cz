---
title: Poradce při potížích a vytváření protokolů pro problémy s msbuildem
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: 07b2c5e941d31ab1be853f9a89af94462329bdf2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278807"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Poradce při potížích a vytváření protokolů pro problémy s msbuildem

Následující postupy vám mohou pomoci diagnostikovat problémy se sestavením v projektu sady Visual Studio a v případě potřeby vytvořit protokol, který bude odeslán společnosti Microsoft k prošetření.

## <a name="a-property-value-is-ignored"></a>Hodnota vlastnosti je ignorována.

Pokud se vlastnost projektu zdá být nastavena na určitou hodnotu, ale nemá žádný vliv na sestavení, postupujte takto:

1. Otevřete příkazový řádek pro vývojáře sady Visual Studio, který odpovídá vaší verzi sady Visual Studio.
1. Spusťte následující příkaz po nahrazení hodnot cesty řešení, konfigurace a názvu projektu:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    Tento příkaz vytvoří "preprocessed" msbuild soubor projektu (out.xml). V tomto souboru můžete vyhledat určitou vlastnost a zjistit, kde je definován.

Poslední definice vlastnosti je, co spotřebovává sestavení. Pokud je vlastnost nastavena dvakrát, druhá hodnota přepíše první. MSBuild také vyhodnocuje projekt v několika průchodech:

- PropertyGroups a importy
- ItemDefinitionGroups
- Skupiny položek
- Cíle

Proto, vzhledem k následujícímu pořadí:

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

Hodnota "MyMetadata" pro položku "MyFile.txt" bude vyhodnocena na "B" během sestavení (ne "A" a není prázdný)

## <a name="incremental-build-is-building-more-than-it-should"></a>Přírůstkové sestavení buduje více, než by mělo

Pokud MSBuild je zbytečně opětovné sestavení projektu nebo položky projektu, vytvořte podrobný nebo binární protokol sestavení. V protokolu můžete zbytečně vyhledat soubor, který byl sestaven nebo zkompilován. Výstup vypadá asi takto:

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

Pokud vytváříte v ide sady Visual Studio (s podrobnostmi o podrobném výstupním okně), **okno Výstup** zobrazí důvod, proč každý projekt není aktuální:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>Vytvoření binárního protokolu msbuild

1. Otevření příkazového řádku pro vývojáře pro vaši verzi sady Visual Studio
1. Na příkazovém řádku spusťte jeden z následujících příkazů. (Nezapomeňte použít skutečné hodnoty projektu a konfigurace.):

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    – nebo –

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Soubor Msbuild.binlog bude vytvořen v adresáři, ze kterého jste spustili službu MSBuild. Můžete jej zobrazit a prohledávat pomocí [programu Msbuild Structured Log Viewer](http://www.msbuildlog.com/).

## <a name="create-a-detailed-log"></a>Vytvoření podrobného protokolu

1. V hlavní nabídce sady Visual Studio**Options** > přejděte na**projekty a řešení** > **nástroje** > **sestavení a spuštění**.
1. Nastavte **msbuild projektu vytvořit podrobnost** podrobně **v** obou polích se seznamem. Horní ovládací prvky sestavení podrobností v **okně výstup** a druhý ovládací prvky sestavení podrobnost v souboru \<\>název_projektu .log, který je vytvořen v adresáři zprostředkující každý projekt během sestavení.
2. Z příkazového řádku vývojáře sady Visual Studio zadejte jeden z těchto příkazů a napočtete skutečné hodnoty cesty a konfigurace:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    – nebo –

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Soubor Msbuild.log bude vytvořen v adresáři, ze kterého jste spustili msbuild.
