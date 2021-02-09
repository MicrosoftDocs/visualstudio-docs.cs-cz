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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a3fb8d56ca4df9912862346e5b096b2bb5414881
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862316"
---
# <a name="overview-debug-interface-access-sdk"></a>Přehled (Přístup k rozhraní ladění SDK)
Pro přístup k informacím o ladění společnosti Microsoft použijte DIA SDK. DIA SDK poskytuje sadu rozhraní API založenou na modelu COM, která eliminuje nutnost přepsat kód vždy, když Microsoft změní formát informací o ladění. DIA SDK také umožňuje číst z vybrané sady předchozích verzí ladicích informací, které jsou umístěny v souborech. pdb a. dbg vygenerovaných [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] verzemi 5,0 a novějšími.

 Každé rozhraní v DIA SDK představuje jiný objekt modelu COM, s výjimkou případů, kdy je uvedeno jinak. Další rozhraní a tedy další objekty jsou vytvořeny pomocí explicitních dotazů, jako je například [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) nebo [IDiaSession:: findChildren –](../../debugger/debug-interface-access/idiasession-findchildren.md), nikoli voláním `QueryInterface` na existující ukazatele rozhraní.

## <a name="see-also"></a>Viz také
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)