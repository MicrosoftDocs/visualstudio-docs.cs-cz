---
title: Příloha na základě spuštění | Microsoft Docs
description: Přečtěte si o připojení na základě spouštěcích programů k programu, který je automaticky a následuje po cestě, jako je například ruční příloha.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97bbc098e766a1025c372ff35c5849bfe652649f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904331"
---
# <a name="launch-based-attachment"></a>Příloha na základě spuštění
Příloha založená na spouštění programu je automatická. V případě, že je proces hostující program spuštěný pomocí modelu SDM, je příloha založená na spuštění následující jako cesta podobná metodě ručního připojení. Informace najdete v tématu věnovaném [připojení k programu](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Proces připojení
 Hlavním rozdílem je posloupnost událostí za voláním **připojení** , a to následujícím způsobem:

1. Odešle objekt události **IDebugEngineCreateEvent2** do SDM. Podrobnosti najdete v tématu [odeslání událostí](../../extensibility/debugger/sending-events.md).

2. Zavolejte `IDebugProgram2::GetProgramId` metodu na rozhraní **IDebugProgram2** předané metodě **Attach** .

3. Odešle objekt události **IDebugProgramCreateEvent2** , který oznamuje službě SDM, že byl vytvořen místní objekt **IDebugProgram2** , který reprezentuje program do de.

4. Odešle objekt události [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) , který oznamuje SDM, že se pro proces, který se spustil, vytvoří nové vlákno.

## <a name="see-also"></a>Viz také
- [Odeslat požadované události](../../extensibility/debugger/sending-the-required-events.md)
- [Povolit ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
