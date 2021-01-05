---
title: Vlastní (Debug Interface Access SDK) | Microsoft Docs
description: Vyhledejte referenční informace o vlastních typech symbolů (identifikovaných pomocí značky SymTagCustom) v rozhraní ladění sady Visual Studio pro přístup.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Custom symbol
ms.assetid: a219fc83-d2a8-4bc5-b7e1-bfafeb247f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4bec65f766eee8bdf2c4ca34a2a801f26b7d69c
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728732"
---
# <a name="custom-debug-interface-access-sdk"></a>Vlastní (Přístup k rozhraní ladění SDK)
Některé kompilátory zavádí symboly, které nejsou identifikovány pomocí žádného ze standardních lexikálních typů symbolů. Tyto symboly jsou označeny `SymTagCustom` značkou.

## <a name="properties"></a>Vlastnosti
 V následující tabulce jsou uvedeny vlastnosti, které jsou platné pro tento typ symbolu.

|Vlastnost|Datový typ|Popis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|`BYTE`|Pole dat přidružené k symbolu.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagCustom` (jednu z hodnot [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="see-also"></a>Viz také
- [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)