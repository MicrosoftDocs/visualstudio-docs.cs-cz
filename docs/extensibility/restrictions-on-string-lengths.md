---
title: Omezení délky řetězců | Microsoft Docs
description: Přečtěte si o omezení délky řetězců používaných různými funkcemi, které jsou uložené v rozhraní API modulu plug-in správy zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5412e930937d029f803f5c6c2b4ddc9d396d9485
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715519"
---
# <a name="restrictions-on-string-lengths"></a>Omezení délky řetězců
Rozhraní API modulu plug-in správy zdrojového kódu omezuje délky řetězců používané v různých funkcích.

## <a name="string-length-values"></a>Hodnoty délky řetězce

|Konstanta|Hodnota|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> Délka nezahrnuje ukončení `null` . Jiné konstanty s příponou "_SIZE" místo "_LEN" obsahují místo pro ukončení `null` .

|Konstanta|Hodnota|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
