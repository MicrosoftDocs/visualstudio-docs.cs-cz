---
title: Přehled (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4269c620247f256d2cfae2e84b76ff60fcf9ba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738610"
---
# <a name="overview-debug-interface-access-sdk"></a>Přehled (Přístup k rozhraní ladění SDK)
Pro přístup k informacím o ladění společnosti Microsoft použijte DIA SDK. DIA SDK poskytuje sadu rozhraní API založenou na modelu COM, která eliminuje nutnost přepsat kód vždy, když Microsoft změní formát informací o ladění. DIA SDK také umožňuje číst z vybrané sady předchozích verzí informací o ladění, které jsou umístěny v souborech. pdb a. dbg vygenerovaných [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] verzích 5,0 a novějším.

 Každé rozhraní v DIA SDK představuje jiný objekt modelu COM, s výjimkou případů, kdy je uvedeno jinak. Další rozhraní, a proto jsou vytvořeny pomocí explicitních dotazů, jako je například [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) nebo [IDiaSession:: findChildren –](../../debugger/debug-interface-access/idiasession-findchildren.md), nikoli voláním `QueryInterface` na stávajících ukazatelích rozhraní.

## <a name="see-also"></a>Viz také:
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)