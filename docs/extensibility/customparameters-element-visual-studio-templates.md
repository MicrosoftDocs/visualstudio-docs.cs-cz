---
title: Element CustomParameters (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739418"
---
# <a name="customparameters-element-visual-studio-templates"></a>Element CustomParameters (šablony sady Visual Studio)
Seskupí vlastní parametry, které mají být předány průvodci šablonou, když průvodce provede nahrazení parametrů.

## <a name="syntax"></a>Syntaxe

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Obsahuje vlastní název parametru a hodnotu, která se má použít při vytvoření projektu nebo položky ze šablony. V prvku může `CustomParameter` být nula `CustomParameters` nebo více prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Určuje obsah šablony.|

## <a name="remarks"></a>Poznámky

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak používat několik vlastních parametrů v šabloně. Při vytvoření projektu nebo položky ze šablony s následujícími vlastními `$color2$` parametry budou všechny instance `Red` `Blue`souborů šablony nahrazeny `$color1$` a , resp.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Viz také
- [Element CustomParameter (šablony sady Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
