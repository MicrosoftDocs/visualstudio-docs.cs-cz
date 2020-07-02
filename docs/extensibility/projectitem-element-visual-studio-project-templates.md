---
title: ProjectItem – element (šablony projektů sady Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
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
ms.openlocfilehash: 943f50823892e3cd942709bdcd4556b65c006b58
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770309"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem – element (šablony projektů sady Visual Studio)
Určuje soubor, který je součástí šablony projektu.

> [!NOTE]
> `ProjectItem`Element přijímá různé atributy v závislosti na tom, zda je šablona určena pro projekt nebo položku. Toto téma vysvětluje `ProjectItem` prvek pro šablony projektů. Vysvětlení `ProjectItem` prvku pro šablony položek naleznete v tématu [element ProjectItem (šablony položek sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<ProjectItem>

## <a name="syntax"></a>Syntax

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

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy

| Atribut | Popis |
|---------------------| - |
| `TargetFileName` | Nepovinný atribut.<br /><br /> Určuje název a cestu položky projektu při vytvoření projektu ze šablony. Tento atribut je vhodný pro vytvoření adresářové struktury odlišné od struktury adresáře v souboru template *. zip* nebo pro vytvoření názvu položky pomocí nahrazení parametru. |
| `ReplaceParameters` | Nepovinný atribut.<br /><br /> Logická hodnota určující, zda má položka hodnoty parametrů, které musí být nahrazeny při vytvoření projektu ze šablony. Výchozí hodnota je `false` . |
| `OpenInEditor` | Nepovinný atribut.<br /><br /> Logická hodnota určující, zda má být položka otevřena v příslušném editoru v případě, že [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je projekt vytvořen ze šablony.<br /><br /> `OpenInWebBrowser`Atributy a `OpenInHelpBrowser` jsou ignorovány u položky s `OpenInEditor` hodnotou `true` .<br /><br /> Výchozí hodnota je `false`. |
| `OpenInWebBrowser` | Nepovinný atribut.<br /><br /> Logická hodnota určující, zda má být položka otevřena ve webovém prohlížeči při vytvoření projektu ze šablony.<br /><br /> Ve webovém prohlížeči lze otevřít pouze soubory HTML a textové soubory, které jsou místní pro projekt. Externí adresy URL nelze pomocí tohoto atributu otevřít.<br /><br /> Výchozí hodnota je `false`. |
| `OpenInHelpBrowser` | Nepovinný atribut.<br /><br /> Logická hodnota určující, zda má být položka otevřena v aplikaci Help Viewer při vytvoření projektu ze šablony.<br /><br /> V prohlížeči Help lze otevřít pouze soubory HTML a textové soubory, které jsou místní pro projekt. Externí adresy URL nelze pomocí tohoto atributu otevřít.<br /><br /> Výchozí hodnota je `false`. |
| `OpenOrder` | Nepovinný atribut.<br /><br /> Určuje číselnou hodnotu, která představuje pořadí, v jakém budou položky otevřeny v příslušných editorech. Všechny hodnoty musí být násobkem 10. Nejprve se otevřou položky s vyššími `OpenOrder` hodnotami. |

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Určuje soubory nebo adresáře, které se mají přidat do projektu.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 `string`Který představuje název nebo cestu k souboru v souboru template *. zip* .

## <a name="remarks"></a>Poznámky
 `ProjectItem`je volitelnou podřízenou položkou `Project` .

 `TargetFileName`Atribut lze použít k vytvoření struktury adresáře odlišnou od adresářové struktury v souboru template *. zip* . Například pokud soubor *MyFile. vb* existuje v kořenové složce souboru template *. zip* , ale chcete, aby se soubor umístil do adresáře s názvem *CustomFiles* ve všech projektech vytvořených ze šablony, použijte následující kód XML:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 `TargetFileName`Atribut lze také použít k přejmenování souborů, které v názvech souborů obsahují mezinárodní znaky. Například soubor template *. zip* nemůže obsahovat názvy souborů s znaky Unicode, takže soubor musí být přejmenován, aby mohl být zkomprimován do souboru *. zip* . `TargetFileName`Atribut se dá použít k nastavení názvu souboru zpátky na původní název souboru Unicode.

 `TargetFileName`Atribut lze také použít k přejmenování souborů s parametry. Následující postup vysvětluje, jak přejmenovat soubor *MyFile. vb*, který existuje v kořenovém adresáři souboru template *. zip* , na název souboru na základě názvu projektu.

### <a name="to-rename-files-with-parameters"></a>Přejmenování souborů s parametry

1. Použijte následující kód XML v souboru *. vstemplate* :

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Otevřete soubor projektu (*. vbproj* pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekt) v textovém editoru nebo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. Vyhledejte řádek v souboru projektu, který vypadá podobně jako následující kód XML:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Řádek kódu nahraďte následujícím kódem XML:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Při vytvoření projektu z této šablony bude název souboru založen na názvu, který uživatel zadal v dialogovém okně **Nový projekt** , přičemž byly odstraněny všechny nezabezpečené znaky a mezery. Další informace najdete v tématu [parametry šablony](../ide/template-parameters.md).

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro šablonu projektu pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikaci.

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

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [ProjectItem – element (šablony položek sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
