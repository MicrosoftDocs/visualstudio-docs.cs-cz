---
title: CustomParameters – – element (šablony sady Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739418"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters – – element (šablony sady Visual Studio)
Seskupí vlastní parametry, které mají být předány Průvodci šablonou, když průvodce provede nahrazení parametru.

## <a name="syntax"></a>Syntax

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Obsahuje název vlastního parametru a hodnotu, která se má použít, když se v šabloně vytvoří projekt nebo položka. Element může obsahovat nula nebo více `CustomParameter` prvků `CustomParameters` .|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Určuje obsah šablony.|

## <a name="remarks"></a>Poznámky

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít několik vlastních parametrů v šabloně. Když je vytvořen projekt nebo položka ze šablony s následujícími vlastními parametry, všechny instance `$color1$` a `$color2$` v souborech šablon budou nahrazeny řetězcem `Red` a v `Blue` uvedeném pořadí.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Viz také
- [CustomParameter – – element (šablony sady Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
