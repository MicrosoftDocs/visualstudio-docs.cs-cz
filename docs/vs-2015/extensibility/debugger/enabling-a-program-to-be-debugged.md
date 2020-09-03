---
title: Povolení ladění programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0f0331430a1cc625dee2a7029742fd62d67fb56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155366"
---
# <a name="enabling-a-program-to-be-debugged"></a>Povolení ladění programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Předtím, než může ladit program (DE), je nutné nejprve spustit příkaz DE nebo ho připojit k existujícímu programu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Získání portu](../../extensibility/debugger/getting-a-port.md)  
 Tento článek popisuje, jak získat port jako první krok, který umožňuje ladit program.  
  
 [Registrace programu](../../extensibility/debugger/registering-the-program.md)  
 Vysvětluje další krok při povolování ladění programu: registrace pomocí portu. Po registraci je možné program ladit buď procesem připojení, nebo laděním JIT (just-in-time).  
  
 [Připojení k programu](../../extensibility/debugger/attaching-to-the-program.md)  
 Vysvětluje další krok: připojení ladicího programu k programu.  
  
 [Připojení založené na spuštění](../../extensibility/debugger/launch-based-attachment.md)  
 Popisuje spuštění přiloženého programu k programu, který je automaticky spouštěn při spuštění ve službě SDM.  
  
 [Odesílání požadovaných událostí](../../extensibility/debugger/sending-the-required-events.md)  
 Provede kroky popsané v části požadované události při vytváření ladicího stroje (DE) a jeho připojení k programu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definuje ladicí modul (DE) a popisuje služby implementované prostřednictvím rozhraní DE a způsob, jakým může ladicí program přecházet mezi různými provozními režimy.
