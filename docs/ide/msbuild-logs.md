---
title: Řešení potíží a vytváření protokolů pro problémy nástroje MSBuild
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: troubleshooting
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
ms.openlocfilehash: 24df9f7c44ea2dbb9e9899abf68823683422da71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235066"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Řešení potíží a vytváření protokolů pro problémy nástroje MSBuild

Následující postupy vám pomohou diagnostikovat problémy sestavení v projektu sady Visual Studio a v případě potřeby vytvořit protokol pro odeslání do Microsoftu pro účely šetření.

## <a name="a-property-value-is-ignored"></a>Hodnota vlastnosti se ignoruje.

Pokud se zdá, že vlastnost projektu je nastavena na konkrétní hodnotu, ale nemá žádný vliv na sestavení, postupujte podle následujících kroků:

1. Otevřete Developer Command Prompt sady Visual Studio, která odpovídá vaší verzi sady Visual Studio.
1. Po nahrazení hodnot pro cestu k řešení, konfiguraci a název projektu spusťte následující příkaz:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    Tento příkaz vytvoří soubor projektu MSBuild "předzpracovaný" (out.xml). V tomto souboru můžete vyhledat konkrétní vlastnost a zjistit, kde je definována.

Poslední definice vlastnosti je to, co sestavení spotřebovává. Pokud je vlastnost nastavena dvakrát, druhá hodnota přepíše první. Nástroj MSBuild také vyhodnocuje projekt v několika průchodech:

- Element PropertyGroups a importy
- ItemDefinitionGroups
- ItemGroups
- Targets

Proto v uvedeném pořadí:

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

Hodnota "MyMetadata" pro položku "MyFile.txt" bude při sestavování vyhodnocena jako "B" (nikoli "a" a není prázdná)

## <a name="incremental-build-is-building-more-than-it-should"></a>Přírůstkové sestavování sestavuje víc, než by mělo

Pokud nástroj MSBuild nemusí nutně znovu sestavit projekt nebo položku projektu, vytvořte podrobný nebo binární protokol sestavení. V protokolu můžete vyhledat soubor, který byl sestaven nebo kompilován zbytečně. Výstup bude vypadat nějak takto:

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

Pokud sestavíte v integrovaném vývojovém prostředí (IDE) sady Visual Studio (s detailní podrobností okna výstup), **okno výstup** zobrazuje důvod, proč každý projekt není aktuální:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>Vytvoření binárního protokolu MSBuild

1. Otevřete Developer Command Prompt pro vaši verzi sady Visual Studio
1. Z příkazového řádku spusťte jeden z následujících příkazů. (Nezapomeňte použít svůj skutečný projekt a konfigurační hodnoty.):

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    nebo

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Soubor MSBuild. binlog bude vytvořen v adresáři, ze kterého jste spustili nástroj MSBuild. Můžete ji zobrazit a vyhledat pomocí [prohlížeče strukturovaného protokolu nástroje MSBuild](http://www.msbuildlog.com/).

## <a name="create-a-detailed-log"></a>Vytvořit podrobný protokol

1. V hlavní nabídce sady Visual Studio přejděte na **nástroje**  >  **Možnosti**  >  **projekty a řešení**  > **sestavování a spouštění**.
1. Nastavte **Podrobnosti sestavení projektu MSBuild** na **podrobné** v obou polích se seznamem. Horní jeden ovládací prvek má v **okno výstup** podrobnost sestavení a druhá z nich je podrobností sestavení v \<projectname\> souboru. log, který je vytvořen v zprostředkujícím adresáři každého projektu během sestavení.
2. Z příkazového řádku pro vývojáře sady Visual Studio zadejte jeden z těchto příkazů a nahraďte svou skutečnou cestu a konfigurační hodnoty:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    nebo

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Soubor MSBuild. log bude vytvořen v adresáři, ze kterého jste spustili nástroj MSBuild.

## <a name="see-also"></a>Viz také

- [Řešení potíží s Visual Studiem](/troubleshoot/visualstudio/welcome-visual-studio/)
