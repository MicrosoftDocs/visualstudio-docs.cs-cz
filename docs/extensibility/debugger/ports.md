---
title: Porty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738297"
---
# <a name="ports"></a>Porty
V architektuře ladicího programu *port*:

- Je kontejner pro sadu procesů spuštěných na serveru. Port může například představovat připojení k systém Windows CEmu zařízení na základě sériového kabelu nebo síťového počítače, který není typu DCOM. Jeden speciální port nazvaný místní port obsahuje všechny procesy spuštěné v místním počítači.

- Může identifikovat podle názvu nebo identifikátoru.

- Může vytvořit výčet všech procesů spuštěných na portu a spustit a ukončit tyto procesy.

- Je reprezentován rozhraním [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , které je vytvořeno předáním argumentu [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) do [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje výchozí port, který zpracovává všechny procesy založené na Windows, a to jak nativní, tak i spravované. Pro připojení s externími zařízeními, která nejsou založená na systému Windows, musí být nastaven vlastní port. Chcete-li zadat vlastní porty, musíte také nastavit vlastního dodavatele portu.

## <a name="see-also"></a>Viz také
- [Servery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Procesy](../../extensibility/debugger/processes.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
