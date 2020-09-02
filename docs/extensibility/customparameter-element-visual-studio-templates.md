---
title: CustomParameter – – element (šablony sady Visual Studio) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739426"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter – – element (šablony sady Visual Studio)
Obsahuje název vlastního parametru a hodnotu, která se má použít, když se v šabloně vytvoří projekt nebo položka.

## <a name="syntax"></a>Syntax

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Povinná hodnota. Název parametru Formát pro parametry je $*název*$.|
|`Value`|Povinná hodnota. Nahrazující hodnota pro parametr.|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Seskupí vlastní parametry, které mají být předány Průvodci šablonou, když průvodce provede nahrazení parametru.|

## <a name="remarks"></a>Poznámky
 Pokud šablona obsahuje `CustomParameter` prvky, každá instance `Name` je nahrazena `Value` atributem v souboru vytvořeného projektu nebo položky.

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít několik vlastních parametrů v šabloně. Když je vytvořen projekt nebo položka ze šablony s následujícími vlastními parametry, všechny instance `$color1$` a `$color2$` v souborech šablon budou nahrazeny řetězcem `Red` a v `Blue` uvedeném pořadí.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Viz také
- [CustomParameters – – element (šablony sady Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
