---
title: Omezení délky | Microsoft Docs
description: Přečtěte si o omezeních délky řetězců používaných různými funkcemi, které jsou vynucované rozhraním API modulu plug-in správy zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7fd0d88a50f64aee1f0bc5c273d7a3cd50c6f53f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900249"
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
> Délka nezahrnuje ukončující . `null` Jiné konstanty s příponou "_SIZE" místo "_LEN" obsahují místo ukončující přípony `null` .

|Konstanta|Hodnota|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
