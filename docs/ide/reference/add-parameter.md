---
title: Přidání parametru do metody rychlá akce
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 0337f9869764f544f5248d4da717af849457b8e8
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446773"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Přidání parametru k metodě pomocí rychlé akce

Tato generace kód platí pro:

- C#

- Visual Basic

**Co:** umožňuje automaticky přidat parametr do metody, na základě využití.

**Kdy:** je nutné přidat parametr do metody a chcete správně deklarujte ho automaticky.

**Důvod, proč:** můžete přidat parametr do deklarace metody před voláním, ale tato funkce se přidá automaticky založené na volání metody.

## <a name="how-to-use-it"></a>Jak jej používat

1. Přidejte volání metody nadbytečný argument.

   Červený "podtržení" se zobrazí pod název metody, kde volání.

2. Umístěte ukazatel na červenou "podtržení" se zobrazí nabídky rychlé akce. Vyberte **šipka dolů** na nabídky rychlé akce a potom vyberte **přidání parametru do [metoda]**.

   ![Přidání parametru do metody rychlé akce v sadě Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > Nabídky rychlé akce se můžete dostat taky tím, že umístíte kurzor na řádek volání metody a pak buď stisknutím klávesy **Ctrl**+**.** nebo vyberte ikonu žárovky na okraji souboru.

   Visual Studio přidá nový parametr deklarace metody.

> [!NOTE]
> Pokud máte další volání metody může vytvářejí chyby po použití této rychlé akce, protože, nezadávejte argument pro parametr nově přidané.

## <a name="see-also"></a>Viz také:

- [Přidat parametr do konstruktoru](generate-constructor.md#addparameter)