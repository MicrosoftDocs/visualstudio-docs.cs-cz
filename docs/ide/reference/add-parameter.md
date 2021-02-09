---
title: Přidání parametru do rychlé akce metody
description: Naučte se používat rychlou akci k automatickému přidání a deklaraci parametru na základě využití metody.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c1e623bea0eab4b45aec3d331864db49a2787f8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846345"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Přidání parametru do metody pomocí rychlé akce

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Umožňuje automaticky přidat parametr do metody na základě využití.

**Když:** Je nutné přidat parametr do metody a chcete jej správně deklarovat automaticky.

**Proč:** Před voláním je možné přidat parametr do deklarace metody, ale tato funkce je automaticky přidá na základě volání metody.

## <a name="how-to-use-it"></a>Jak ji použít

1. Přidejte do volání metody další argument.

   Pod názvem metody, kde ji voláte, se zobrazí červená vlnovka.

2. Umístěte ukazatel myši na červenou vlnovku, dokud se nezobrazí nabídka rychlé akce. V nabídce rychlé akce vyberte **šipku dolů** a pak vyberte **Přidat parametr do [metoda]**.

   ![Přidání parametru do rychlé akce metody v aplikaci Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > K nabídce rychlá akce se dostanete také tak, že umístíte kurzor na řádek volání metody a potom stisknete **klávesu CTRL** + **.** (tečka) nebo v okraji souboru vyberte ikonu žárovky.

   Visual Studio přidá nový parametr do deklarace metody.

> [!NOTE]
> Pokud máte další volání metody, mohou způsobit chyby po použití této rychlé akce, protože neurčují argument pro nově přidaný parametr.

## <a name="see-also"></a>Viz také

- [Přidat parametr do konstruktoru](generate-constructor.md#addparameter)
