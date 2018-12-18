---
title: Povolení ladění programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad6e8e9cb8dd34e3cd084bde1eb94ff5774dd4ba
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204385"
---
# <a name="enable-a-program-to-be-debugged"></a>Povolit program k ladění
Předtím, než vaše ladicího stroje (DE) můžete ladit program, musí nejdřív spustit DE nebo připojit k existující program.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Získání portu](../../extensibility/debugger/getting-a-port.md)  
 Popisuje, jak získat port jako první krok k povolení ladění programu.  
  
 [Registrace programu](../../extensibility/debugger/registering-the-program.md)  
 Vysvětluje povolení ladění programu na další krok: registrace s portem. Po registraci do programu můžete ladit buď tak, že proces připojení nebo ladění just-in-time (JIT).  
  
 [Připojit k programu](../../extensibility/debugger/attaching-to-the-program.md)  
 Popisuje dál: připojování ladicího programu k programu.  
  
 [Připojení založená na spuštění](../../extensibility/debugger/launch-based-attachment.md)  
 Popisuje přílohu spuštění programu, který je automaticky při spuštění pomocí SDM.  
  
 [Odesílání požadovaných událostí](../../extensibility/debugger/sending-the-required-events.md)  
 Provede požadované události při vytváření ladicího stroje (DE) a připojení k programu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definuje ladicího stroje (DE) a jsou popsány služby implementované pomocí rozhraní DE a jak může způsobit přechod mezi různé provozní režimy ladicí program.