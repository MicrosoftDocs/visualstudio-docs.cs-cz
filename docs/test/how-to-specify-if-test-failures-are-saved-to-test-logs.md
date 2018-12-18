---
title: Uložit protokol testu zatížení pro neúspěšné testy
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c583418fa34a44d4bc0bf78996df4cb35908b4f0
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064401"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Postupy: určení, zda jsou ukládána selhání testů pro testování protokolů pomocí editoru zátěžových testů

Po vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**, můžete použít **editoru zátěžového testu** Chcete-li změnit vlastnosti zátěžového testu odpovídá potřebám a cílům testování. Zobrazit [návod: vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md). Můžete zadat, pokud chcete protokol testu uložit Pokud selhání testu v rámci zátěžového testu tak, že změníte **při selhání testu uložit protokol** vlastnost.

> [!NOTE]
> Úplný seznam vlastností parametrů spuštění a jejich popis najdete v části [zátěžového testu spusťte nastavení](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Určení, zda bude protokol testu při selhání testu ve scénáři uložen

1.  Otevřete zátěžový test.

     **Editoru zátěžových testů** se zobrazí. Zobrazí se strom zátěžového testu.

2.  V zátěžového testu stromů **parametrů běhu** složky, vyberte uzel parametrů spuštění, který chcete zadat maximální počet iterací testu.

3.  Na **zobrazení** nabídce vyberte možnost **okno vlastností**.

     Vlastnosti parametrů běhu kategorií a jsou zobrazeny v **vlastnosti** okna.

4.  V **při selhání testu uložit protokol** vlastnosti, vyberte buď **True** nebo **False** k určení, zda chcete uložit protokol testu v případě selhání testu ve scénáři.

     Po dokončení změn vlastnosti, zvolte **Uložit** na **souboru** nabídky.

     Data uložená v protokolu lze zobrazit pomocí tabulkového zobrazení v Analyzéru zátěžového testu. Další informace najdete v tématu [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Viz také:

- [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md)
- [Návod: Vytvoření a spuštění zátěžového testu](../test/walkthrough-create-and-run-a-load-test.md)