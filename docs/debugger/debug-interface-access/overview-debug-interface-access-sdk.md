---
title: Přehled (přístup k rozhraní ladění SDK) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 807690edaf5626e3ec007a005717622592c14ce9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471437"
---
# <a name="overview-debug-interface-access-sdk"></a>Přehled (Přístup k rozhraní ladění SDK)
Použijte pro přístup k informacím ladění Microsoft DIA SDK. DIA SDK poskytuje že com na základě sada rozhraní API, která eliminuje nutnost přepisu kódu při každé změně formát ladicích informací společnosti Microsoft. DIA SDK vám umožní číst z vyberte sadu předchozích verzích informace o ladění, umístěný v PDB a dbg soubory generované [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] verze 5.0 a novější.  
  
 Každé rozhraní v sadě DIA SDK představuje jiný objekt COM, s výjimkou, kde je uvedeno jinak. Další rozhraní a proto další objekty, jsou vytvořeny pomocí explicitní dotazy, jako například [idiadatasource::opensession –](../../debugger/debug-interface-access/idiadatasource-opensession.md) nebo [idiasession::findchildren –](../../debugger/debug-interface-access/idiasession-findchildren.md), nikoli voláním `QueryInterface` na existující ukazatele rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Idiadatasource::opensession –](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)