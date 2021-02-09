---
title: Časy přemýšlení pro zátěžové testování
description: Naučte se, jak upravit čas pomýšlení, který simuluje lidské chování, které lidem vynutí, aby mezi interakcemi s webem čekali.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 0c6dc458fed9f03a4b9176817e243dca3a048b4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887845"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Úprava časů pomýšlení pro simulaci zpoždění lidské interakce webu ve scénářích zátěžových testů

Časy přemýšlení se používají k simulaci lidského chování, které způsobuje, že lidé budou mezi interakcemi s webem čekat. Časy přemýšlení mezi požadavky v testu výkonnosti webu a mezi testovacími iteracemi ve scénáři zátěžového testu. Použití časů pomýšlení v zátěžovém testu může být užitečné při vytváření přesnějších simulací zatížení. Můžete změnit, zda se v zátěžových testech použijí nebo ignorují časy v promyšlenosti. Můžete změnit, zda jsou časy použití v zátěžových testech použity v **Editor zátěžového testu**.

*Profil přemýšleje* je nastavení, které se vztahuje na scénář v rámci zátěžového testu. Toto nastavení určuje, zda jsou během zátěžového testu použity časy přemýšlení, které jsou uloženy v jednotlivých testech výkonu webu. Pokud chcete v některých testech výkonu webu použít časy promýšlení, ale ne jiné, musíte je umístit do různých scénářů. Další informace o scénářích najdete v tématu [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md).

Zpočátku nastavíte, zda při vytváření zátěžového testu pomocí **nového Průvodce zátěžovým testem** použijete časy pomýšlení v zátěžových testech. Další informace najdete v tématu [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md).

Možnosti **profilu promýšlení** jsou popsány v následujícím seznamu:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Vypnuto**

Časy přemýšlení se ignorují. Toto nastavení použijte, pokud chcete vygenerovat maximální zatížení pro vysoce zatížený webový server. Nepoužívejte ji při pokusu o vytvoření realističtějších uživatelských interakcí s webovým serverem.

**Zapnuto**

Časy přemýšlení se používají přesně tak, jak byly zaznamenány v testu výkonnosti webu. Simuluje více uživatelů, kteří spouštějí testy výkonu webu přesně tak, jak jsou zaznamenané. Vzhledem k tomu, že zátěžový test simuluje více uživatelů, může při použití stejné doby pomýšlení vytvořit nepřirozený vzor zatížení synchronizovaných virtuálních uživatelů.

**Normální distribuce**

Používají se časy přemýšlení, ale jsou rozlišené na normální křivce. Nabízí realističtější simulaci virtuálních uživatelů mírně proměnlivou dobu promýšlení mezi požadavky.

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popis naleznete v tématu [Vlastnosti scénáře zátěžového testu](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Změna profilu přemýšleje

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Změna profilu pomýšlení ve scénáři zátěžového testu

1. Z projektu testování výkonu webu a zátěžového testu otevřete zátěžový test.

2. V **Editor zátěžového testu** vyberte uzel scénář, ve kterém chcete změnit **profil promyšlenosti**. **Profil promýšlení** se zobrazí v okně **vlastnosti** . Stisknutím klávesy **F4** zobrazte okno **vlastnosti** .

3. V okně **vlastnosti** změňte vlastnost **profil přemýšlejí** .

4. Po dokončení změny vlastností vyberte v nabídce **soubor** možnost **Uložit** . Potom můžete spustit zátěžový test s novým profilem přemýšlejí.

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
