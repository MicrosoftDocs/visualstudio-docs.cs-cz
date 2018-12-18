---
title: Kódy zpráv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25b2061d9f20da8e9c4d5b4f9794f400d638260c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474440"
---
# <a name="message-codes"></a>Kódy zpráv
Každý řádek zprávy uvedené v [zobrazení zpráv](../debugger/messages-view.md) obsahuje "P", je, "na,' nebo 'R' kódu. Tyto kódy mají následující významy:  
  
|Kód|Význam|  
|----------|-------------|  
|P|Zpráva byla odeslána do fronty s **zpravy** funkce. Nejsou dostupné, ultimate dispozice zprávy týkající se žádné informace.|  
|S|Zpráva byla odeslána s **SendMessage** funkce. To znamená, že odesílatel nemá znovu získat kontrolu dokud příjemce zpracuje a vrátí zprávu. Příjemce může, tedy předat návratovou hodnotu zpět odesílatele.|  
|s|Zpráva byla odeslána, ale zabezpečení brání přístupu k návratovou hodnotu.|  
|R|Pro každý ' řádek obsahuje odpovídající řádek "R" (vrátit), který uvádí zprávy návratovou hodnotu. V některých případech jsou vnořeny volání zpráva, což znamená, že tuto obslužnou rutinu jednu zprávu odešle další zprávu.|