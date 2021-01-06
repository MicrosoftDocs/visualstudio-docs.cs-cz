---
title: Kódy zpráv | Microsoft Docs
description: Naučte se význam kódů zpráv zobrazených na jednotlivých řádcích zpráv v zobrazení zpráv.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4b836a5d4c1faad6b4c0375e2ec51d759816889
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903607"
---
# <a name="message-codes"></a>Kódy zpráv
Každá čára zprávy zobrazená v [zobrazení zprávy](../debugger/messages-view.md) obsahuje kód P, 's, ', ' nebo R '. Tyto kódy mají následující význam:

|Kód|Význam|
|----------|-------------|
|P|Zpráva byla odeslána do fronty pomocí funkce **PostMessage** . Nejsou k dispozici žádné informace týkající se konečné dispozice zprávy.|
|S|Zpráva byla odeslána pomocí funkce **SendMessage** . To znamená, že odesílatel nezíská řízení, dokud příjemce nevrátí zprávu. Příjemce může proto předat návratovou hodnotu zpět odesílateli.|
|s|Zpráva byla odeslána, ale zabezpečení brání přístupu k vrácené hodnotě.|
|R|Každý řádek má odpovídající řádek R (Return), který vypisuje vrácenou hodnotu zprávy. Někdy jsou volání zpráv vnořená, což znamená, že jedna obslužná rutina zprávy pošle další zprávu.|