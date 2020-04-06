---
title: 'Nový projekt Generace: Pod kapotou, část druhá | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707012"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nová generace projektů: Pod pokličkou, část druhá

V [nové generaci projektu: Pod kapotou, část jedna](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) jsme viděli, jak je vyplněno dialogové okno Nový **projekt.** Předpokládejme, že jste vybrali **aplikaci Visual C# Windows**, vyplnili textová pole **Název** a **Umístění** a klikli na OK.

## <a name="generating-the-solution-files"></a>Generování souborů řešení
 Výběrem šablony aplikace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] přesměruje rozbalit a otevřít odpovídající soubor .vstemplate a spustit šablonu pro interpretaci příkazů XML v tomto souboru. Tyto příkazy vytvářejí projekty a položky projektu v novém nebo existujícím řešení.

 Šablona rozbalí zdrojové soubory, nazývané šablony položek, ze stejné složky ZIP, která obsahuje soubor .vstemplate. Šablona tyto soubory zkopíruje do nového projektu a odpovídajícím způsobem je přizpůsobí.

### <a name="template-parameter-replacement"></a>Nahrazení parametru šablony
 Když šablona zkopíruje šablonu položky do nového projektu, nahradí všechny parametry šablony řetězci pro přizpůsobení souboru. Parametr šablony je speciální token, který předchází a následuje znak dolaru, například $date$.

 Podívejme se na typickou šablonu položky projektu. Extrahujte a prohlédněte si Program.cs ve složce Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

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

Pokud vytvoříte nový projekt aplikace systému Windows `$safeprojectname$` s názvem Jednoduché, šablona nahradí parametr názvem projektu.

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

 Úplný seznam parametrů šablony naleznete v tématu [Parametry šablony](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Pohled dovnitř . Soubor VSTemplate
 Základní soubor .vstemplate má tento formát

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Podívali jsme \<se na TemplateData> části nové [generace projektu: Pod kapotou, část první](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Značky v této části slouží k řízení vzhledu dialogového okna **Nový projekt.**

 Značky v \<části TemplateContent> řídí generování nových projektů a položek projektu. Zde je \<oddíl TemplateContent> ze souboru cswindowsapplication.vstemplate ve složce \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

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

 Značka \<Project> řídí generování projektu a \<značka ProjectItem> řídí generování položky projektu. Pokud je parametr ReplaceParameters pravdivý, šablona přizpůsobí všechny parametry šablony v souboru projektu nebo položce. V tomto případě jsou přizpůsobeny všechny položky projektu, s výjimkou Nastavení.settings.

 Parametr TargetFileName určuje název a relativní cestu výsledného souboru nebo položky projektu. To umožňuje vytvořit strukturu složek pro váš projekt. Pokud tento argument nezadáte, bude mít položka projektu stejný název jako šablona položky projektu.

 Výsledná struktura složek aplikace systému Windows vypadá takto:

 ![Jednoduché řešení](../../extensibility/internals/media/simplesolution.png "Jednoduché řešení")

 První a \<jediná značka project> v šabloně zní:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 To dává pokyn šablonu Nový projekt k vytvoření souboru projektu Simple.csproj zkopírováním a přizpůsobením položky šablony windowsapplication.csproj.

### <a name="designers-and-references"></a>Návrháři a reference
 V Průzkumníku řešení se zobrazí, že složka Vlastnosti je přítomna a obsahuje očekávané soubory. Ale co odkazy na projekt a závislosti souborů návrháře, jako je například Resources.Designer.cs resources.resx a Form1.Designer.cs Form1.cs?  Ty jsou nastaveny v souboru Simple.csproj, když je generován.

 Zde je \<ItemGroup> z Simple.csproj, který vytváří odkazy na projekt:

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

 Můžete vidět, že se jedná o šest odkazů na projekt, které se zobrazí v Průzkumníku řešení. Zde je oddíl z \<jiného> ItemGroup. Mnoho řádků kódu byly odstraněny pro přehlednost. Tato část Settings.Designer.cs v závislosti na nastavení Nastavení:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Viz také

- [Nová generace projektů: Pod pokličkou, část první](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
