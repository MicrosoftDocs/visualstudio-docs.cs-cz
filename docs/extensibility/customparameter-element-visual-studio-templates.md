---
title: Element CustomParameter (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9063a354f03b896e189566e8d84a18caf7509db8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739426"
---
# <a name="customparameter-element-visual-studio-templates"></a>Element CustomParameter (šablony sady Visual Studio)
Obsahuje vlastní název parametru a hodnotu, která se má použít při vytvoření projektu nebo položky ze šablony.

## <a name="syntax"></a>Syntaxe

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Povinná hodnota. Název parametru Formát parametrů je $*name*$.|
|`Value`|Povinná hodnota. Hodnota nahrazení parametru.|

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Seskupí vlastní parametry, které mají být předány průvodci šablonou, když průvodce provede nahrazení parametrů.|

## <a name="remarks"></a>Poznámky
 Pokud šablona `CustomParameter` obsahuje prvky, každá instance `Name` `Value` atributu je nahrazen atributem v vytvořeném projektu nebo souborech položek.

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak používat několik vlastních parametrů v šabloně. Při vytvoření projektu nebo položky ze šablony s následujícími vlastními `$color2$` parametry budou všechny instance `Red` `Blue`souborů šablony nahrazeny `$color1$` a , resp.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Viz také
- [Element CustomParameters (šablony sady Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
