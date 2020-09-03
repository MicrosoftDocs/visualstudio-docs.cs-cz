---
title: Moduly | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738344"
---
# <a name="modules"></a>Moduly
V podobě architektury ladicího programu *modul*:

- Je fyzický kontejner kódu, jako je spustitelný soubor nebo knihovna DLL.

- Může znovu načíst své symboly a popsat sebe sama. Popisy modulů jsou zobrazeny v okně moduly rozhraní IDE.

- Je reprezentován rozhraním [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) vytvořeným ladicím modulem, který popisuje modul.

## <a name="see-also"></a>Viz také
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
