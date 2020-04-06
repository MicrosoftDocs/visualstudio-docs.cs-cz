---
title: Element ProjectItem (šablony položek sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: 6826440ed12e90f1ffced63dfef45bb3d86177ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701864"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Element ProjectItem (šablony položek sady Visual Studio)
Určuje soubor, který je součástí šablony položky.

> [!NOTE]
> Prvek `ProjectItem` přijímá různé atributy v závislosti na tom, zda je šablona pro projekt nebo položku. Toto téma `ProjectItem` vysvětluje prvek pro položku. Vysvětlení prvku pro `ProjectItem` šablony projektu naleznete v tématu [ProjectItem element (Šablony projektu Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).

 \<VSTemplate \<> TemplateContent> \<položku projektu>

## <a name="syntax"></a>Syntaxe

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

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy

| Atribut | Popis |
|---------------------| - |
| `SubType` | Nepovinný atribut.<br /><br /> Určuje podtyp položky v šabloně vícesouborové položky. Tato hodnota se používá k [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] určení editoru, který se použije k otevření položky. |
| `CustomTool` | Nepovinný atribut.<br /><br /> Nastaví Nástroj CustomTool pro položku v souboru projektu. |
| `ItemType` | Nepovinný atribut.<br /><br /> Nastaví ItemType pro položku v souboru projektu. |
| `ReplaceParameters` | Nepovinný atribut.<br /><br /> Logická hodnota, která určuje, zda má položka hodnoty parametrů, které musí být nahrazeny při vytvoření projektu ze šablony. Výchozí hodnota `false`je . |
| `TargetFileName` | Nepovinný atribut.<br /><br /> Určuje název položky, která je vytvořena ze šablony. Tento atribut je užitečný pro použití nahrazení parametru k vytvoření názvu položky. |

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Určuje obsah šablony.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 A, `string` který představuje název souboru v souboru *.zip* šablony.

## <a name="remarks"></a>Poznámky
 `ProjectItem`je volitelné dítě `TemplateContent`.

 Atribut `TargetFileName` lze použít k přejmenování souborů s parametry. Pokud například soubor *MyFile.vb* existuje v kořenovém adresáři souboru *ZIP* šablony, ale chcete, aby byl soubor pojmenován na základě názvu souboru poskytnutého uživatelem v dialogovém okně Přidat **novou položku,** použijte následující xml:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Když je položka vytvořena z této šablony, bude název souboru založen na názvu, který uživatel zadal v dialogovém okně **Přidat novou položku.** To je užitečné při vytváření šablon vícesouborových položek. Další informace naleznete v [tématu Postup: Vytvoření šablon vícesouborových položek](../ide/how-to-create-multi-file-item-templates.md) a [parametrů šablony](../ide/template-parameters.md).

## <a name="example"></a>Příklad
 Následující příklad ilustruje metadata pro šablonu standardní [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] položky pro třídu.

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

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postup: Vytvoření šablon vícesouborových položek](../ide/how-to-create-multi-file-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
