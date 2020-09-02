---
title: TemplateGroupID – – element (šablony sady Visual Studio) | Microsoft Docs
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
ms.openlocfilehash: affc324418e3745f85fb0b91a0ef7abda0ab28b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699081"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID – element (šablony sady Visual Studio)
Určuje, v jakém typu projektu se budou šablony položek zobrazovat. Tento prvek je významný, pokud je [ShowByDefault (šablony sady Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) nastaveny na `false` . Když je [ShowByDefault (šablony sady Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) nastaveno na `true` , je šablona položky k dispozici ve všech typech projektů.

 \<VSTemplate> \<TemplateData>
 \<TemplateGroupID>

## <a name="syntax"></a>Syntax

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

 Hodnota `TemplateGroupID` elementu se používá společně s registrací systému projektu (HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio \\ *\<version number>* \Projects \\ ) k filtrování šablon, které se zobrazí v dialogovém okně **Přidat novou položku** .

|Hodnota Visual C++|Význam|
|------------------------|-------------|
|VC – nativní|Používá se pro nativní projekty. Také výchozí, pokud nelze určit typ projektu.|
|Spravované VC|Používá se pro spravované projekty (/CLR).|
|VC – Windows|Používá se pro všechny projekty, které cílí na platformu Windows (nativní/spravovaná/Store).|
|WinRT – nativní – UAP|Používá se pro projekty Windows 10 Store.|
|CodeSharing – nativní|Používá se pro projekty sdílených položek.|
|WinRT – nativní-6,3|Používá se pro projekty Windows 8.1 Storu.|
|WinRT – nativní – telefon – 6,3|Používá se pro projekty Windows Phone 8,1.|
|WinRT – nativní|Používá se pro projekty Windows 8,0 Store.|
|VC – Android|Používá se pro projekty Androidu.|

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
