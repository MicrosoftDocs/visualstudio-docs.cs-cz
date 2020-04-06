---
title: Element ProjectType (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d794bd5e81e77a892b5a3be38ff73ab805582dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701811"
---
# <a name="projecttype-element-visual-studio-templates"></a>Prvek ProjectType (šablony sady Visual Studio)
Zařadí šablonu projektu tak, aby se zobrazila pod zadanou skupinou v dialogovém okně **Nový projekt** nebo **Přidat novou položku.**

> [!WARNING]
> Šablony projektů jsou podporované pro C++ počínaje Visual Studio 2012. Nejsou podporovány pro C++ v sadě Visual Studio 2010 a starší verze.

 \<VSTemplate \<> TemplateData> \<> typu projektu

## <a name="syntax"></a>Syntaxe

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogovém **okně Nový projekt** nebo Přidat novou **položku.**|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Tato hodnota určuje typ projektu, který šablona vytvoří, a musí obsahovat jednu z následujících hodnot:

- `CSharp`: Určuje, že šablona [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] vytvoří projekt nebo položku.

- `VisualBasic`: Určuje, že šablona [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] vytvoří projekt nebo položku.

- `Web`: Určuje, že šablona vytvoří webový projekt nebo položku. Pokud `ProjectType` prvek obsahuje tuto hodnotu, jazyk projektu nebo položky je definován v [prvku ProjectSubType Element (Visual Studio Templates).](../extensibility/projectsubtype-element-visual-studio-templates.md)

## <a name="remarks"></a>Poznámky
 `ProjectType`je povinnýpodřízený `TemplateData`prvek .

 Hodnota prvku `ProjectType` určuje, kde se šablona nachází v dialogovém okně **Nový projekt** nebo **Přidat novou položku.** Například šablona s `ProjectType` hodnotou `CSharp` se zobrazí pod uzlem **Visual C#** v dialogovém okně Nový **projekt.**

 Podtyp šablony lze zadat pomocí prvku [ProjectSubType.](../extensibility/projectsubtype-element-visual-studio-templates.md)

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
            <ProjectItem>Form1.cs<ProjectItem>
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
- [Element ProjectSubType (šablony Sady Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
