---
title: CustomDataSignature – – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o prvku CustomDataSignature – a o tom, jak určuje signaturu textu pro vyhledání vlastních dat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0b2442e7b254ccaaf9e890b5370f712b5715f18
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671516"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>CustomDataSignature – – element (šablony sady Visual Studio)
Určuje podpis textu pro vyhledání vlastních dat.

 \<VSTemplate> \<TemplateData>
 \<CustomDataSignature>

## <a name="syntax"></a>Syntax

```
<CustomDataSignature>"string"</CustomDataSignature>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text je řetězec s podpisem textu, který je požadován k vyhledání vlastních dat.

## <a name="remarks"></a>Poznámky
 `CustomDataSignature` je volitelný prvek.

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
