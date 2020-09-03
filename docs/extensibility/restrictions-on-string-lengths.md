---
title: Omezení délky řetězců | Microsoft Docs
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
ms.openlocfilehash: df6e068ba612d5e8876e4fa01fbc0751759d5a80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701477"
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
