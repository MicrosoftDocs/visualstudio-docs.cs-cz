---
title: ProjectItem – element (šablony položek sady Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 885d0fbb50204f23a30fa43c1ffad45c9d67f829
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770726"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem – element (šablony položek sady Visual Studio)
Určuje soubor, který je součástí šablony položky.

> [!NOTE]
> `ProjectItem`Element přijímá různé atributy v závislosti na tom, zda je šablona určena pro projekt nebo položku. Toto téma vysvětluje `ProjectItem` prvek pro položku. Vysvětlení `ProjectItem` prvku pro šablony projektů naleznete v tématu [element ProjectItem (šablony projektů sady Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<ProjectItem>

## <a name="syntax"></a>Syntax

```
<ProjectItem
    SubType="Form/Component/CustomControl/UserControl"
    CustomTool="string"
    ItemType="string"
    ReplaceParameters="true/false"
    TargetFileName="TargetFileName.ext">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy

| Atribut | Popis |
|---------------------| - |
| `SubType` | Nepovinný atribut.<br /><br /> Určuje podtyp položky v šabloně položky s více soubory. Tato hodnota se používá k určení editoru, který [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bude použit k otevření položky. |
| `CustomTool` | Nepovinný atribut.<br /><br /> Nastaví CustomTool pro položku v souboru projektu. |
| `ItemType` | Nepovinný atribut.<br /><br /> Nastaví typ ItemType pro položku v souboru projektu. |
| `ReplaceParameters` | Nepovinný atribut.<br /><br /> Logická hodnota určující, zda má položka hodnoty parametrů, které musí být nahrazeny při vytvoření projektu ze šablony. Výchozí hodnota je `false` . |
| `TargetFileName` | Nepovinný atribut.<br /><br /> Určuje název položky, která je vytvořena ze šablony. Tento atribut je vhodný pro použití nahrazení parametru pro vytvoření názvu položky. |

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Určuje obsah šablony.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 `string`Který představuje název souboru v souboru template *. zip* .

## <a name="remarks"></a>Poznámky
 `ProjectItem`je volitelnou podřízenou položkou `TemplateContent` .

 `TargetFileName`Atribut lze použít k přejmenování souborů s parametry. Například pokud soubor *MyFile. vb* existuje v kořenovém adresáři souboru template *. zip* , ale chcete soubor pojmenovat na základě názvu souboru zadaného uživatelem v dialogovém okně **Přidat novou položku** , použijte následující kód XML:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Při vytvoření položky z této šablony bude název souboru založen na názvu, který uživatel zadal v dialogovém okně **Přidat novou položku** . To je užitečné při vytváření šablon položek s více soubory. Další informace najdete v tématu [Postupy: vytváření šablon položek](../ide/how-to-create-multi-file-item-templates.md) a [parametrů šablony](../ide/template-parameters.md)s více soubory.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro standardní šablonu položky pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] třídu.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postupy: vytváření šablon položek s více soubory](../ide/how-to-create-multi-file-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
