---
title: Kódy zpráv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92cc911b0217a406302553b3d913c032fc915b4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182966"
---
# <a name="message-codes"></a>Kódy zpráv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Každá čára zprávy zobrazená v [zobrazení zprávy](../debugger/messages-view.md) obsahuje kód P, 's, ', ' nebo R '. Tyto kódy mají následující význam:  
  
|Kód|Význam|  
|----------|-------------|  
|P|Zpráva byla odeslána do fronty pomocí funkce **PostMessage** . Nejsou k dispozici žádné informace týkající se konečné dispozice zprávy.|  
|S|Zpráva byla odeslána pomocí funkce **SendMessage** . To znamená, že odesílatel nezíská řízení, dokud příjemce nevrátí zprávu. Příjemce může proto předat návratovou hodnotu zpět odesílateli.|  
|s|Zpráva byla odeslána, ale zabezpečení brání přístupu k vrácené hodnotě.|  
|R|Každý řádek má odpovídající řádek R (Return), který vypisuje vrácenou hodnotu zprávy. Někdy jsou volání zpráv vnořená, což znamená, že jedna obslužná rutina zprávy pošle další zprávu.|
