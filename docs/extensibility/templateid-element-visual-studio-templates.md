---
title: TemplateID – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o prvku TemplateID a o tom, jak Určuje identifikátor pro šablonu položky, která je zařazena do skupiny šablon položek pomocí elementu TemplateGroupID –.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 26a0b3ef90eab7cef51e5ca65032f2f4f68acd42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895320"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID – element (šablony sady Visual Studio)
Určuje identifikátor šablony položky, která je zařazena do skupiny šablon položek pomocí elementu [TemplateGroupID –](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

## <a name="syntax"></a>Syntax

```
<TemplateID> ... </TemplateID>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené elementy
 Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota
 `string`Který představuje identifikátor pro šablonu položky, která je zařazena do skupiny šablon položek podle `TemplateGroupID` prvku.

## <a name="remarks"></a>Poznámky
 `TemplateID` je volitelný prvek.

 Pokud soubor. vstemplate vynechává `TemplateID` prvek, pak se jako identifikátor šablony používá element [Name](../extensibility/name-element-visual-studio-templates.md) .

 Hodnota `TemplateID` prvku se používá společně s registrací systému projektu (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\ ) k filtrování šablon, které se zobrazí v dialogovém okně **Přidat novou položku** .

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
