---
title: Přidat parametr k rychlé akci metody
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6720421fd5188688214665d85de682542b1c1357
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595862"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Přidání parametru k metodě pomocí rychlé akce

Toto generování kódu se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje automaticky přidat parametr k metodě na základě použití.

**Kdy:** Je třeba přidat parametr k metodě a chcete správně deklarovat automaticky.

**Proč:** Parametr můžete přidat do deklarace metody před jeho voláním, ale tato funkce jej přidá automaticky na základě volání metody.

## <a name="how-to-use-it"></a>Jak ji použít

1. Přidejte další argument do volání metody.

   Pod názvem metody, ve které ji nazýváte, se zobrazí červená vlnovka.

2. Umístěte ukazatel myši na červenou vlnovku, dokud se nezobrazí nabídka Rychlé akce. Vyberte **šipku dolů** v nabídce Rychlé akce a pak vyberte **Přidat parametr do [metody]**.

   ![Přidat parametr pro rychlou akci metody v sadě Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > K nabídce Rychlé akce můžete také získat přístup tak, že umístíte kurzor na řádek volání metody a potom stisknete **klávesu Ctrl**+**.** (tečka) nebo výběrem ikony žárovky na okraji souboru.

   Visual Studio přidá nový parametr do deklarace metody.

> [!NOTE]
> Pokud máte další volání metody, mohou způsobit chyby po použití této rychlé akce, protože neurčují argument pro nově přidaný parametr.

## <a name="see-also"></a>Viz také

- [Přidat parametr do konstruktoru](generate-constructor.md#addparameter)
