---
title: Přemýšlejte o časech pro testování zatížení
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 887d2af9e60be914bd74141041ecc375cfea4f00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590030"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Upravit doby přemýšlení pro simulaci zpoždění interakce s lidmi na webu ve scénářích zátěžových testů

Myslíš, že časy se používají k simulaci lidského chování, které způsobuje, že lidé čekají mezi interakcemi s webovými stránkami. Myslíš, že časy dojít mezi požadavky v testu výkonu webu a mezi iterací testu ve scénáři zátěžového testu. Použití doby přemýšlení v zátěžovém testu může být užitečné při vytváření přesnějších simulací zatížení. Můžete změnit, zda se časy přemýšlení používají nebo ignorují v zátěžových testech. Můžete změnit, zda se časy přemýšlení používají v zátěžových testech v **Editoru zátěžového testu**.

*Think profil* je nastavení, které se vztahuje na scénář v zátěžovém testu. Nastavení určuje, zda časy přemýšlení, které jsou uloženy v jednotlivých testech výkonu webu jsou použity během zátěžového testu. Pokud chcete použít doby přemýšlení v některých testech výkonu webu, ale ne v jiných, musíte je umístit v různých scénářích. Další informace o scénářích naleznete v [tématu Úprava scénářů zátěžového testu](../test/edit-load-test-scenarios.md).

Zpočátku nastavíte, zda použijete časy přemýšlení v zátěžových testech při vytváření zátěžového testu pomocí **Průvodce novým zátěžového testu**. Další informace naleznete v [tématu Úprava scénářů zátěžového testu](../test/edit-load-test-scenarios.md).

Možnosti **profilu myšlenky** jsou popsány v následujícím seznamu:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Vypnuto**

Myslím, že časy jsou ignorovány. Toto nastavení použijte, pokud chcete generovat maximální zatížení, abyste silně zdůraznili webový server. Nepoužívejte jej při pokusu o vytvoření realističtějších interakcí uživatelů s webovým serverem.

**Zapnuto**

Myslím, že časy se používají přesně tak, jak byly zaznamenány v testu výkonu webu. Simuluje více uživatelů, kteří spouštějí testy výkonu webu přesně tak, jak bylo zaznamenáno. Vzhledem k tomu, že zátěžový test simuluje více uživatelů, použití stejného času přemýšlení by mohlo vytvořit nepřirozený vzor zatížení synchronizovaných virtuálních uživatelů.

**Normální distribuce**

Myslím, že časy se používají, ale liší se na normální křivky. Poskytuje realističtější simulaci virtuálních uživatelů tím, že mírně mění dobu přemýšlení mezi požadavky.

> [!NOTE]
> Úplný seznam vlastností scénáře zátěžového testu a jejich popisy naleznete v tématu [Load test scenario properties](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Změna think profilu

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Změna think profilu ve scénáři zátěžového testu

1. Z webového výkonu a zatížení testovacího projektu otevřete zátěžový test.

2. V **Editoru zátěžových testů**zvolte uzel scénáře, ve kterém chcete změnit **profil think**. **Profil think** se zobrazí v okně **Vlastnosti.** Stisknutím **klávesy F4** zobrazte okno **Vlastnosti.**

3. Změňte vlastnost **Think Profile** v okně **Vlastnosti.**

4. Po dokončení změny vlastností zvolte **Uložit** v nabídce **Soubor.** Potom můžete spustit zátěžový test s novým profilem think.

## <a name="see-also"></a>Viz také

- [Upravit scénáře zátěžového testu](../test/edit-load-test-scenarios.md)
