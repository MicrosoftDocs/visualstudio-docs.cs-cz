---
title: Ověření grafického snímku | Microsoft Docs
description: Přečtěte si o nástroji pro ověřování snímků grafiky v aplikaci Visual Studio. Tento nástroj zobrazuje chyby a upozornění související se seznamem událostí.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fe9b1ed3acbe588b342ba6550bc45558a2070d2
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727642"
---
# <a name="graphics-frame-validation"></a>Ověření grafického snímku
<!-- VERSIONLESS -->
Visual Studio 2017 a vyšší podporují Nástroj pro **ověření snímků** .  V okně ověření rámce se zobrazí chyby a upozornění, která jsou přidružená k seznamu událostí.  Chcete-li zobrazit toto okno, vyberte nabídku **zobrazení > snímku** .

![Ověření snímku](media/gfx_diag_frame_validation.png)

Kliknutím na tlačítko **Spustit ověřování** v levém horním rohu spusťte analýzu.  Dokončení může trvat několik minut v závislosti na složitosti rámce.  Data, která se tady zobrazují, jsou kombinací dvou zdrojů: zprávy, které využívají rozhraní D3D, vygenerují, pokud jsou povolené [vrstvy SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) , a data shromažďovaná z vlastního interního sledování stavu nástroje. Po dokončení se zobrazí několik sloupců dat:

| **Sloupec** | **Popis** |
|------------| - |
| ID události | ID, které mapuje položku v okně [seznam událostí](graphics-event-list.md) . |
| Závažnost | Poškození, chyba, upozornění, informace nebo zpráva. |
| Kategorie | Definovaná aplikace, různé, inicializace, vyčištění, kompilace, vytvoření stavu, nastavení stavu, získání stavu, spuštění, manipulace s prostředky, shader, redundantní a nepoužívá se. |
| Zpráva | Zpráva přidružená k události |
| Událost | Událost přidružená k chybě nebo upozornění |

## <a name="see-also"></a>Viz také
[Diagnostika grafiky (Ladění grafiky DirectX)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->