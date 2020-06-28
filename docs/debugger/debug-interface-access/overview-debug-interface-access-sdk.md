---
title: Přehled (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 7a403a8d3ddec82ce7e051e545687511c2421fa9
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461166"
---
# <a name="overview-debug-interface-access-sdk"></a>Přehled (Přístup k rozhraní ladění SDK)
Pro přístup k informacím o ladění společnosti Microsoft použijte DIA SDK. DIA SDK poskytuje sadu rozhraní API založenou na modelu COM, která eliminuje nutnost přepsat kód vždy, když Microsoft změní formát informací o ladění. DIA SDK také umožňuje číst z vybrané sady předchozích verzí ladicích informací, které jsou umístěny v souborech. pdb a. dbg vygenerovaných [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] verzemi 5,0 a novějšími.

 Každé rozhraní v DIA SDK představuje jiný objekt modelu COM, s výjimkou případů, kdy je uvedeno jinak. Další rozhraní a tedy další objekty jsou vytvořeny pomocí explicitních dotazů, jako je například [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) nebo [IDiaSession:: findChildren –](../../debugger/debug-interface-access/idiasession-findchildren.md), nikoli voláním `QueryInterface` na existující ukazatele rozhraní.

## <a name="see-also"></a>Viz také
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)