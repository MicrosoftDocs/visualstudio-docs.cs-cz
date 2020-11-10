---
title: Synchronizace sad pravidel projektu se zásadou vrácení se změnami
ms.date: 11/04/2016
description: Naučte se, jak synchronizovat sadu pravidel projektu Visual Studio Code se zásadou vrácení se změnami projektu Azure DevOps.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 913860538fe7f9da1514d0e51d23bb3ea48c3b66
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434685"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Postupy: synchronizace sady pravidel projektu kódu se zásadou vrácení se změnami projektu Azure DevOps

Synchronizujete nastavení analýzy kódu pro projekty kódu se zásadou vrácení se změnami pro projekt Azure DevOps zadáním sady pravidel, která obsahuje alespoň pravidla zadaná v sadě pravidel pro zásadu vrácení se změnami. Váš vedoucí vývojář může informovat o názvu a umístění sady pravidel pro zásadu vrácení se změnami. Pomocí jedné z následujících možností lze zajistit, aby analýza kódu pro projekt používala správnou sadu pravidel:

- Pokud zásada vracení se změnami používá jednu z předdefinovaných sad pravidel společnosti Microsoft, otevřete dialogové okno Vlastnosti pro projekt kódu, zobrazte stránku Analýza kódu a vyberte sadu pravidel. Standardní sady pravidel společnosti Microsoft jsou automaticky nainstalovány se sadou Visual Studio, jsou nastaveny jen pro čtení a neměly by být upravovány. Pokud se sady pravidel neupravují, pravidla v zásadách a v místních pravidlech se budou zaručit, aby odpovídala.

- Pokud zásada vracení se změnami používá vlastní sadu pravidel, vytvořte místní kopii provedením operace Get v souboru sady pravidel ve správě verzí. Pak zadejte toto místní umístění v nastavení analýzy kódu pro projekt kódu. Je zaručeno, že pravidla budou shodná s tím, zda je sada pravidel pro zásady vracení se změnami v aktuálním stavu.

     Pokud namapujete umístění správy verzí na místní složku, která se nachází ve stejné relaci jako projekt kódu v kořenovém adresáři projektu Azure DevOps, umístění pravidla se nastaví pomocí relativní cesty. Relativní cesta zajišťuje, že nastavení projektu kódu pro analýzu kódu lze přesunout do jiných počítačů.

- Přizpůsobení kopie sady pravidel pro zásadu vrácení se změnami pro projekt kódu. Ujistěte se, že nová sada pravidel obsahuje všechna pravidla v zásadách vrácení se změnami a všechna další pravidla, která chcete zahrnout. Musíte se ujistit, že sada pravidel obsahuje všechna pravidla v sadě pravidel pro zásadu vrácení se změnami.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Určení standardní sady pravidel společnosti Microsoft

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt kódu a pak klikněte na **vlastnosti**.

2. Klikněte na **Analýza kódu**.

::: moniker range="vs-2017"

3. V seznamu **Spustit tuto sadu pravidel** vyberte sadu pravidel zásad vracení se změnami.

::: moniker-end

::: moniker range=">=vs-2019"

3. V seznamu **aktivní pravidla** vyberte sadu pravidel zásad vracení se změnami.

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Určení sady pravidel zásad pro vlastní vracení se změnami

1. V případě potřeby proveďte operaci získat v souboru sady pravidel, který určuje zásadu vrácení se změnami.

2. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt kódu a pak klikněte na **vlastnosti**.

3. Klikněte na **Analýza kódu**.

::: moniker range="vs-2017"

4. V seznamu **Spustit tuto sadu pravidel** klikněte na **\<Browse>** .

::: moniker-end

::: moniker range=">=vs-2019"

4. V seznamu **aktivní pravidla** klikněte na **\<Browse>** .

::: moniker-end

5. V dialogovém okně **otevřít** zadejte soubor sady pravidel zásad vracení se změnami.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Vytvoření vlastní sady pravidel pro projekt kódu

Informace o vytvoření vlastní sady pravidel najdete v tématu [přizpůsobení sady pravidel](how-to-create-a-custom-rule-set.md).
