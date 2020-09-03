---
title: 'Nová generace projektů: pod digestoří, část dvě | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707012"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nová generace projektů: Pod kapotou, část 2

V [nové generaci projektu: v digestoři, část One,](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) jsme viděli, jak se vyplní dialogové okno **Nový projekt** . Předpokládejme, že jste vybrali **aplikaci Visual C# pro Windows**, vyplnili textová pole **název** a **umístění** a kliknuli jste na tlačítko OK.

## <a name="generating-the-solution-files"></a>Generování souborů řešení
 Výběr šablony aplikace, která je přesměrována na rozbalení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a otevření odpovídajícího souboru. vstemplate a spuštění šablony pro interpretaci příkazů XML v tomto souboru. Tyto příkazy vytvářejí projekty a položky projektu v novém nebo existujícím řešení.

 Šablona rozbalí zdrojové soubory, označované jako šablony položek, ze stejné složky. zip, která obsahuje soubor. vstemplate. Šablona tyto soubory zkopíruje do nového projektu a odpovídajícím způsobem ji přizpůsobuje.

### <a name="template-parameter-replacement"></a>Nahrazení parametru šablony
 Když šablona zkopíruje šablonu položky do nového projektu, nahradí všechny parametry šablony s řetězci pro přizpůsobení souboru. Parametr šablony je speciální token, který předchází a následuje znak dolaru, například $date $.

 Pojďme se podívat na typickou šablonu položky projektu. Extrahujte a prověřte Program.cs ve složce Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

Pokud vytvoříte nový projekt aplikace pro systém Windows s názvem jednoduchý, šablona nahradí `$safeprojectname$` parametr názvem projektu.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 Úplný seznam parametrů šablony najdete v tématu [parametry šablony](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Vzhled uvnitř. Soubor VSTemplate
 Soubor Basic. vstemplate má tento formát.

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Prohlédli jsme se v \<TemplateData> části [nového projektu generace: v digestoři, která je první částí](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Značky v této části slouží k řízení vzhledu dialogového okna **Nový projekt** .

 Značky v \<TemplateContent> oddílu určují generování nových projektů a položek projektu. Tady je \<TemplateContent> oddíl ze souboru cswindowsapplication. vstemplate ve složce \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 \<Project>Značka řídí generování projektu a \<ProjectItem> značka řídí generování položky projektu. Pokud má parametr ReplaceParameters hodnotu true, šablona bude přizpůsobovat všechny parametry šablony v souboru projektu nebo v položce. V tomto případě jsou všechny položky projektu přizpůsobené, s výjimkou nastavení. Settings.

 Parametr TargetFileName Určuje název a relativní cestu výsledného souboru projektu nebo položky. To vám umožní vytvořit strukturu složek pro svůj projekt. Pokud tento argument nezadáte, bude mít položka projektu stejný název jako šablona položky projektu.

 Výsledná struktura složky aplikace systému Windows vypadá takto:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 První a jenom \<Project> značka v šablonách čte:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 To instruuje novou šablonu projektu pro vytvoření jednoduchého souboru projektu. csproj zkopírováním a přizpůsobením položky šablony souboru WindowsApplication. csproj.

### <a name="designers-and-references"></a>Návrháři a odkazy
 Můžete vidět v Průzkumník řešení, že složka Properties je přítomná a obsahuje očekávané soubory. Ale co se týká odkazů na projekt a závislostí souborů návrháře, jako je například Resources.Designer.cs k souboru Resources. resx a Form1.Designer.cs na Form1.cs?  Ty jsou nastaveny v jednoduchém souboru. csproj při jeho vygenerování.

 Tady je \<ItemGroup> z jednoduchého. csproj, který vytváří odkazy na projekt:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Vidíte, že se jedná o šest odkazů na projekt, které se zobrazí v Průzkumník řešení. Tady je oddíl z jiného \<ItemGroup> . Bylo odstraněno mnoho řádků kódu pro přehlednost. V této části je Settings.Designer.cs závislý na nastavení. nastavení:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Viz také

- [Nová generace projektů: Pod kapotou, část 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [Nástroji](../../msbuild/msbuild.md)
