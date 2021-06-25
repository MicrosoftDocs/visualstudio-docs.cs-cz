---
title: Porty | Microsoft Docs
description: Tento článek popisuje definici a roli portu v architektuře ladicího programu v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e53b2b804433f7e9450f34dac5b21e45710cd71c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900769"
---
# <a name="ports"></a>Porty
V architektuře ladicího programu *port*:

- Je kontejner pro sadu procesů spuštěných na serveru. Port může například představovat připojení k zařízení založenému systém Windows CE pomocí sériového kabelu nebo síťového počítače bez modelu DCOM. Jeden speciální port, který se nazývá místní port, obsahuje všechny procesy spuštěné na místním počítači.

- Může se identifikovat podle názvu nebo identifikátoru.

- Může vytvořit výčet všech procesů spuštěných na portu a tyto procesy spustit a ukončit.

- Je reprezentováno [rozhraním IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) které je vytvořeno předáním argumentu [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) do [addPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje výchozí port, který zpracovává všechny nativní i spravované procesy systému Windows. Pro připojení k externím zařízením, která nejsou založená na Windows, musí být nastavený vlastní port. Pokud chcete zadat takové vlastní porty, musíte také nastavit vlastního dodavatele portů.

## <a name="see-also"></a>Viz také
- [Servery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Procesy](../../extensibility/debugger/processes.md)
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
