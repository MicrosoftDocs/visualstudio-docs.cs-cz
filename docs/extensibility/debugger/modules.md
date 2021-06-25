---
title: Moduly | Microsoft Docs
description: Tento článek popisuje definici a roli modulu v architektuře ladicího programu v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 03a3ad588b0a2e0f3aa6f04ddeb742ab66064bc9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902602"
---
# <a name="modules"></a>Moduly
Z hlediska architektury ladicího programu *modul*:

- Je fyzický kontejner kódu, například spustitelný soubor nebo knihovna DLL.

- Může znovu načíst jeho symboly a popsat sám sebe. Popisy modulů se zobrazují v okně Moduly integrovaného vývojového prostředí (IDE).

- Je reprezentováno [rozhraním IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) vytvořeným ladicím modulem pro popis modulu.

## <a name="see-also"></a>Viz také
- [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
