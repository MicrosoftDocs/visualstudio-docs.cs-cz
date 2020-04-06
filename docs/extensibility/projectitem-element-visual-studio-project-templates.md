---
title: Element ProjectItem (šablony projektů sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11052d8e585f1d06f6d787402001cfbbe2b6810f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701841"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Element ProjectItem (šablony projektů sady Visual Studio)
Určuje soubor, který je součástí šablony projektu.

> [!NOTE]
> Prvek `ProjectItem` přijímá různé atributy v závislosti na tom, zda je šablona pro projekt nebo položku. Toto téma `ProjectItem` vysvětluje prvek pro šablony projektů. Vysvětlení prvku pro `ProjectItem` šablony položek naleznete v tématu [ProjectItem Element (Visual Studio Item Templates).](../extensibility/projectitem-element-visual-studio-item-templates.md)

 \<VSTemplate \<> TemplateContent \< \<> project> ProjectItem>

## <a name="syntax"></a>Syntaxe

```
<ProjectItem
    TargetFileName="TargetFileName.ext"
    ReplaceParameters="true/false"
    OpenInEditor="true/false"
    OpenInWebBrowser="true/false"
    OpenInHelpBrowser="true/false"
    OpenOrder="Value">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy

| Atribut | Popis |
|---------------------| - |
| `TargetFileName` | Nepovinný atribut.<br /><br /> Určuje název a cestu položky projektu při vytvoření projektu ze šablony. Tento atribut je užitečný pro vytvoření struktury adresáře odlišné od struktury adresáře v souboru *ZIP* šablony nebo pro použití nahrazení parametrů k vytvoření názvu položky. |
| `ReplaceParameters` | Nepovinný atribut.<br /><br /> Logická hodnota, která určuje, zda má položka hodnoty parametrů, které musí být nahrazeny při vytvoření projektu ze šablony. Výchozí hodnota `false`je . |
| `OpenInEditor` | Nepovinný atribut.<br /><br /> Logická hodnota, která určuje, zda má být položka [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otevřena v příslušném editoru v aplikaci při vytvoření projektu ze šablony.<br /><br /> `OpenInWebBrowser` Atributy `OpenInHelpBrowser` a jsou ignorovány u `OpenInEditor` položky `true`s hodnotou .<br /><br /> Výchozí hodnota je `false`. |
| `OpenInWebBrowser` | Nepovinný atribut.<br /><br /> Logická hodnota, která určuje, zda má být položka otevřena webový prohlížeč při vytvoření projektu ze šablony.<br /><br /> Ve webovém prohlížeči lze otevřít pouze soubory HTML a textové soubory, které jsou místní pro projekt. Pomocí tohoto atributu nelze otevřít externí adresy URL.<br /><br /> Výchozí hodnota je `false`. |
| `OpenInHelpBrowser` | Nepovinný atribut.<br /><br /> Logická hodnota, která určuje, zda má být položka otevřena v prohlížeči nápovědy při vytvoření projektu ze šablony.<br /><br /> V prohlížeči nápovědy lze otevřít pouze soubory HTML a textové soubory, které jsou v projektu místní. Pomocí tohoto atributu nelze otevřít externí adresy URL.<br /><br /> Výchozí hodnota je `false`. |
| `OpenOrder` | Nepovinný atribut.<br /><br /> Určuje číselnou hodnotu, která představuje pořadí, ve které budou položky otevřeny v příslušných editorech. Všechny hodnoty musí být násobky 10. Nejprve `OpenOrder` se otevřou položky s vyššími hodnotami. |

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Určuje soubory nebo adresáře, které chcete přidat do projektu.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 A, `string` který představuje název nebo cestu k souboru v souboru *.zip* šablony.

## <a name="remarks"></a>Poznámky
 `ProjectItem`je volitelné dítě `Project`.

 Atribut `TargetFileName` lze použít k vytvoření struktury adresáře odlišné od struktury adresáře v souboru *zip* šablony. Pokud například soubor *MyFile.vb* existuje v kořenovém adresáři souboru *ZIP* šablony, ale chcete, aby byl soubor umístěn do adresáře s názvem *CustomFiles* ve všech projektech vytvořených ze šablony, použijte následující xml:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 Atribut `TargetFileName` lze také přejmenovat soubory, které obsahují mezinárodní znaky v jejich názvy souborů. Soubor *ZIP* šablony například nemůže obsahovat názvy souborů se znaky Unicode, takže soubor musí být přejmenován, aby mohl být komprimován do souboru *ZIP.* Atribut `TargetFileName` lze použít k nastavení názvu souboru zpět na původní název souboru Unicode.

 Atribut `TargetFileName` lze také přejmenovat soubory s parametry. Následující postup vysvětluje, jak přejmenovat soubor *MyFile.vb*, který existuje v kořenovém adresáři souboru *ZIP* šablony, na název souboru na základě názvu projektu.

### <a name="to-rename-files-with-parameters"></a>Přejmenování souborů pomocí parametrů

1. V souboru *.vstemplate* použijte následující kód XML:

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Otevřete soubor projektu (*.vbproj* pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekt) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]v textovém editoru nebo .

3. Vyhledejte řádek v souboru projektu, který vypadá podobně jako následující xml:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Nahraďte řádek kódu následujícím xml:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Při vytvoření projektu z této šablony bude název souboru založen na názvu, který uživatel zadal v dialogovém okně **Nový projekt,** přičemž budou odebrány všechny nebezpečné znaky a mezery. Další informace naleznete v [tématu Template parameters](../ide/template-parameters.md).

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro šablonu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu pro aplikaci.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Element ProjectItem (šablony položek sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
