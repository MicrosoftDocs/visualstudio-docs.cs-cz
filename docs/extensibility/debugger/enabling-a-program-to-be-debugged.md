---
title: Povolení ladění programu | Microsoft Docs
description: Přečtěte si, jak spustit ladicí stroj nebo připojit ladicí stroj k existujícímu programu pro ladění programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4ed7ce97e6ff7e8801953877ed80afa7ca262f20
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097224"
---
# <a name="enable-a-program-to-be-debugged"></a>Povolit ladění programu
Předtím, než může ladit program (DE), je nutné nejprve spustit příkaz DE nebo ho připojit k existujícímu programu.

## <a name="in-this-section"></a>V této části
 [Získat port](../../extensibility/debugger/getting-a-port.md) Tento článek popisuje, jak získat port jako první krok, který umožňuje ladit program.

 [Zaregistrovat program](../../extensibility/debugger/registering-the-program.md) Vysvětluje další krok při povolování ladění programu: registrace pomocí portu. Po registraci je možné program ladit buď procesem připojení, nebo laděním JIT (just-in-time).

 [Připojit k programu](../../extensibility/debugger/attaching-to-the-program.md) Vysvětluje další krok: připojení ladicího programu k programu.

 [Připojení založené na spuštění](../../extensibility/debugger/launch-based-attachment.md) Popisuje spuštění přiloženého programu k programu, který je automaticky spouštěn při spuštění ve službě SDM.

 [Odeslat požadované události](../../extensibility/debugger/sending-the-required-events.md) Provede kroky popsané v části požadované události při vytváření ladicího stroje (DE) a jeho připojení k programu.

## <a name="related-sections"></a>Související oddíly
 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md) Definuje ladicí modul (DE) a popisuje služby implementované prostřednictvím rozhraní DE a způsob, jakým může ladicí program přecházet mezi různými provozními režimy.
