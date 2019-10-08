---
title: Přidání parametru do rychlé akce metody
ms.date: 09/28/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4dbed81809cb3b69814fbf10dde7129b45396eaa
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000197"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Přidání parametru do metody pomocí rychlé akce

Tato generace kód platí pro:

- C#

- Visual Basic

**Co:** Umožňuje automaticky přidat parametr do metody na základě využití.

**Kdy:** Je nutné přidat parametr do metody a chcete jej správně deklarovat automaticky.

**Proč:** Před voláním je možné přidat parametr do deklarace metody, ale tato funkce je automaticky přidá na základě volání metody.

## <a name="how-to-use-it"></a>Jak ji použít

1. Přidejte do volání metody další argument.

   Pod názvem metody, kde ji voláte, se zobrazí červená vlnovka.

2. Umístěte ukazatel myši na červenou vlnovku, dokud se nezobrazí nabídka rychlé akce. V nabídce rychlé akce vyberte **šipku dolů** a pak vyberte **Přidat parametr do [metoda]** .

   ![Přidání parametru do rychlé akce metody v aplikaci Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > K nabídce rychlá akce se dostanete také tak, že umístíte kurzor na řádek volání metody a potom stisknete **klávesu Ctrl**+ **.** (tečka) nebo v okraji souboru vyberte ikonu žárovky.

   Visual Studio přidá nový parametr do deklarace metody.

> [!NOTE]
> Pokud máte další volání metody, mohou způsobit chyby po použití této rychlé akce, protože neurčují argument pro nově přidaný parametr.

## <a name="see-also"></a>Viz také:

- [Přidat parametr do konstruktoru](generate-constructor.md#addparameter)