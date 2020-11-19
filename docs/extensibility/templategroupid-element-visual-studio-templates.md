---
title: TemplateGroupID – – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o prvku TemplateGroupID – a o tom, jak určuje, na jaký druh projektu se šablony položek budou zobrazovat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5f7d30036f0f25d1f81b690168675d74fc36bbd
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903218"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID – element (šablony sady Visual Studio)
Určuje, v jakém typu projektu se budou šablony položek zobrazovat. Tento prvek je významný, pokud je [ShowByDefault (šablony sady Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) nastaveny na `false` . Když je [ShowByDefault (šablony sady Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) nastaveno na `true` , je šablona položky k dispozici ve všech typech projektů.

 \<VSTemplate> \<TemplateData>
 \<TemplateGroupID>

## <a name="syntax"></a>Syntaxe

```
<TemplateGroupID> ... </TemplateGroupID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text určuje identifikátor pro kategorii šablon položek.

## <a name="remarks"></a>Poznámky
 `TemplateGroupID` je element.

 Hodnota `TemplateGroupID` elementu se používá společně s registrací systému projektu (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<version number>* \Projects \\ ) pro filtrování šablon, které se zobrazí v dialogovém okně **Přidat novou položku** .

|Hodnota Visual C++|Význam|
|------------------------|-------------|
|VC-Native|Používá se pro nativní projekty. Také výchozí, pokud nelze určit typ projektu.|
|VC-Managed|Používá se pro spravované projekty (/CLR).|
|VC-Windows|Používá se pro všechny projekty, které cílí na platformu Windows (nativní/spravovaná/Store).|
|WinRT – nativní – UAP|Používá se pro projekty Windows 10 Store.|
|CodeSharing-Native|Používá se pro projekty sdílených položek.|
|WinRT – nativní-6,3|Používá se pro projekty Windows 8.1 Storu.|
|WinRT – nativní – telefon – 6,3|Používá se pro projekty Windows Phone 8,1.|
|WinRT-Native|Používá se pro projekty Windows 8,0 Store.|
|VC-Android|Používá se pro projekty Androidu.|

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
