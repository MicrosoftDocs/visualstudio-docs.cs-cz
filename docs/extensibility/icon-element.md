---
title: Element Icon | Microsoft Docs
description: Přečtěte si o elementu Icon, který představuje ikony používané v rozšířeních IDE sady Visual Studio, které obsahuje atributy pro použitou bitmapu a slot v rastrovém obrazovém pruhu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ad5bfdf000232ef92a9e9a27b12152df36a4335
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900821"
---
# <a name="icon-element"></a>Element Icon
Atribut GUID značky Icon je identifikátor GUID definované bitmapy. `id`Atribut vybere slot v rastrovém obrázku. Tento element je volitelný. Pokud tento prvek není zahrnut, hodnota **guidOfficeIcon: msotcidNoIcon** bude předpokládaná.

## <a name="syntax"></a>Syntax

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota. Identifikátor GUID definované bitmapy.|
|id|Povinná hodnota. Vybere slot v rastrovém obrázku.|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Žádné|Žádné|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Buttons – Element](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
