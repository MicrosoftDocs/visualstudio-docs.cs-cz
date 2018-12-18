---
title: 'Nová generace projektů: Pod pokličkou, část 2 | Dokumentace Microsoftu'
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
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5732db4ab36a7e198ee6ebdce185294d3b5bc31
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722473"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nová generace projektů: Pod pokličkou, část druhá
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V [nová generace projektů: pod pokličkou, část jednoho](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) jsme viděli jak **nový projekt** pole se vyplní dialogového okna. Předpokládejme, že jste vybrali **aplikace Visual C# Windows**, vyplněné **název** a **umístění** textová pole a kliknutí na OK.  
  
## <a name="generating-the-solution-files"></a>Generují se soubory řešení  
 Výběr šablony aplikace přesměruje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se rozzipují a otevřou odpovídající soubor .vstemplate a spusťte šablonu a interpretovat příkazy XML v tomto souboru. Tyto příkazy vytvoří projekty a položky projektu v rámci nového nebo existujícího řešení.  
  
 Šablona rozbalí zdrojové soubory, volá se, šablony položek ze stejné složky ZIP, který obsahuje soubor .vstemplate. Šablona zkopíruje tyto soubory do nového projektu přizpůsobení je odpovídajícím způsobem. Přehled šablon projektů a položek, naleznete v tématu [NIB: šablony sady Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Nahrazení parametru šablony  
 Když šablona zkopíruje do nového projektu šablony položky, nahradí řetězce pro přizpůsobení souboru žádné parametry šablony. Parametr šablony je speciální token, který je před a za nímž následuje znak dolaru, třeba $date$.  
  
 Podívejme se na šablonu položky obvyklou pro projekty. Extrahovat a prozkoumejte Program.cs ve složce Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.  
  
```  
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
  
 Pokud vytvoříte nový projekt aplikace Windows s názvem jednoduchý, nahradí šablony `$safeprojectname$` parametr s názvem projektu.  
  
```  
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
  
 Úplný seznam parametrů šablony, najdete v části [parametry šablony](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Podívejte se uvnitř. Soubor VSTemplate  
 Soubor basic .vstemplate má tento formát  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Zvažovali jsme i \<TemplateData > v oddílu [nová generace projektů: pod pokličkou, část jednoho](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Značky v této části se používají k řízení vzhledu **nový projekt** dialogové okno.  
  
 Značky v \<TemplateContent > části ovládacího prvku generování nových projektů a položek projektů. Tady je \<TemplateContent > části cswindowsapplication.vstemplate souboru ve složce 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip \Program Files\Microsoft Visual Studio.  
  
```  
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
  
 \<Projekt > značky určuje generování projektu a \<ProjectItem > značky určuje generování položky projektu. Pokud má parametr ReplaceParameters hodnotu true, šablona přizpůsobovat všech parametrů šablony v souboru projektu nebo položky. V takovém případě všechny položky projektu jsou přizpůsobené, s výjimkou Settings.settings.  
  
 TargetFileName parametr určuje název a relativní cestu z výsledného souboru projektu nebo položky. To vám umožní vytvořit strukturu složek pro váš projekt. Pokud nezadáte tento argument, položky projektu bude mít stejný název jako šablonu položky projektu.  
  
 Výsledný struktury složek Windows aplikace vypadá takto:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 První a jediný \<Projekt > značky v šabloně čtení:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Toto dá pokyn šabloně nový projekt pro vytvoření souboru projektu Simple.csproj zkopírováním a přizpůsobení windowsapplication.csproj šablony položky.  
  
### <a name="designers-and-references"></a>Návrháři a odkazy  
 Zobrazí se v Průzkumníku řešení, že je k dispozici vlastnosti složky a obsahuje očekávané soubory. Ale co o projekt odkazuje na a soubor návrháře závislosti, jako je například Resources.Designer.cs k Resources.resx a Form1.Designer.cs k Form1.cs?  Tato nastavení jsou v souboru Simple.csproj kdy se generují.  
  
 Tady je \<ItemGroup > z Simple.csproj, který vytváří odkazy projektu:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Uvidíte, že jde o šesti projektu odkazy, které se zobrazí v Průzkumníku řešení. Tady je oddíl z jiné \<ItemGroup >. Pro přehlednost se odstranily spousty řádků kódu. Tato část umožňuje Settings.Designer.cs závisí na Settings.settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Viz také  
 [Nová generace projektů: Pod pokličkou, část první](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)


