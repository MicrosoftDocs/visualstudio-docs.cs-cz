---
title: Přístavy | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738297"
---
# <a name="ports"></a>Porty
V architektuře ladicího programu *port*:

- Je kontejner pro sadu procesů spuštěných na serveru. Port může například představovat připojení k zařízení se systémem Windows CE pomocí sériového kabelu nebo k počítači bez dcom v síti. Jeden speciální port, nazývaný místní port, obsahuje všechny procesy spuštěné v místním počítači.

- Dokáže se identifikovat podle názvu nebo identifikátoru.

- Můžete vytvořit výčet všech procesů spuštěných na portu a spustit a ukončit tyto procesy.

- Je reprezentován [rozhraním IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) které je vytvořeno předáním argumentu [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) [addportu](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]poskytuje výchozí port, který zpracovává všechny procesy založené na systému Windows, nativní i spravované. Vlastní port musí být nastaven pro připojení s externími zařízeními, která nejsou založena na systému Windows. Chcete-li dodat takové vlastní porty, musíte také nastavit vlastního dodavatele portu.

## <a name="see-also"></a>Viz také
- [Servery](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Procesy](../../extensibility/debugger/processes.md)
- [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
