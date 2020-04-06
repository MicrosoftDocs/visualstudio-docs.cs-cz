---
title: Element TemplateGroupID (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699081"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID – element (šablony sady Visual Studio)
Určuje, v jakém projektu se šablony položek zobrazí. Tento prvek je významný, když je [hodnota ShowByDefault (šablony sady Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) nastavena na hodnotu `false`. Pokud je hodnota [ShowByDefault (Šablony sady Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) nastavena na `true`hodnotu , je šablona položky k dispozici ve všech typech projektů.

 \<VSTemplate \<> TemplateData> \<TemplateGroupID>

## <a name="syntax"></a>Syntaxe

```
<TemplateGroupID> ... </TemplateGroupID>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené elementy
 Žádné.

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogovém **okně Nový projekt** nebo Přidat novou **položku.**|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text určuje identifikátor pro kategorii šablon položek.

## <a name="remarks"></a>Poznámky
 `TemplateGroupID`je prvek.

 Hodnota `TemplateGroupID` prvku se používá společně s registrací systému projektu (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<číslo verze>* \Projekty\\) pro filtrování šablon, které se zobrazí v dialogovém okně Přidat novou **položku.**

|Vizuální hodnota C++|Význam|
|------------------------|-------------|
|VC-nativní|Používá se pro nativní projekty. Také výchozí, pokud nelze určit typ projektu.|
|Spravované vv|Používá se pro řízené (/clr) projekty|
|VC-Windows|Používá se pro všechny projekty, které cílí na platformu Windows (nativní/spravované/úložiště)|
|WinRT-Nativní-UAP|Používá se pro projekty obchodu s Windows 10|
|CodeSharing-Nativní|Používá se pro projekty sdílených položek|
|WinRT-Nativní-6,3|Používá se pro projekty windows 8.1 Store|
|WinRT-Nativní-Telefon-6,3|Používá se pro projekty windows phone 8.1|
|WinRT-Nativní|Používá se pro projekty Windows 8.0 Store|
|VC-Android|Používá se pro projekty Android|

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
