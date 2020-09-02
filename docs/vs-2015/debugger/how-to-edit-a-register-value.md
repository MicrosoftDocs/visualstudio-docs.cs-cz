---
title: 'Postupy: Úprava hodnoty registru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7f0cd04b054d51119f6f6c1b0275c4f781656bff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811954"
---
# <a name="how-to-edit-a-register-value"></a>Postupy: Úprava hodnoty registru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno Registry je k dispozici pouze v případě, že je povoleno ladění na úrovni adresy v dialogovém okně **Možnosti** , uzel **ladění** .  
  
### <a name="to-change-the-value-of-a-register"></a>Změna hodnoty registru  
  
1. V okně **Registry** pomocí klávesy TAB nebo myši přesuňte kurzor na hodnotu, kterou chcete změnit. Když začnete psát, ukazatel se musí nacházet před hodnotou, kterou chcete přepsat.  
  
2. Zadejte novou hodnotu.  
  
    > [!CAUTION]
    > Změna hodnot registru (zejména v registrech EIP a EBP) může ovlivnit spuštění programu.  
  
    > [!CAUTION]
    > Úpravy hodnot s plovoucí desetinnou čárkou mohou díky převodu komponenty zlomku z desítkové do binární soustavy způsobit drobné nepřesnosti. Dokonce i zdánlivě neškodného úpravy můžou mít za následek změny některých nejméně významných bitů v registru s plovoucí desetinnou čárkou.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití okna Registry](../debugger/how-to-use-the-registers-window.md)
